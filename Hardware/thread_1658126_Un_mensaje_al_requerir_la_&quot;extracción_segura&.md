---
title: "Un mensaje al requerir la &quot;extracción segura&quot; de un disco removible"
date: 2011-01-02
forum: Hardware
---

### Post by mecdem on 2011-01-02
:?: :p :?:
Hola. La Tía MEC de nuevo por acá haciendo consultas a la gente sabia.

Equipo: Toshiba Satellite A105-S4384
Sistema: Ubuntu 10.04 (32 bits)
__________

Tengo un par de discos removibles que conecto habitualmente a la notebook.
Uno de ellos comenzó a tirar un mensaje al pulsar con botón derecho sobre su ícono en el escritorio para usar la opción extracción segura.

El mensaje dice:

[I]NO SE PUDO PARAR LA UNIDAD
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:01d.7/usb1/1-3)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory[/I]

Mi inglés es suficientemente pobre como para no estar yo muy segura de lo que dice el mensaje.
El disco aparentemente queda sin actividad, al menos no se lo siente vibrar al tocar el estuche.

La pregunta: ¿es importante ese mensaje? ¿preanuncia alguna e-catástrofe?

Gracias anticipadas a quien tenga la amabilidad de darme respuesta y quitarme la inquietud que me causa la aparición de ese mensajito.

Cordial saludo.
MEC

---

### Post by biale on 2011-01-03
Por las dudas habría que correr algún programa para la verificacion del sistema de archivos del usb.

¿El formato del sistema de archivos es "fat"? Luego de desmontar (extraer) el dispositivo, Gparted tiene una opción para verificar.

---

### Post by mecdem on 2011-01-03
Hola Biale.
Gracias por tu respuesta.

Seguí tus instrucciones. Instalé el GParted. Previa copia de resguardo del contenido, desmonté y verifiqué el dispositivo y no dió ninguna información de error... pero siguió tirando el consabido "NO SE PUDO PARAR LA UNIDAD. Error detaching...".

Se me ocurrió que a lo mejor formateándolo se arreglaba (el disco vacío era una gran tentación para los viejos hábitos de una vieja-windowsera-vieja). Así lo hice. En FAT32, tal como estaba antes.
No pasó nada. Sigue con el mensaje "NO SE PUDO PARAR LA UNIDAD. Error detaching...". Pero la novedad es que no puedo hacer ahora la verificación con GParted.

