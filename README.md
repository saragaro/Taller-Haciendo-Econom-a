# Taller 7: Consultoría para un Fondo de Inversión — Índices sectoriales de Canadá (2015–2025)

Repositorio del equipo consultor para el encargo de un fondo de inversión que quiere comparar la evolución de tres sectores de la economía global entre 2015 y 2025, con especial atención a las diferencias entre un periodo previo al COVID y uno posterior. Para ello se construyen índices transparentes a partir de datos de mercado de Bloomberg, se evalúa cómo la regla de ponderación cambia la lectura de los resultados, se comparan retornos y volatilidad, y se formula una recomendación de inversión sustentada en la evidencia.

Taller basado en *Doing Economics*: https://books.core-econ.org/doing-economics/book/text/10-02.html

## Equipo consultor

| Integrante | Rol |
|---|---|
| _Juan Esteban Plazas Romero_ | _Líder del proyecto y enlace con el fondo_ |
| _Sara Gabriela Rodríguez Moreno_ | _Especialista en visualización y comunicación_ |
| _Angélica María Díaz Niño_ | _Analista cuantitativo_ |
| _Danna Sofía Romero Ortíz_ | _Especialista en datos y reproducibilidad_ |

## Descripción del encargo

El fondo quiere entender cómo se comportaron tres sectores del mercado canadiense antes y después del COVID. Puntualmente, busca respuesta a cuatro preguntas:

1. ¿Cómo se construyen índices sectoriales transparentes y qué cambia según la regla de ponderación (volumen vs. precio)?
2. ¿Qué muestran los índices sobre desempeño y riesgo entre 2015 y 2025?
3. ¿Qué diferencias hay entre 2015 y 2025, y qué limitaciones tiene esa comparación?
4. ¿Qué sectores priorizar, mantener bajo observación o evitar?

**Universo de análisis.** Tres sectores de la Bolsa de Valores de Toronto (TSX), con 10 acciones por sector (identificador `CN Equity`):

| Sector | Acciones |
|---|---|
| Financiero | RY, TD, BMO, BNS, CM, NA, BN, MFC, SLF, GWO |
| Materiales | ABX, AEM, LUG, WPM, FNV, TECK/B, K, FM, LUN, PAAS |
| Energía | SU, CNQ, ENB, TRP, CVE, IMO, PPL, TOU, WCP, ARX |

**Fuente de los datos.** Terminal Bloomberg: precios de cierre diarios (`PX_LAST`) y volúmenes de transacción diarios (`PX_VOLUME`), del 1 de enero de 2015 al 31 de diciembre de 2025, descargados con el complemento de Bloomberg para Excel (Spreadsheet Builder).

## Estructura del repositorio

```
TALLER_7_FONDO_INVERSION/
├── Analisis/
│   └── Taller_7_Consultoria_Bloomberg.xlsx   # Libro de Excel con todo el análisis
├── Docs/
│   └── Taller_7_Consultoria_Fondo_Inversion.docx   # Enunciado del taller
├── Informe/
│   └── informe_taller7.docx                  # Entrega escrita (respuestas 1.1 a 3.5)
├── Presentacion/
│   └── presentacion.pptx                     # Material para la Sesión 3 (máx. 5 min)
├── .gitignore
└── README.md
```

## Reproducibilidad

- **Todo el análisis vive en un único libro de Excel** (`Analisis/Taller_7_Consultoria_Bloomberg.xlsx`). Las fórmulas están visibles y no hay valores pegados donde el resultado pueda obtenerse con una fórmula o una referencia.
- Las hojas se leen en este orden:

| Hoja | Contenido |
|---|---|
| `Portada y Roles` | Integrantes, roles y aportes concretos con su evidencia |
| `S.FINANCIERO`, `S. MATERIALES`, `S. ENERGÍA` | Precios de cierre y volúmenes diarios de Bloomberg (10 acciones por sector) |
| `Ponderaciones e Índices.` | Pesos por volumen y por precio de enero de 2015, con verificación de que suman 1 |
| `2.2 Retornos` | Retornos aritméticos diarios de cada acción y retornos diarios ponderados de los tres índices |
| `2.3 calculos` | Cuartiles, límites, bigotes y valores atípicos |
| `2.5` | Índices en base 100 (enero de 2015 = 100) |
| `3.1 y 3.2` | Desviación estándar, número de observaciones e intervalos de confianza al 95% (2015 y 2025) con `CONFIDENCE.T` |
| `Riesgo` | Tablas de apoyo al análisis de riesgo: retorno anual por índice, volatilidad móvil de 60 días anualizada, caída desde el máximo (drawdown) y tabla resumen (volatilidad, retorno anualizado, retorno/riesgo, caída máxima y peor día) |
| `Riesgo gráficos` | Gráficos de retorno anual, volatilidad móvil y drawdown, con su lectura y la recomendación de inversión |
| `Gráficas` | Gráficos del taller: pesos, cajas y bigotes, histogramas, índices base 100 y comparación 2015 vs. 2025 con IC |

- Los retornos se calculan como P(t)/P(t−1) − 1 y el retorno de cada índice como la suma ponderada de los retornos de sus 10 acciones, con pesos fijos de enero de 2015.
- **Controles de consistencia** (sirven para verificar el libro): los pesos de cada sector suman 1; cada índice tiene 2.869 retornos diarios; el último valor de los índices base 100 es ≈ 270,4 (Financiero), ≈ 1.009,9 (Materiales) y ≈ 208,0 (Energía).
- Para actualizar el análisis, basta con reemplazar los datos de las hojas `S.*`: el resto de las hojas se recalcula por fórmulas.

