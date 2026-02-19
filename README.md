# Potential-Customers-Prediction
Analyze and build an ML model to help identify which leads are more likely to convert to paid customers, find the factors driving the lead conversion process and create a profile of the leads which are likely to convert.

# ExtraaLearn Project

## Contexto
La industria EdTech ha crecido exponencialmente en la última década. Según proyecciones, el mercado de educación online alcanzaría los $286.62bn en 2023 con una tasa de crecimiento anual compuesta (CAGR) de 10.26% entre 2018 y 2023.  
La era moderna de la educación online ha impulsado este crecimiento gracias a características como:
- Facilidad para compartir información
- Experiencia personalizada de aprendizaje
- Transparencia en la evaluación

Durante la pandemia de Covid-19, el sector experimentó un crecimiento acelerado, atrayendo nuevos clientes y generando múltiples startups. Con recursos digitales de marketing, las empresas pueden llegar a audiencias más amplias y captar leads a través de:
- Interacciones en redes sociales y plataformas online
- Navegación en el sitio web/app y descarga de brochures
- Contacto vía email

El reto: identificar qué leads tienen mayor probabilidad de convertirse en clientes pagos.

---

## Objetivo
ExtraaLearn, startup en etapa inicial, ofrece programas en tecnologías de vanguardia para estudiantes y profesionales.  
El objetivo principal es:
1. Analizar y construir un modelo de ML que identifique leads con mayor probabilidad de conversión.
2. Encontrar los factores que impulsan el proceso de conversión.
3. Crear un perfil de leads con alta probabilidad de conversión.

---

## Insights y Recomendaciones

### Modelos
- Algoritmos usados: Decision Tree y Random Forest
- Mejor modelo: Random Forest podado (depth=9)
- Accuracy: ~85.4%
- F1 Score (Clase 1 - Convertido): 0.75

### Principales Predictores
- Tiempo en el sitio web (25.8%)
- Primer interacción vía sitio web (18.2%)
- Nivel de perfil completado (6.3% y 4.4%)
- Vistas por visita (12.1%)
- Edad (11.3%)
- Última actividad (Website > Email > Phone)
- Fuente de referencia (Referral)

### Segmentación de Leads
```python
def segment_lead(row):
    if row['profile_completed'] == 2 and row['website_visits'] >= 3 and row['referral'] == 'Yes':
        return 'Hot'
    elif row['website_visits'] >= 2:
        return 'Warm'
    else:
        return 'Cold'
```

Resumen de segmentos:
- Hot: visitas altas, perfiles completos, referidos → mayor probabilidad de conversión
- Warm: visitas moderadas → probabilidad media
- Cold: baja interacción → baja probabilidad

Factores Clave de Conversión
- Engagement en el sitio web: más tiempo y páginas vistas → mayor conversión.
- Perfil completo: leads con 75–100% de perfil completado convierten más.
- Primer canal de interacción: leads vía sitio web convierten más que vía app.
- Última actividad: email es el canal más efectivo para re-engagement.
- Referidos: aunque pocos, tienen la tasa de conversión más alta (67.7%).

Perfil de Leads con Alta Conversión
- Edad: promedio ~50 años (profesionales y desempleados convierten más).
- Ocupación: profesionales > desempleados > estudiantes.
- Primer interacción: sitio web.
- Perfil completo (75–100%).
- Alta actividad en el sitio (visitas, tiempo, páginas).
- Última actividad: website o teléfono.
- Fuente: referidos.

Implicaciones de Negocio
- Marketing: mejorar experiencia web y fomentar completar perfiles.
- Ventas: priorizar leads con alto engagement web y referidos.
- Producto: añadir funcionalidades que incentiven visitas y exploración.
- Campañas:
- Incentivar referidos
- Promover completitud de perfil
- Mejorar experiencia en la app móvil

Conclusión
El modelo de ML permite a ExtraaLearn:
- Asignar recursos de manera eficiente
- Mejorar tasas de conversión
- Crecer su base de clientes enfocándose en los leads más prometedores