Pongo imágenes:
[http://picasaweb.google.com/mecdem/BoticaII#5558134632003559138](http://picasaweb.google.com/mecdem/BoticaII#5558134632003559138)
En la 1 aparece el triángulo con el signo de admiración dentro.
[http://picasaweb.google.com/mecdem/BoticaII#5558134635629791954](http://picasaweb.google.com/mecdem/BoticaII#5558134635629791954)
En la 2 se ve la información: "Imposible encontrar el punto de montaje...".
Los paquetes de soft que menciona al final he visto que ya están instalados.

Otros detalles observados (que no sé si sirven pero porsi los menciono):
Cuando conecto el dispositivo a la notebook -o a la netbook- es reconocido, aparece su ícono en el escritorio, y permite copiar archivos en él y luego leerlos. La anomalía sigue apareciendo sólo cuando se ejecuta la opción "extraer unidad de forma segura".

Amigo Biale, si cuando me pongas tu respuesta no te contesto enseguida es porque el jueves parto de vacaciones a un lugar donde no tengo internet "a mano". ¡¡Sí, existen esos lugares!! Pero trataré de recoger tus instrucciones lo antes posible, ejecutarlas e informarte.

Gracias mil y un abrazo. MEC

---

### Post by biale on 2011-01-04
Digamos que la idea no era formatearlo...

Solo 60 Gb! Puedo suponer que es un disco usb "unidad sellada" de fábrica?  O es un disco chico y comun dentro de una caja adaptadora IDE/SATA a USB?  Un pendrive? marca/modelo?

---

### Post by mecdem on 2011-01-04
> **biale said:**
> Digamos que la idea no era formatearlo...

Sin duda!! Por eso dije que fue maña de ex-windowsera...
Cuesta quitarse las malas mañas :-\"
Volví a cargarle el contenido que tenía, y -como dije en el mensaje anterior- la anomalía sigue apareciendo sólo cuando se ejecuta la opción "extraer unidad de forma segura".

> Solo 60 Gb! Puedo suponer que es un disco usb "unidad sellada" de fábrica?  O es un disco chico y comun dentro de una caja adaptadora IDE/SATA a USB?  Un pendrive? marca/modelo?

Es un disco chico, sobreviviente de una notebook que murió hace tiempo. Está dentro de una caja adaptadora con conexión mediante USB. Datos del disco en [http://picasaweb.google.com/mecdem/BoticaII#5558336754193560962](http://picasaweb.google.com/mecdem/BoticaII#5558336754193560962)

Disculpa que no te pasara antes esta info, pero no sé cuál es la necesaria para hacer bien la consulta. Espero haber comprendido tu pregunta y ojalá esté completa mi respuesta.

Nuevamente, gracias por tu atención.
__________

> Solo 60 Gb!

(¡¡Nada de reírse de mis disquitos ¿eh?!! [el otro que tengo es de 40 GB] que buena utilidad me prestan para ciertos usos.
Hace poco tuve en las manos un pendrive [o disco mini removible, no estoy segura] de 1 TB. ¡¡Impresionante!! Pero andá a perderlo... Jua!! Como no tengas tus backups en otra parte...)
__________

Un abrazo. MEC

---

### Post by biale on 2011-01-04
Bien, entonces estamos seguros que el disco esta formateado en su totalidad.

De todas maneras observo que gparted esta pidiendo sus modulos opcionales para el manejo del sistema de archivos. Conviene instalarlos:

(Ver [http://picasaweb.google.com/mecdem/BoticaII#5558336754193560962](http://picasaweb.google.com/mecdem/BoticaII#5558336754193560962) )

    sudo apt-get install dosfstools mtools

(1) Hay actualizaciones (fuse) para Lucid, conviene aplicarlas, si no lo habias hecho

(2) Conviene repetir la verificación. Incluso puede hacerce bajo alguna computadora Win.

(3) Al desmontar, "dmesg" tira algun mensaje de error distinto o que aporte algo?

(4) Si arrancamos con el nucleo de respaldo (o con live cd) la situación se repite?

Mientras busco algo, te comento que si el sistema de archivos es fat y ademas el disco se abrió solo para leer sus contenidos, el mensaje no es preocupante. Y si por contrario modificaste los contenidos del disco, es un llamado de atención y debe ser tenido en cuenta.

Realmente no hubo risas por el tamaño del disco. Incluso no muy lejos tengo un disco SCSI de 20 Gb girando en un servidor de red. Un abrazo.

---

### Post by mecdem on 2011-01-04
> **biale said:**
> ...De todas maneras observo que gparted esta pidiendo sus modulos opcionales para el manejo del sistema de archivos. Conviene instalarlos:...
    sudo apt-get install dosfstools mtools

Ya están instalados.
"Los paquetes de soft que menciona al final he visto que ya están instalados", decía en un mensaje anterior.

> 
(1) Hay actualizaciones (fuse) para Lucid, conviene aplicarlas, si no lo habias hecho...

Querido amigo, veo que hay bastantes cosas que hacer -mis "deberes para el hogar"- y ya no me dan los tiempos. Cuando regrese de ese incivilizado mundo que no tiene conexión a internet, ejecutaré prolijamente tus instrucciones y reanudaré la consulta informándote de los resultados obtenidos.

> Realmente no hubo risas por el tamaño del disco. Incluso no muy lejos tengo un disco SCSI de 20 Gb girando en un servidor de red. Un abrazo.
Ja, ja, nunca tomes en serio mis "rezongos". Son pura cháchara.
:lolflag:.

Te agradezco toda la información que me has brindado.
Creo que en esta consulta has tenido en cuenta lo que dije acerca de que me marchaba a vacaciones, así que mi especial agradecimiento por la mucha rapidez con que has ido volcando tus respuestas.

Queda la consulta en "stand by".
Un abrazo. MEC

---

### Post by mecdem on 2011-03-19
Hola Biale.
Ando cerrando consultas que quedaron stand by.

Después de unas cuantas comprobaciones, llegué a la conclusión de que el origen del mensaje que motivó este hilo está en el disco removible. Y que pese al mensaje, el aparatito sigue andando normalmente.

"Si funciona, no lo toques".

Así que cierro la consulta muy agradecida por tu ayuda y tu tiempo. MEC.
):P

---

### Post by asterix77 on 2011-03-21
A mi hace tiempo me sucedió algo parecido, no recuerdo los errores que me arrojaba en forma exacta, pero si tenía problemas con un disco interno que lo dejé como externo conectado por puerto usb. De pronto sin aviso como que se desmontaba, y no podía encontrar la unidad ni desmontarla, pero podía escribir y borrar archivos sin problemas mientras no se desmontaba. 

Me sucedía tanto en windows como en ubuntu, era como que después de un tiempo conectado por usb, entraba en una especie  de reposo para ahorrar energía, o algo así. Quizás el problema es que no alcanza a recibir la energía necesaria para funcionar por usb

Finalmente lo que hice fue dejarlo como disco interno conectado vía puerto SATA y se solucionó el problema.

Aquí se necesitaría la opinión ya de un experto para determinar si la energía entregada al disco, es la suficiente o no para hacerlo funcionar en forma correcta.


Saludos

---

### Post by mecdem on 2011-04-01
Asterix, gracias por "el agregadito".
Saludos.

---

