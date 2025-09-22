#  Minería de Datos de Lípidos  

Este proyecto tiene como objetivo **unificar, analizar y limpiar bases de datos de lípidos** para obtener un recurso propio, completo y depurado, listo para análisis posteriores.  

La idea principal es construir un **pipeline reproducible** que permita:  
- Recolectar información de múltiples fuentes.  
- Integrar datos en un solo archivo maestro.  
- Analizar su calidad y estructura.  
- Depurar y normalizar los datos para usos en investigación y análisis bioinformático.

## 🧾 Procedimiento Paso a Paso  

### 1️⃣ Búsqueda y Descarga de Bases de Datos  
- Se realizó una búsqueda de información sobre lípidos en bases de datos especializadas.  
- Fuentes utilizadas:  
  - [Glycosmos](https://glycosmos.org/)  
  - [LIPID MAPS® LMSD](https://www.lipidmaps.org/)  
- Se descargaron todas las bases de datos disponibles de las fuentes seleccionadas.

### 2️⃣ Creación de la Base de Datos Unificada  
- Se desarrolló un script en Jupyter Lab llamado **`creation_databank.ipynb`** con la ayuda de DeepSeek.  
- Este script integró todas las bases de datos descargadas y generó una base de datos unificada en formato **CSV**.  

📁 **Archivo resultante:**  
`unified_lipid_database.csv`  

📊 **Reporte de Unificación:**  
- **Total de registros:** `118,462`  
- **Total de columnas:** `37`  
- **Registros por fuente:**  
  - nan → 0 registros  
  - comp_db → 64,891 registros  
  - lipiglu → 3,325 registros  
- **Primeras 10 columnas:**  
  `['lm_id', 'inchi_key_lipidmaps', 'smiles_lipidmaps', 'obsolete_id', 'source_lipidmaps', 'name', 'systematic_name', 'category', 'main_class', 'exact_mass']`
---

### 3️⃣ Análisis Inicial de la Base de Datos  
- Se ejecutó el script **`analysis_databank.ipynb`** para:  
  - Identificar columnas vacías.  
  - Detectar datos incompletos o fuera de lugar.  
  - Generar estadísticas iniciales.  

📁 **Archivo resultante:**  
`enhanced_lipid_database.csv`  

resultados 
Dimensiones finales: (115138, 35)
Columnas finales: ['lm_id', 'inchi_key_lipidmaps', 'smiles_lipidmaps', 'source_lipidmaps', 'name', 'systematic_name', 'category', 'main_class', 'exact_mass', 'formula', 'inchi_key_sdf', 'inchi', 'smiles_sdf', 'abbreviation', 'synonyms', 'pubchem_cid', 'chebi_id', 'molwt', 'hmdb_id', 'swisslipids_id', 'sub_class', 'source_sdf', 'headgroup', 'abbrev', 'mass', 'chain_type', 'source', 'morgan_fp', 'mol_weight', 'logp', 'hbd', 'hba', 'rotatable_bonds', 'tpsa', 'heavy_atoms']

Nuevas columnas añadidas:
  - morgan_fp: 49443 valores no nulos (42.94%)
  - mol_weight: 49443 valores no nulos (42.94%)
  - logp: 49443 valores no nulos (42.94%)
  - hbd: 49443 valores no nulos (42.94%)
  - hba: 49443 valores no nulos (42.94%)
  - rotatable_bonds: 49443 valores no nulos (42.94%)
  - tpsa: 49443 valores no nulos (42.94%)
  - heavy_atoms: 49443 valores no nulos (42.94%)

Proceso completado exitosamente!

### 4️⃣ Limpieza y Depuración de Datos  
- Se utilizó el script **`cleaned_databank.ipynb`** para:  
  - Eliminar registros duplicados, vacíos o inconsistentes.  
  - Corregir formatos y nombres de columnas.  
  - Documentar los datos eliminados.  
  - Generar estadísticas y gráficas sobre valores nulos antes y después de la limpieza.  

📁 **Archivo resultante:**  
`cleaned_lipid_database.csv`  

resultados 
=== RESUMEN EJECUTIVO ===

Base de datos original:
- Registros: 118462
- Columnas: 37

Después de la limpieza:
- Registros: 49466 (41.76% retenidos)
- Columnas: 27 (72.97% retenidas)

Eliminados:
- 10 columnas con >95% de valores nulos
- 68996 registros con >50% de valores nulos

La base de datos limpia se ha guardado en: la ruta impuesta
El reporte detallado se ha guardado en: /home/edwin/proyectos/spent_coffee_grounds/lipids/raw/databases/data_cleaning_report.txt

Gráficas generadas:
## 📊 Distribución de Valores Nulos

<p align="center">
  <img src="./null_values_analysis.png" width="600"><br>
  <em>Análisis general de valores nulos</em>
</p>

<p align="center">
  <img src="./nulls_per_record_distribution.png" width="600"><br>
  <em>Distribución de valores nulos por registro</em>
</p>

<p align="center">
  <img src="./remaining_nulls_analysis.png" width="600"><br>
  <em>Análisis de nulos remanentes después de la limpieza</em>
</p>
---
Proceso completado exitosamente!


