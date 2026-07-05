# 🛍️ Factores de Comportamiento Asociados al Ingreso Anual en NovaRetail+

## 📌 Descripción
Análisis exploratorio y correlacional sobre 15,000 clientes de una plataforma de e-commerce en Latinoamérica, con el objetivo de identificar qué variables de comportamiento están más fuertemente asociadas al ingreso anual generado por cliente.

## 🎯 Objetivo
NovaRetail+ es una plataforma de comercio electrónico en Latinoamérica con millones de usuarios. Para el cierre de 2024, el equipo de Crecimiento y Retención buscaba responder:

- ¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?

Este es un análisis **correlacional (exploratorio)** — no busca ni permite establecer relaciones de causalidad, solo identificar asociaciones que orienten futuras estrategias e hipótesis de negocio.

---

## 📂 Conjunto de datos
**Archivo:** `novaretail_comportamiento_clientes_2024.csv` — 15,000 registros, 12 columnas, sin valores nulos.

**Columnas:**
- `id_cliente`: Identificador único del cliente  
- `edad`: Edad del cliente  
- `nivel_ingreso`: Ingreso anual estimado (poder adquisitivo)  
- `visitas_mes`: Número de visitas mensuales a la app/sitio web  
- `compras_mes`: Número de compras realizadas en el mes  
- `gasto_publicidad_dirigida`: Gasto en anuncios asignado al usuario  
- `satisfaccion`: Calificación de satisfacción (escala 1-5)  
- `miembro_premium`: Suscripción premium (1 = sí, 0 = no)  
- `abandono`: Abandono de la plataforma (1 = sí, 0 = no)  
- `tipo_dispositivo`: Dispositivo utilizado (móvil, escritorio, tablet)  
- `region`: Región geográfica (norte, sur, este, oeste)  
- `ingreso_anual`: Métrica principal — ingreso anual generado por el cliente  

---

## 🛠️ Herramientas y librerías
- Python (pandas, numpy)  
- `scipy.stats` — Pearson, Spearman, punto-biserial, chi-cuadrado  
- Seaborn / Matplotlib — heatmap de correlación, scatterplots  

---

## 🔬 Metodología
1. Carga y exploración inicial de datos  
2. Preparación y documentación de supuestos  
3. Visualización de relaciones (heatmap y scatterplots)  
4. Cuantificación de correlaciones (Pearson, Spearman, punto-biserial, V de Cramér)  
5. Interpretación de negocio  
6. Limitaciones y próximos pasos  

---

## 📊 Hallazgos principales
**Correlaciones numéricas (mapa de calor):**
- `compras_mes – ingreso_anual`: **0.97 (muy fuerte)**  
- `visitas_mes – gasto_publicidad_dirigida`: 0.58 (moderada-fuerte)  
- `visitas_mes – ingreso_anual`: 0.34 (moderada)  
- `visitas_mes – compras_mes`: 0.35 (moderada)  
- `gasto_publicidad_dirigida – ingreso_anual`: 0.20 (débil)  
- `satisfaccion`, `edad`, `nivel_ingreso` vs. `ingreso_anual`: ≤ 0.06 (prácticamente nulas)  

**Hallazgo destacado:**  
La correlación de **compras_mes vs. ingreso_anual (r=0.97)** es inusualmente fuerte y sugiere posible redundancia de información en el dataset.  

**Binarias (punto-biserial):**
- `miembro_premium vs. ingreso_anual`: relación positiva, baja pero significativa (p<0.05).  
- `abandono vs. ingreso_anual`: relación negativa, muy baja y no significativa (p>0.05).  

**Categóricas (V de Cramér):**
- `region vs. tipo_dispositivo`: asociación muy débil (V=0.0123, p=0.59).  

---

## 💡 Implicaciones de negocio
- Segmentar clientes según **compras_mes** para diseñar incentivos diferenciados.  
- No enfocarse únicamente en aumentar visitas: un cliente con pocas visitas puede ser más rentable si su ticket promedio es alto.  

---

## ⚠️ Limitaciones
- Correlación ≠ causalidad.  
- Las visitas explican solo una parte de la variación del ingreso anual.  
- El análisis es agregado; las relaciones podrían variar por segmento (ej. clientes nuevos vs. recurrentes).  

---

## 🔜 Próximos pasos
- Segmentar clientes por nivel de actividad de compra.  
- Analizar el efecto de `miembro_premium` dentro de cada segmento.  
- Explorar `nivel_ingreso` como variable adicional para explicar `ingreso_anual`.  

---
Este proyecto forma parte de mi portfolio de análisis de datos, con énfasis en el rigor metodológico al distinguir correlación de causalidad y en traducir hallazgos estadísticos en implicaciones de negocio accionables.
