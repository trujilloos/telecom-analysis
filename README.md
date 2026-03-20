# telecom-analysis
Este proyecto tiene como objetivo analizar el comportamiento de uso de los clientes de ConnectaTel (empresa de telecomunicaciones en México y Colombia), a partir de datos de:  📦 Planes contratados  👤 Información de usuarios  📞 Uso real de servicios (llamadas y mensajes)  para generar insights accionables de negocio
🎯 Objetivos

Explorar y limpiar los datasets
Detectar problemas de calidad de datos (nulos, sentinels, formatos)
Analizar el comportamiento de uso (llamadas y mensajes)
Identificar outliers y evaluar su impacto

Crear segmentaciones por:
Nivel de uso
Edad
Generar recomendaciones estratégicas

🗂️ Estructura de Datos

Se utilizaron tres fuentes principales:

plans.csv → Información de planes (precio, beneficios)
users_latam.csv → Datos de clientes (edad, ciudad, plan)
usage.csv → Registro de uso (llamadas y mensajes)

🧹 Limpieza de Datos

Se aplicaron las siguientes transformaciones:
Conversión de tipos de datos (fechas y numéricos)

Reemplazo de valores centinela:
-999 en edad → reemplazado por la mediana
"?" en ciudad → reemplazado por NaN
Manejo de valores nulos:
Identificación de patrones MAR (Missing At Random)
Conservación de nulos cuando representan ausencia lógica (ej. duración en mensajes)

Validación de fechas:

Conversión a formato datetime
Eliminación de fechas fuera de rango (>2024)

📊 Ingeniería de Variables

Se construyeron métricas clave por usuario:
cant_mensajes → total de mensajes
cant_llamadas → total de llamadas
cant_minutos_llamada → minutos totales de llamadas

Se creó un dataset consolidado (user_profile) combinando uso + usuarios.

🔍 Análisis Exploratorio (EDA)

Se realizaron:

Histogramas para analizar distribuciones:
Edad
Mensajes
Llamadas
Minutos
Boxplots para detectar outliers

Análisis de:

Media vs mediana
Distribución por plan
⚠️ Outliers

Detectados principalmente en minutos de llamada

Representan usuarios intensivos ("heavy users")

No se eliminaron, ya que:
Son comportamientos reales
Tienen alto valor de negocio

🧩 Segmentación
📊 Por nivel de uso

Se creó la variable grupo_uso:
Bajo uso → llamadas < 5 y mensajes < 5
Uso medio → llamadas < 10 y mensajes < 10
Alto uso → resto de casos

👤 Por edad

Se creó la variable grupo_edad:
Joven → edad < 30
Adulto → edad < 60
Adulto Mayor → resto

📈 Principales Hallazgos

La mayoría de los usuarios se concentran en Uso Medio
Existe una “larga cola” de usuarios con consumo alto (especialmente en minutos)
La edad no influye significativamente en el tipo de plan contratado
Algunos usuarios presentan consumo intensivo que podría afectar costos operativos

💡 Recomendaciones de Negocio

Crear planes específicos para heavy users
Rediseñar el plan Premium con beneficios diferenciados
Implementar estrategias de retención para usuarios de bajo uso
Aprovechar segmentos de alto consumo para estrategias de monetización

🛠️ Tecnologías Utilizadas

Python 🐍
Pandas
NumPy
Matplotlib

Seaborn