## Contenido del análisis

**Parte 1 — Construcción de los índices.** Selección de sectores y acciones (1.1); pesos por volumen de enero de 2015, con verificación de que suman 1 (1.2); pesos por precio inicial y comparación con los de volumen (1.3).

**Parte 2 — Resumen y comportamiento de los datos.** Naturaleza de cada índice y limitaciones de la selección (2.1); retornos diarios de cada activo y del índice ponderado (2.2); gráficos de cajas y bigotes con valores atípicos (2.3); histogramas (2.4); gráfico de líneas en base 100 (2.5).

**Parte 3 — Comparación 2015 vs. 2025.** Desviación estándar y número de observaciones (3.1); intervalos de confianza al 95% con `CONFIDENCE.T` (3.2); gráfico de barras con IC (3.3); interpretación (3.4); recomendación de inversión con al menos una cautela metodológica (3.5). Como apoyo a 3.4 y 3.5, las hojas `Riesgo` y `Riesgo gráficos` reúnen el retorno anual, la volatilidad móvil, el drawdown y una tabla resumen de riesgo por índice.
## Resultados principales

| Medida | Financiero | Materiales | Energía |
|---|---|---|---|
| Índice final (base 100) | 270,4 | 1.009,9 | 208,0 |
| Retorno anualizado (CAGR) | 9,5% | 23,4% | 6,9% |
| Volatilidad anualizada | 17,6% | 33,8% | 31,5% |
| Caída máxima (drawdown) | −41,4% | −50,2% | −75,6% |
| Peor retorno diario | −13,7% | −13,3% | −27,5% |
| Días atípicos (de 2.869) | 202 | 112 | 125 |
| Retorno diario promedio 2015 → 2025 | −0,016% → 0,114% | −0,112% → 0,333% | −0,056% → 0,048% |

La recomendación de inversión y su sustentación están en `Informe/informe_taller7.docx` (sección 3.5) y en el excel en el la hoja de riesgo gráficas.

### Notas metodológicas
- Los precios son de cierre y no incluyen dividendos.
- Los pesos son fijos (enero de 2015) y no se rebalancean.
- Cada índice usa solo 10 acciones, de empresas grandes.
- Bloomberg repite el último precio en días festivos, por lo que hay cerca de 109 días con retorno cero.
- Los datos muestran coincidencias temporales con el COVID, pero no prueban que sea la causa de los cambios.

## Contribuciones individuales

**Juan Esteban Plazas Romero — Líder del proyecto y enlace con el fondo**

Coordinó el trabajo del equipo y verificó que el análisis respondiera a las preguntas del fondo. Lideró la integración de la evidencia en la recomendación de inversión (3.5) y la preparación de la presentación al cliente. Puede verificarse en `Informe/informe_taller7.docx`, secciones 3.4 y 3.5, y en `Presentacion/presentacion.pptx`.

**Sara Gabriela Rodríguez Moreno — Especialista en visualización y comunicación**

_(Verificar y ajustar)_ Construyó los gráficos del taller en la hoja `Gráficas`: pesos por volumen y por precio (1.3), cajas y bigotes (2.3), histogramas (2.4), índices en base 100 en escala lineal y logarítmica (2.5) y barras de 2015 vs. 2025 con intervalos de confianza (3.3). Armó además las hojas `Riesgo` y `Riesgo gráficos`, con los gráficos de retorno anual, volatilidad móvil y drawdown, y la lectura que sustenta la recomendación. Dio coherencia visual y narrativa a la presentación. Puede verificarse en las hojas `Gráficas`, `Riesgo` y `Riesgo gráficos` delExcel y en `Presentacion/presentacion.pptx`.

**Angélica María Díaz Niño — Analista cuantitativo**

 Construyó los pesos por volumen y por precio de enero de 2015 y verificó que suman 1 (hoja `Ponderaciones e Índices.`). Calculó los retornos aritméticos diarios y los retornos ponderados de los tres índices (hoja `2.2 Retornos`, columnas L, W y AH) y los índices en base 100 (hoja `2.5`). Calculó los estadísticos de cajas y bigotes (hoja `2.3 calculos`) y la desviación estándar, el número de observaciones y los intervalos de confianza al 95% con `CONFIDENCE.T` (hoja `3.1 y 3.2`).

**Danna Sofía Romero Ortíz — Especialista en datos y reproducibilidad**

Descargó y organizó los precios y volúmenes de Bloomberg y documentó las acciones, los sectores y la fuente de los datos. Estructuró las hojas del libro para que los cálculos puedan seguirse y actualizarse sin rehacer el análisis, y organizó la estructura de este repositorio. Puede verificarse en las hojas `S.FINANCIERO`, `S. MATERIALES` y `S. ENERGÍA`, y en la organización general del libro.


- Doing Economics, Capítulo 10, Proyecto 2: https://books.core-econ.org/doing-economics/book/text/10-02.html
- Bloomberg LP. Precios de cierre (`PX_LAST`) y volúmenes (`PX_VOLUME`) de emisores listados en la TSX, 2015–2025.
