# 📊 Academic Performance Dashboard & Grade Simulator

> **PWA (Progressive Web App)** interactiva de alto rendimiento construida con **React**, **TypeScript**, **Tailwind CSS** y **Recharts**. Diseñada para el seguimiento en tiempo real de calificaciones ponderadas, análisis visual de rendimiento y simulación predictiva de metas académicas.

---

## 💡 Propósito e Inspiración

El desarrollo de esta plataforma responde a dos objetivos clave:

1. **Gestión Académica Personal:** Proveer una herramienta ágil, precisa y accesible desde cualquier dispositivo para llevar el control diario de asignaturas, calcular promedios ponderados en tiempo real y simular escenarios futuros (*"¿Cuánto necesito obtener en mi examen final para alcanzar una meta X?"*).
2. **Exhibición Técnica y Buenas Prácticas:** Demostrar capacidades de arquitectura *Clean Code*, diseño responsive moderno en modo oscuro, desarrollo *offline-first* (PWA/LocalStorage), y manejo de librerías de visualización interactiva de datos.

---

## 🛠️ Tech Stack & Herramientas

| Capa / Módulo | Tecnología | Justificación |
| :--- | :--- | :--- |
| **Framework UI** | **React 18** | Arquitectura basada en componentes reactivos y manejo eficiente del DOM. |
| **Lenguaje** | **TypeScript** | Tipado estricto para prevenir errores en cálculos numéricos y estructuras de datos. |
| **Estilos** | **Tailwind CSS** | Utilidades CSS de alta velocidad para un diseño *Dark Mode* elegante y responsive. |
| **Visualización** | **Recharts** | Gráficas SVG interactivas, responsivas y declarativas. |
| **Persistencia** | **Web Storage (LocalStorage)** | Mantenimiento de estado en cliente con sincronización síncrona. |
| **Deployment** | **GitHub Pages / Vercel** | Despliegue continuo con cero latencia y alta disponibilidad. |

---

## 📐 Fundamento Matemático & Algoritmos

El motor de cálculo interno implementa dos algoritmos principales:

### 1. Promedio Ponderado Relativo Escalar

El promedio actual $P_A$ de una materia no asume una calificación por defecto en evaluaciones pendientes; en su lugar, calcula el rendimiento basado en la suma ponderada del porcentaje acumulado hasta la fecha:

$$P_A = \left( \frac{\sum_{i \in E} (S_i \cdot W_i)}{\sum_{i \in E} W_i} \right) \cdot M$$

Donde:
* $S_i$: Calificación obtenida en la evaluación $i$.
* $W_i$: Ponderación (%) de la evaluación $i$.
* $E$: Conjunto de evaluaciones con nota registrada.
* $M$: Escala máxima de calificación (ej. 10.0).

---

### 2. Algoritmo de Simulación Inversa de Metas

Para proyectar la nota mínima requerida en las evaluaciones pendientes $R$ para alcanzar una meta $T$, el sistema aplica:

$$S_{\text{requerida}} = \frac{T \cdot 100 - \sum_{i \in E} (S_i \cdot W_i)}{\sum_{j \in R} W_j}$$

* Si $S_{\text{requerida}} \le M$, la meta se identifica como **alcanzable**.
* Si $S_{\text{requerida}} > M$, el dashboard advierte automáticamente que la meta es **matemáticamente inalcanzable** con las ponderaciones pendientes.

---

## 📂 Arquitectura del Proyecto

El proyecto está estructurado bajo la separación estricta de responsabilidades (*Clean Architecture*):

```text
academic-performance-dashboard/
├── index.html                 # Punto de entrada / Single-file standalone app
├── src/
│   ├── components/
│   │   └── Dashboard.tsx      # Componente principal de UI y gráficas
│   ├── context/
│   │   └── AcademicContext.tsx# Estado global React + LocalStorage Provider
│   ├── types/
│   │   └── academic.ts        # Interfaces y contratos de datos TypeScript
│   └── utils/
│       ├── calculations.ts    # Motor matemático puro
│       └── simulator.ts       # Algoritmos de predicción
├── package.json
└── README.md
