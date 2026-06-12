---
title: "Consulta comando TAR con Unidad de cinta LTO2"
date: 2011-07-29
forum: Hardware
---

### Post by pabletesss on 2011-07-29
[FONT=Arial]Buenos días, estoy teniendo una duda con el comando TAR. Les comento mi situación:
Tengo un equipo con Ubuntu 11.04 que utilizo como servidor de archivos. A  este equipo le puse una placa SCSI y una unidad de cinta LTO2 modelo  IBM ULT3580-TD2. Como verán si ejecuto el comando[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]cat /proc/scsi/scsi[/FONT]



me figuran tanto la grabadora de DVD, el disco rigido, la placa SCSI y la unidad de cinta:

[FONT=Arial]Attached devices:
Host: scsi0 Channel: 00 Id: 01 Lun: 00
 Vendor: Optiarc  Model: DVD+-RW ND-3570A Rev: 104B
 Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
 Vendor: ATA      Model: SAMSUNG HD753LJ  Rev: 1AA0
 Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 15 Lun: 00
 Vendor: IBM      Model: SERVERAID        Rev: 1.00
 Type:   Processor                        ANSI  SCSI revision: 02
Host: scsi4 Channel: 01 Id: 04 Lun: 00
 Vendor: IBM      Model: ULT3580-TD2      Rev: 4772
 Type:   Sequential-Access                ANSI  SCSI revision: 03

Hasta ahí todo bien. Cuando verifico la configuración de la unidad con el comando:[FONT=Verdana]

[/FONT]mt -f /dev/nst0 status

Creería que los datos están de manera correcta:[FONT=Verdana]

[/FONT]SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 0 bytes. Density code 0x42 (LTO-2).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN

Mi duda se debe al que al guardar algún dato en una cinta con  el comando TAR se demora demasiado. Y no hace una grabación continua,  sino que es como que primero pusiera en buffer cierta cantidad de  información y luego guarda esa porción en la cinta y así sucesivamente.  Estoy queriendo hacer backup de un archivo que pesa 114GB y tarda  muchísimo (Cachea una pequeña porción del archivo y luego la copia a la  cinta, termina de escribir esa pequeña porción en cinta y vuelve a  cachear y después recién copia esa otra pequeña porción. Y así  sucesivamente. En el display de la unidad se que escribe y para, a los  cinco minutos de nuevo escribe y para...)

Mi consulta es si el funcionamiento este es correcto. Ya que tarda  demasiado y me estoy volviendo loco. Primero probé con los parámetros:

tar -cvf /dev/nst0 (carpeta a archivar)

y estuvo mas de 10 horas para guardar 120GB. Y después probé agregándole el -z

tar -czvf /dev/nst0 (carpeta a archivar)

Y así tardo un poco menos pero sigue de la misma manera, cachea  una pequeña porción y luego escribe en cinta y sigue así. En caso de  que este sea el correcto funcionamiento, hay manera de cambiar esto? Que  cachee todo y después escriba en cinta. O sino utilizando algún otro  comando. Tal vez necesite ajustar algo en la configuración de la unidad  de cinta o cambiar algún parámetro. Por favor agradezco su ayuda, ya que  busque información por todos lados y no logro encontrarle la vuelta.  Muchas gracias!

Pablo[/FONT]

---

### Post by guillermolisi on 2011-07-29
No me parece normal que funcione de esa forma.
Tampoco me parece normal que el tape block size este en cero ya que los cartridges vienen formateados y eso define un tamaño de bloque.

No tenes a mano la documentacion de la unidad ?

---

### Post by biale on 2011-07-29
> primero pusiera en buffer cierta cantidad de información y luego guarda esa porción en la cinta y así sucesivamente

La grabación en bloques fué el comportamiento de las unidades de cinta durante mucho tiempo. Tamaño de bloques y numero de buffers (RAM) se podía ajustar. 

Lo primero siempre es verificar que ese backup sirva para algo. listar, md5, e intentar recuperar algun archivo "prueba.txt".

Lo siguiente sería analizar la performance. No hay mas remedio que ir al manual del fabricante y tratar de sacar algo en limpio.

