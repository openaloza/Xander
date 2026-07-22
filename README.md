[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21443498.svg)](https://doi.org/10.5281/zenodo.21443498)


# 🌀 Hybrid Quantum-Classical Ensemble Pipeline

Este proyecto implementa un **pipeline híbrido cuántico-clásico** optimizado que combina modelos cuánticos y clásicos en un esquema de ensamble para tareas de clasificación y análisis de robustez.

## 🚀 Características principales
- **Modelos cuánticos**: QSVM, VQC y QCNN-like (con fallback clásico cuando el backend cuántico no está disponible).
- **Modelos clásicos**: RandomForest, XGBoost, MLP y SVC.
- **Estrategias de ensamble**: soft, hard y functional voting, con búsqueda de pesos mediante grid search.
- **Extras incluidos**:
  - Calibración de clasificadores (`CalibratedClassifierCV`).
  - Ajuste de umbral (threshold tuning).
  - Validación cruzada estratificada (StratifiedKFold).
  - Exportación de métricas por fold (`resumen_estadistico.csv`).
  - Resumen global con medias y desviaciones estándar (`metrics_summary.csv`).
  - Pruebas estadísticas inferenciales (Shapiro-Wilk, Levene, t-test pareado, ANOVA, Cohen’s d).
  - Gráficas automáticas: matrices de confusión y curvas ROC.
  - Simulación de robustez frente a ruido.
  - Logs detallados de entrenamiento y consumo de recursos (CPU/memoria).

## 📂 Estructura de archivos
- `pipeline_gpu.py` → Pipeline híbrido completo (entrenamiento, validación, ensamble).
- `lanzamiento_ibm_kingston.py` → Ejecución en backend real IBM Quantum (`ibm_kingston`) o simulador local.
- `lanzamiento_ibm_simulador.py` → Wrapper para ejecutar el pipeline en modo simulador Aer o QPU real, con integración IBM Runtime.
- `outputs/` → Carpeta donde se guardan métricas, gráficas y logs.

## ⚙️ Requisitos
- Python >= 3.9
- Librerías principales:
  - `numpy`, `pandas`, `scikit-learn`, `matplotlib`, `seaborn`
  - `xgboost`
  - `qiskit`, `qiskit-ibm-runtime` (para ejecución cuántica)
  - `torch` (para modelos híbridos VQC/QCNN)
- Archivo `variables.env` con credenciales de IBM Quantum:
  ```env
  IBM_API_TOKEN=tu_token
  IBM_INSTANCE=tu_instancia
  USE_REAL_QPU=0  # 1 para QPU real, 0 para simulador
  IBM_BACKEND=ibm_kingston


## ▶️ Uso
- Clona el repositorio:

1. git clone https://github.com/tuusuario/hybrid-quantum-classical-pipeline.git  ---  cd hybrid-quantum-classical-pipeline
2. Instala dependencias: pip install -r requirements.txt
3. Ejecuta el pipeline en modo GPU/simulador: python pipeline_gpu.py
4. Ejecuta en backend IBM Quantum: python lanzamiento_ibm_kingston.py
5. Ejecuta en modo simulador Aer con wrapper: python lanzamiento_ibm_simulador.py

## 📊 Resultados

- Métricas por fold → outputs/resumen_estadistico.csv
- Resumen global → outputs/metrics_summary.csv
- Gráficas → outputs/*.png
- Logs → outputs/runtime_log.txt

## 🧪 Pruebas estadísticas
El pipeline genera automáticamente datos para:

- Normalidad (Shapiro-Wilk)
- Homogeneidad de varianzas (Levene)
- Comparaciones pareadas (t-test)
- ANOVA global
- Tamaños de efecto (Cohen’s d)

## 📌 Notas
El pipeline está diseñado para ser reproducible (GLOBAL_SEED).

- Los modelos cuánticos pueden ejecutarse en hardware real (ibm_kingston) o en simulador local.
- Los resultados se exportan automáticamente para facilitar análisis y publicación en artículos científicos.

## 📜 Licencia

Este proyecto está bajo la **Licencia Pública General de GNU, versión 3 (GPLv3)**.  
Consulta el archivo [LICENSE](./LICENSE) para más detalles o visita la página oficial:  
[https://www.gnu.org/licenses/gpl-3.0.html](https://www.gnu.org/licenses/gpl-3.0.html)

---

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**.  
See the [LICENSE](./LICENSE) file for details or visit the official page:  
[https://www.gnu.org/licenses/gpl-3.0.html](https://www.gnu.org/licenses/gpl-3.0.html)




[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21443498.svg)](https://doi.org/10.5281/zenodo.21443498)
https://zenodo.org/badge/DOI/10.5281/zenodo.21443498.svg

