# 🏋️ Gym Tracker

Aplicación web de página única para registrar y visualizar tus entrenamientos. Funciona completamente en el navegador sin necesidad de backend.

---

## 🚀 Cómo usar la aplicación

### Pantalla principal

Al abrir `index.html` verás la pantalla principal con tres pestañas:

| Pestaña | Descripción |
|---------|-------------|
| **Registro** | Añade y edita sesiones de entrenamiento día a día |
| **📈 Progresión** | Gráficas de evolución de peso por ejercicio |
| **📊 Volumen** | Gráficas de volumen total por día |

Desde el menú superior también puedes acceder a:
- 🏆 **Estadísticas** – racha, promedio semanal, 1RM estimado
- ⚙️ **Ajustes** – edita los ejercicios de cada día
- ☀️/🌙 **Tema** – alterna entre modo oscuro y claro
- **⬆️ CSV** – importar datos
- **⬇️ CSV** – exportar registros actuales

---

### Agregar una sesión

1. Ve a la pestaña **Registro**.
2. Selecciona el día deseado en la barra de días.
3. Haz clic en **➕ Agregar Sesión del Día**.  
   Se crea automáticamente una sesión con la fecha de hoy y todos los ejercicios de ese día.
4. Rellena las columnas **S** (series), **R** (reps), **Kg** (peso) y **RIR** para cada ejercicio.
5. Los datos se guardan automáticamente en el almacenamiento local del navegador.

---

## 📥 Importar datos CSV

Al pulsar **⬆️ CSV** se mostrará un diálogo que te preguntará qué tipo de datos quieres importar:

### Opción A — Rutina (plantilla)

Actualiza los días y ejercicios que aparecen como plantilla.  
Soporta cualquier número de días (5, 6, 7…) y cualquier número de ejercicios por día.

**Formato del CSV:**

```
Día,Ejercicio,Series,Reps
Lunes - Push Pecho,Press de Banca Plano (Barra),3,8
Lunes - Push Pecho,Press Militar de Pie (Barra),3,8
Lunes - Push Pecho,Fondos en Paralelas (Lastrados),3,10
Martes - Pull Espalda,Dominadas Pronas (Lastradas),3,8
Martes - Pull Espalda,Remo Pendlay (Barra),3,8
Miércoles - Pierna + Abs,Sentadilla Trasera (Barra),4,6
Jueves - Push Hombro,Press Inclinado (Barra),3,8
Viernes - Pull Bíceps,Chin-ups / Supinas (Lastradas),3,8
Sábado - Full Body,Peso Muerto (Barra),4,5
```

> **Notas:**
> - La primera fila es la cabecera (obligatoria).
> - El nombre del día puede ser cualquier texto; la parte antes del espacio se usa como clave.  
>   Días reconocidos automáticamente: `Lunes`, `Martes`, `Miércoles`, `Jueves`, `Viernes`, `Sábado`, `Domingo`.
> - Las columnas `Series` y `Reps` de la rutina son solo informativas (valores por defecto al crear la sesión).
> - Cada día puede tener un número distinto de ejercicios.
> - Si el CSV incluye 6 días, la aplicación crea el 6.º día automáticamente.

---

### Opción B — Registros de pesos (historial)

Agrega sesiones de entrenamiento pasadas al historial. No sobreescribe registros existentes, los añade.

**Formato del CSV:**

```
Día,Fecha,Ejercicio,Series,Reps,Peso,RIR
Lunes - Push Pecho,2024-03-01,Press de Banca Plano (Barra),3,8,80,2
Lunes - Push Pecho,2024-03-01,Press Militar de Pie (Barra),3,8,60,1
Lunes - Push Pecho,2024-03-01,Fondos en Paralelas (Lastrados),3,10,0,2
Martes - Pull Espalda,2024-03-02,Dominadas Pronas (Lastradas),3,8,10,1
Viernes - Pull Bíceps,2024-03-08,Chin-ups / Supinas (Lastradas),3,8,10,2
```

> **Notas:**
> - La primera fila es la cabecera (obligatoria).
> - `Fecha` debe estar en formato `AAAA-MM-DD`.
> - `Peso` es el peso usado en kg. Usa `0` si es ejercicio con peso corporal.
> - `RIR` (Reps in Reserve) es opcional; déjalo vacío si no lo usas.
> - Todos los registros de la misma fecha y día se agrupan en la misma sesión.
> - Si el CSV contiene días que no existen en la rutina, se crean automáticamente.

---

## 📤 Exportar datos

Haz clic en **⬇️ CSV** para descargar un archivo `registro_entrenamiento.csv` con todos tus registros en el formato de *Registros de pesos* descrito arriba.

---

## 🎨 Paleta de colores

La aplicación usa un tema oscuro con los siguientes colores temáticos por tipo de día:

| Tipo | Color |
|------|-------|
| Push | 🟠 `#e8521a` |
| Pull | 🔵 `#2196f3` |
| Pierna / Legs | 🟢 `#4caf50` |
| Abs | 🟣 `#9c27b0` |
| Otro | 🟡 `#f0a500` |

---

## 💾 Almacenamiento

Todos los datos se guardan en el **localStorage** del navegador. No se envía ningún dato a ningún servidor.

Para hacer una copia de seguridad, usa el botón **⬇️ CSV** periódicamente.
