Está Coverflow - Fé de erratas
==============================

* En el archivo de configuración de la UMV falta el tamaño del bloque de memoria que funcionará como memoria principal.
* En el archivo de configuración del Kernel falta la IP/Puerto de la UMV.
* El enunciado del TP dice que el Stack tiene un tamaño fijo de 100 bytes. Lo correcto es que el tamaño del Stack sea configurable por archivo de configuración.
* En el archivo de configuración del Kernel faltan las variables globales.
* El “Diagrama de Estados de un proceso en el sistema” tiene una transición de más desde Ready hacia el PLP. El Diagrama corregido es el siguiente:

![Diagrama de Estados corregido](diagrama_estados.png)

* El PLP pondrá a todos los Programas recién creados en la cola de New y, en la medida en que el Grado de Multiprogramación lo permita, moverá los Programas de New a Ready, seleccionando según el algoritmo SJN.

* En el enunciado lo nombra poco, así que lo reafirmamos: efectivamente, el PCP planifica según el algoritmo Round Robin.

* En la lista de tareas a realizar del PCP dice:
> Recibirá los PCB del PLP y los encolará en la cola de READY, según el algoritmo de planificación de corto plazo Round Robin.

 Dado que es el PLP el encargado de transicionar Programas de New a Ready, esta tarea debería decir:
 > Planificará según el algoritmo Round Robin a los procesos encolados en la cola de READY.

* Página 7, `System Calls`:
 >En el código Ansisop el identificador de la variable compartida, para diferenciarlo de las variables normales, comenzará con el caracter signo de admiración (!), seguido del identificador de un caracter alfabético, por ejemplo: !a, !g, !q

 La restricción de un único caracter alfabético es incorrecta. Las variables globales se identifican con un `!` y luego una cadena alfanumérica, como correctamente dice la página 18. Por ejemplo, `!a`, `!A`, `!compartida`, `!ParaTodos`, `!Compartidas10`.

* Estructura del PCB: aclaramos el tipo de cada dato.

| Estructura                 | Tipo      |
|----------------------------|-----------|
| Identificador único        | Numérico  |
| Segmento de código         | Dirección |
| Segmento de stack          | Dirección |
| Cursor del stack           | Dirección |
| Índice de código           | Dirección |
| Índice de etiquetas        | Dirección |
| Program counter            | Numérico  |
| Tamaño del Contexto Actual | Numérico  |

* Las primitivas `llamarSinRetorno` y `llamarConRetorno` figuran en el enunciado con un parámetro `t_puntero_instruccion linea_en_ejecuccion` que no aparece en la documentación del Parser. Efectivamente ese parámetro se eliminó de la interfaz, y **no deberá usarse**. Como nota general, ante una incongruencia entre la documentación del Parser y la especificación de AnSISOP que figura como Anexo del TP, la documentación del Parser prevalecerá.

* El PCB debe incluir un campo numérico con el tamaño del segmento Índice de Etiquetas, a fin de que la CPU pueda obtenerlo de la UMV para la búsqueda de etiquetas.
