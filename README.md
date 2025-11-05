# Pipelines-de-Preprocesamiento 
Trabajo N°1 
#**Autora: Maria Paula Sánchez Parra**

Este proyecto tiene como propósito aplicar técnicas de limpieza y transformación de datos utilizando el módulo sklearn.pipeline.
Se trabaja con el conjunto de datos dirty_cafe_sales.csv, el cual contiene información de ventas en una cafetería, pero presenta problemas de calidad como valores faltantes, errores tipográficos y datos inconsistentes.

A través de un análisis exploratorio de datos (EDA), se identifican estos problemas y posteriormente se construye un pipeline de preprocesamiento que automatiza su corrección y estandarización, haciendo el flujo de trabajo más eficiente y reproducible.

#**Datos**

El dataset dirty_cafe_sales.csv contiene 10.000 registros sobre ventas realizadas en una cafetería.
Las variables incluidas son:

| Variable               | Descripción                                                           |
| ---------------------- | --------------------------------------------------------------------- |
| `ID de transacción`    | Identificador único de cada compra.                                   |
| `Artículo`             | Producto adquirido (ej. café, pastel, galleta).                       |
| `Cantidad`             | Número de unidades compradas por transacción.                         |
| `Precio por unidad`    | Valor unitario del producto.                                          |
| `Total gastado`        | Precio total de la transacción.                                       |
| `Método de pago`       | Medio de pago utilizado (efectivo, tarjeta, billetera digital, etc.). |
| `Ubicación`            | Tipo de compra (por ejemplo: “In-store” o “Takeaway”).                |
| `Fecha de transacción` | Fecha exacta en la que se realizó la venta.                           |


El dataset presenta inconsistencias como:

-Datos faltantes en columnas numéricas y categóricas.

-Tipos de datos incorrectos (todas las columnas cargadas inicialmente como object).

-Errores tipográficos en variables categóricas.


##**Proceso realizado**

**1.Análisis exploratorio de datos (EDA)**:
-Se revisaron los tipos de variables, se identificaron los valores nulos y se detectaron errores de lectura.
-Todas las columnas fueron inicialmente leídas como object, por lo que se transformaron a category y float según correspondiera.

**2.Construcción del pipeline:** Se diseñó un flujo de preprocesamiento con scikit-learn que incluye:

-**Imputación de datos numéricos**: mediante el promedio de los valores existentes.

-**Imputación de datos categóricos**: usando la moda (categoría más frecuente).

-**Codificación de variables categóricas:** Se aplicó One Hot Encoding únicamente a las variables Método de pago y Ubicación para evitar una explosión de columnas y mantener la interpretabilidad.
Además, se eliminó la primera columna generada para prevenir la trampa de las variables ficticias, asumiendo una categoría base (por ejemplo: “In-store” para ubicación y “Cash” para método de pago).

-**Transformación de fechas:** La variable Fecha de transacción se descompuso en día, mes y año, lo que facilita análisis temporales y patrones de estacionalidad.

-**Escalamiento:** No se aplicó escalamiento a las variables numéricas, ya que representan precios y cantidades, y conservar su magnitud original permite una interpretación más precisa de los resultados.

**Implementación de transformadores personalizados:** Se incluyeron transformadores construidos con FunctionTransformer, para automatizar procesos específicos y garantizar flexibilidad en futuras adaptaciones del pipeline.

**Conclusiones**

-La transformación de variables categóricas permitió estandarizar los datos sin generar un exceso de columnas innecesarias.

-La imputación por moda y promedio aseguró la conservación de información relevante sin sesgar los resultados.

-Mantener las escalas originales de precios y cantidades fue adecuado para mantener la interpretación económica del dataset.

-La división de fechas en componentes temporales facilita futuros análisis de tendencia y estacionalidad.

-El uso de pipelines y transformadores personalizados hizo el proceso de preprocesamiento más eficiente, estructurado y replicable, aplicable a otros conjuntos de datos en el contexto de análisis económico o empresarial.

**Aplicación práctica**

Este pipeline puede adaptarse fácilmente a conjuntos de datos de naturaleza económica, comercial o social, permitiendo procesar información sobre precios, transacciones, consumo o indicadores regionales antes de un análisis econométrico o de aprendizaje automático.
