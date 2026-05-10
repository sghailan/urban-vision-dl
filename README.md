# Urban Vision DL

Detección de objetos en entornos urbanos con YOLOv8 sobre el dataset VisDrone2019. Sistema de vigilancia urbana inteligente capaz de detectar coches, peatones, motos y autobuses desde perspectiva aérea y a nivel de calle en tiempo real.

## Estructura del proyecto

```bash
urban-vision-dl/
├── data/                    → datasets (no incluidos, ver instrucciones)
├── notebooks/
│   └── urban_vision_dl.ipynb   → notebook principal/incluye reflexión
├── figures/
│   ├── v1_yolov8n/          → curvas y métricas modelo baseline
│   ├── v2_yolov8s/          → curvas y métricas mejor modelo
│   ├── v3_yolov8n_tuned/    → curvas y métricas modelo con lr ajustado
│   └── v4_yolov8s_combined/ → curvas y métricas modelo dataset ampliado
├── demo_videos/ → ejemplos aplicando el mejor modelo
│   ├── video1_highway_output.mp4      → inferencia en carretera de alta velocidad
│   ├── video2_intersection_output.mp4 → inferencia en intersección con múltiples vehículos
│   └── video3_urban_dense_output.mp4  → inferencia en cruce urbano denso con peatones
├── informe.pdf              → memoria técnica Parte 1
├── requirements.txt
└── README.md
```

## Instalación

```bash
python3 -m venv venv_urban_dl
source venv_urban_dl/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name venv_urban_dl --display-name "Urban Vision DL"
```
## Datos

Los datos NO están incluidos por su tamaño. Son necesarios para ejecutar el notebook desde el principio.

### VisDrone2019-DET
Descarga desde: https://github.com/VisDrone/VisDrone-Dataset — Task 1: Object Detection in Images

- data/VisDrone2019-DET-train/ → trainset (1.44 GB)
- data/VisDrone2019-DET-val/ → valset (0.07 GB)
- data/VisDrone2019-DET-test/ → testset-dev (0.28 GB)

Cada carpeta debe contener dos subcarpetas: images/ y annotations/

### car+person
Descarga desde Roboflow: https://universe.roboflow.com/salma-ghailan/car-person-m16gb-7pqjm

1. Entra en el dataset y haz Fork
2. Ve a Dataset → Generate New Version
3. Exporta en formato YOLOv8
4. Descarga el zip y descomprímelo en data/car-person.yolov8/

## Vídeos de demo

No necesitas descargar nada. Al ejecutar la sección de demo del notebook, yt-dlp descarga automáticamente los tres vídeos de YouTube directamente en la carpeta `data/`. Solo asegúrate de tener conexión a internet al ejecutar esas celdas.

## Ejecución

Con los datos en `data/` y el entorno activado con las dependencias de `requirements.txt`, el notebook es ejecutable en su totalidad. No obstante, el tiempo de cómputo del entrenamiento es elevado (varias horas por modelo). Por ello se incluye la carpeta `figures/` con las gráficas y tablas de resultados más importantes de cada modelo organizadas por carpetas, permitiendo revisar los resultados sin necesidad de reentrenar. La carpeta `demo_videos/` incluye tres vídeos de inferencia real con el modelo v2 sobre escenas urbanas distintas.