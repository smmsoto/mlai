# Proyecto de Clasificación de Residuos Reciclables

## **Recycle Project**

#### **Resumen Ejecutivo**
Este proyecto explora la aplicación de redes neuronales y aprendizaje supervisado para clasificar y ordenar diferentes tipos de basura en una línea de reciclaje. Aprovechando datos de conjuntos públicos como TrashNet y empleando Redes Neuronales Convolucionales (CNN), el proyecto busca mejorar la eficiencia y precisión de los sistemas de clasificación de residuos, contribuyendo a prácticas de gestión de residuos más sostenibles.

#### **Justificación**
El reciclaje efectivo es un pilar fundamental de la gestión sostenible de residuos. Sin embargo, los métodos actuales de clasificación—ya sea mediante separación manual o sistemas automatizados rudimentarios—suelen ser lentos, costosos y propensos a errores. Esta ineficiencia conduce a altas tasas de contaminación, reduciendo la efectividad general de las iniciativas de reciclaje. Al automatizar el proceso de clasificación con IA, podemos abordar estas ineficiencias, minimizar la contaminación y promover mejores prácticas de reciclaje.

#### **Pregunta de Investigación**
¿Cómo se pueden aplicar las redes neuronales y las técnicas de aprendizaje supervisado para clasificar diferentes tipos de residuos (por ejemplo, plástico, papel, metal) en una línea de reciclaje para optimizar el proceso de clasificación?

#### **Fuentes de Datos**
- Fuente principal de datos: Conjunto de datos TrashNet, que contiene imágenes etiquetadas de varios tipos de residuos.
- Fuentes complementarias: Conjuntos de datos adicionales disponibles públicamente relacionados con la clasificación de residuos o conjuntos personalizados obtenidos a través de asociaciones con instalaciones de reciclaje.
- Datos simulados: Conjuntos de datos sintéticos basados en propiedades conocidas (físicas y visuales) de diferentes tipos de residuos, en caso de que otras fuentes no estén disponibles.

#### **Metodología**
- **Modelado**: Se utilizarán Redes Neuronales Convolucionales (CNN) para clasificar imágenes de residuos. Se empleará aprendizaje por transferencia con modelos preentrenados como ResNet o VGG para mejorar el rendimiento y reducir el tiempo de entrenamiento.
- **Preparación de datos**: Las imágenes serán preprocesadas mediante redimensionamiento, normalización y aumento de datos para mejorar la generalización del modelo.
- **Entrenamiento**: El modelo CNN se entrenará con un conjunto de datos etiquetados, evaluando métricas de rendimiento como precisión, precisión positiva y recuperación en un conjunto de validación.
- **Optimización**: Se aplicarán técnicas como balanceo de clases, ajuste de hiperparámetros y dropout para optimizar el rendimiento del modelo.

#### **Resultados**
Se anticipa que el modelo de red neuronal pueda clasificar los tipos de residuos con alta precisión, especialmente después de abordar problemas relacionados con clases subrepresentadas. Este modelo tiene el potencial de mejorar la velocidad y precisión de los sistemas automatizados de clasificación en instalaciones de reciclaje.


#### **Próximos Pasos**
- Integrar el modelo en un sistema de clasificación en tiempo real y evaluar su rendimiento en un entorno práctico.
- Explorar fuentes de datos adicionales y refinar el modelo para manejar nuevas categorías de residuos.
- Investigar la escalabilidad de la solución para su implementación en diversas instalaciones de reciclaje.

#### **Estructura del Proyecto**

1. **Recolección y Preparación de Datos**

2. **Desarrollo y Entrenamiento del Modelo**