---

### Post by pabletesss on 2011-08-01
Gracias por contestar!
Probé cambiando el block size por el máximo que tendría que funcionar con cintas LTO2 y al intentar grabar la cinta me aparecía un error de I/O. Y lamentablemente no encontré las hojas de datos (o red books de IBM) que tengan información técnica general sobre la unidad porque ya se encuentra discontinuada. Y probé con archivos pequeños la escritura y lectura funciona de manera correcta, el tema es el tiempo que tarda en grabar 120GBs de información es muy alto. Y haciendo lo mismo desde un Windows 2003 Server R2 tarda mucho menos con la misma placa SCSI y misma unidad. Seguiré probando, por favor si se les ocurre algo les pido que me avisen. Si encuentro algo lo posteo por las dudas.

Nuevamente, muchas gracias!

Saludos,

Pablo

---

### Post by biale on 2011-08-02
Encare una googleda muy rapida con "cintas LTO2 unix tar2" y hay material, por ejemplo:

"Las aplicaciones de copia de seguridad nativas (por ejemplo, el comando UNIX® .tar) no suelen proporcionar la velocidad de transmisión por secuencias de datos necesaria para que el lector funcione al máximo rendimiento. (No obstante, si por algún motivo tiene que utilizar el software de copia de seguridad nativo de Microsoft®Windows®, en el CD que venía con el lector encontrará los controladores para usar el lector con Windows 2003.) Dell recomienda usar una aplicación de copia de seguridad con funciones mejoradas para la gestión de la memoria y otras prestaciones útiles, como TapeAlert."

Por alli aparece algun parámetro de configuración para Amanda, se menciona a Bacula. Productos que no usé nunca, pero que tendrían funcionar.

En la Wiki aparecen los parámetros de las cintas, 40 MB/s (?) o sea que tendría que funcionar mejor.

---

### Post by guillermolisi on 2011-08-03
Para que las unidades de cinta no se desgasten prematuramente y para mejorar su rendimiento, se recomienda generar una imagen de lo que se quiere resguardar en cinta en el disco y luego copiar esta imagen a la unidad.

Des esta forma, la lectura es de un solo archivo y la unidad realiza un solo ciclo de grabacion y uno solo de verificacion (en caso que corresponda). Asi se evita el clasico avance y retroceso de la cinta por partes preservando todo el mecanismo de traslacion.

Ademas, alguna unidades (por no decir todas) poseen la capacidad de compresion por hardware, con lo cual practicamente se puede duplicar la capacidad de almacenamiento del cartucho a costas de alguna baja en la velocidad de operacion de la unidad.

En modelos viejos la opcion de compresion por hardware se habilitaba/deshabilitaba con un jumper. En modelos mas modernos se puede configurar por software (consola).

El tema da para investigar mas a fondo y buscar las caracteristicas de la unidad especificamente (mas alla de los Red Books de IBM, ya que el fabricante de la unidad generalmente ronda entre dos o tres clasicos y ninguno es IBM o HP o Dell, por ejemplo).

---

### Post by pabletesss on 2011-08-11
Perdon por la demora en contestar (Fue por temas laborales). Voy a ponerme a probar lo de crear un archivo y luego pasarlo todo a la cinta. Y sino probare con Amanda o Bacula a ver como me va. Se agradece mucho la ayuda. Si llega a funcinar algo les aviso.

---

### Post by guillermolisi on 2011-08-11
La mejor forma de probar es usando la linea de comandos en consola. Es mas simple y rapido ya que podes elegir parametros en cada prueba, tenes el resultado al instante y no tenes que configurar ningun paquete de software mas o menos denso.

Meterte con Bacula y similares no solo podra enmascarar el posible problema anteponiendo cuestiones de configuracion incorrectas sino que, ademas, tenes que tomerte el trabajo de leer la documentacion y entenderla, configurarlo (aunque sea minimamente) y probar.

El documento "Bacula Problems Resolution Guide" tiene el capitulo 3 dedicado a las unidades de cinta magnetica y sugiere alguna forma de probarlas.

---