3. **Evaluación y Optimización**

   - [Enlace al notebook del Recycle Project ](https://github.com/smmsoto/mlai/blob/main/RecycleFinalProject/RecycleFinalProject/recyclemodel-FinalProject.ipynb)

##### Contacto e Información Adicional
Para consultas adicionales, por favor contacta a [stephaniemora1789@gmail.com].

## **Reporte Final del captone Project**


## **1. Objetivo del Proyecto**
El objetivo principal del proyecto es **clasificar residuos reciclables** mediante el uso de **aprendizaje profundo**. Se implementó un enfoque de **Transfer Learning**, aprovechando modelos preentrenados para mejorar la precisión en la tarea de clasificación de imágenes.

---



## **2. Carga y Preprocesamiento de Datos**
- **Organización del Dataset**:  
  Las imágenes están organizadas en carpetas, cada una representando una clase específica. El problema se define como una **clasificación multiclase** con **6 categorías**.

- **Librerías Utilizadas**:  
  - **TensorFlow**, **Keras**: Para la creación y entrenamiento del modelo.  
  - **NumPy**, **Pandas**: Para el procesamiento de datos.  
  - **Matplotlib**, **Seaborn**: Para la visualización de resultados.

- **División del Dataset**:  
  Se realizó una división **estratificada** en entrenamiento y validación:  
  - **Número de muestras**:
    - **Entrenamiento**: 1110 imágenes  
    - **Validación**: 277 imágenes  

---



## **3. Aumentación de Datos**
Para mejorar la capacidad del modelo y evitar **overfitting**, se implementó **aumentación de datos** utilizando `ImageDataGenerator`. Se aplicaron las siguientes transformaciones:  
- **Rotación de imágenes**  
- **Normalización de píxeles** en el rango [0,1]

Estas técnicas ayudan a entrenar un modelo más robusto al generar variaciones de las imágenes originales.

---



## **4. Creación del Modelo**
Se utilizó **Transfer Learning** con las siguientes arquitecturas preentrenadas:  
- **VGG16**  
- **ResNet152V2**  

A las redes preentrenadas se les añadieron capas personalizadas para ajustar el modelo a nuestro problema:  
- **GlobalAveragePooling2D**  
- **Capas Dense y Dropout**  
- **Capa de salida** con activación **softmax** para 6 clases.

---



## **5. Entrenamiento del Modelo**
- **Optimizador**: Se utilizó **Adam**, un optimizador eficiente y adaptativo.  
- **Callbacks Implementados**:
  - **ModelCheckpoint**: Guarda el mejor modelo durante el entrenamiento.
  - **ReduceLROnPlateau**: Reduce la tasa de aprendizaje si no hay mejora.  
  - **EarlyStopping**: Detiene el entrenamiento si el rendimiento se estanca.

- **Resultados del Entrenamiento**:  
  - **Precisión en entrenamiento**: **84.67%**  
  - **Pérdida en entrenamiento**: **0.4946**  
  - **Precisión en validación**: **80.50%**  
  - **Pérdida en validación**: **0.6549**  

---



## **6. Evaluación del Modelo**
Se evaluó el modelo utilizando:  
- **Precisión global en validación**: **80.50%**  
- **Confusion Matrix**: Permite identificar las clases con menor rendimiento.  
- **Classification Report**: Incluye métricas como **precision**, **recall** y **F1-score**.

---



## **7. Resultados Finales**
| Métrica               | Entrenamiento | Validación |
|-----------------------|---------------|------------|
| **Precisión**         | 84.67%        | 80.50%     |
| **Pérdida (Loss)**    | 0.4946        | 0.6549     |

- **Número de muestras**:
   - Entrenamiento: **1110 imágenes**
   - Validación: **277 imágenes**

---



## **8. Conclusiones**
1. Se implementó con éxito un modelo de **Transfer Learning** utilizando **VGG16** y **ResNet152V2**, logrando una precisión del **80.50%** en validación.  
2. La **aumentación de datos** mejoró la capacidad de generalización del modelo.  
3. El uso de **callbacks** optimizó el proceso de entrenamiento, evitando el **overfitting**.

### **Recomendaciones**
- Analizar las imágenes mal clasificadas para identificar patrones o problemas.  
- Explorar el ajuste fino (**fine-tuning**) de las capas superiores de los modelos preentrenados.  
- Implementar **validación cruzada** para asegurar un rendimiento más robusto.

---


