---
title: "Requerimiento de hardware para video 1080p"
date: 2011-04-21
forum: Hardware
---

### Post by z37a on 2011-04-21
Gente, quiero ver que opinan sobre el hardware que tengo y que podria hacer para ver sin problemas video h264 en 1080p. Esto es pro que compre una camarita pocket que filma en 1080p a 30fps, peor reproducirlo en mi pc es un tanto complicado y se cuelga un poco el video, le paso a describir mi hardware actual:

CPU Athlon 64 LE-1620 @ 2.4Ghz (1MB Cache)
IGP AMD Radeon HD3200 ( Memoria a full)
6GB DDR2 800

Y bueno uso 64 bits.

Quería saber si solo cambiando el CPU podría reproducir vídeo de esta manera sin problemas, pensaba en un Phenom ya que mi mother es AM2+ (max 140W).

Alguno reproduce video en 1080p sin problemas, que hardware usan?

---

### Post by juancarlospaco on 2011-04-21
Datos del disco?
Cuanta memoria es Memoria a full?

:)

---

### Post by z37a on 2011-04-22
> **juancarlospaco said:**
> Datos del disco?
Cuanta memoria es Memoria a full?

:)

usa 256MB de RAM en estado full, y el disco es un hdd SATA II 7,2K comun y corriente, pero la filmadora almacena en una SD clase 4, que es mas lenta que el disco, asi que supongo que el disco no tiene problemas.

---

### Post by MeduZa on 2011-05-26
supuestamente para correr 1080p [no necesitas mucho hard, solo una buena GPU que se encarge de eso]("http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1").
incluso [con un ion podes hacerlo]("http://www.phoronix.com/scan.php?page=article&item=nvidia_ion_linux&num=2"), yo creo que tenes un problema de ram!

---

### Post by biale on 2011-05-27
Se podría bajar desde internet algun trailer de película que use h.264 a 1080p y ver como lo reproduce... 

Encontré los requerimientos para reproducir TDT Full seg a partir de un dongle USB, solo que en este caso ademas hay que maniobrar al dongle USB. Bajo WXP (que sería bastante equivalente), solo piden 512 Mb de RAM, CPU doble core y sobre todo que el adaptador de video soporte DirectX 9.0c o superior.

Para mi el problema pasa mucho por la relacion entre la GPU del adaptador de video + driver y los modulos del soft para la reproduccion del flujo de video.

---

### Post by alfplayer on 2011-05-28
Podés chequear con un monitor de sistema si el CPU está en 100 %.

Saludos.

---

### Post by z37a on 2011-05-29
> **MeduZa said:**
> supuestamente para correr 1080p [no necesitas mucho hard, solo una buena GPU que se encarge de eso]("http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_gpu&num=1").
incluso [con un ion podes hacerlo]("http://www.phoronix.com/scan.php?page=article&item=nvidia_ion_linux&num=2"), yo creo que tenes un problema de ram!

Viendo esto me doy cuenta que con una simple placa de video pci-express ya debería tener solucionado el tema, mas aun si es del 2008 esto! Mi problema 2 es que solo consigo una placa ATI para mi maquina (es small form factor), pero supongo que en estos 2 años debería haber mejorado mucho también AMD con sus drivers (aunque en 11.04 AMD64 me di cuenta que en mi HD3200 anda mejor el driver libre para video en 720p!!!!).

Enserio crees que con 6GB tendré problemas de RAM? espero que con 8 no ya que pienso meterle 2 mas!!! Jajajajajaj (la pc la uso para pruebas en maquinas virtuales también, de ahi tanta ram!)

Igualmente tenia que comprar una placa de video para otra PC que tengo planeado un menjunje raro entre varias pcs que tengo (es un mother que trae IGP VIA!!!!) así que apenas la consiga (espero sea esta semana) comento como quedo todo!

---

### Post by pablo.s on 2011-05-29
El video de tu camarita se "cuelga" (en la jerga se denomina  "framedropping") porque el codec con el que arman los videos  las camaras de tipo Flip (como las Kodak de bolsillo) es del tipo  Quicktime H.264 con una compresión que no está optimizada.  Dan por hecho que ese video va a ser convertido a otro formato  con otra compresión, asi que no se esmeran mucho con el dato  que vos quieras verlo en tu computadora.  No, no tiene mucho que ver ni la tarjeta de video, ni la memoria,  ni para donde hayas orientado la budinera. Simplemente hay que recodificar el video con un bitrate similar o incluso un poco inferior  en un codec mas civilizado, por ejemplo en MPEG 4 Xvid y vas a notar que no hay mas framedropping. Para codificarlo podes utilizar Avidemux, que tiene predefinidos los ajustes para la mayoria de los codecs domesticos.

---

### Post by biale on 2011-05-29
> Quicktime H.264 

Por eso la idea de usar un trailer de pelicula HD para probar un poco el hardware con algo mas tipico.

Y tambien hay que tener en cuenta el SW reproductor que se use.

La duda que me queda es si con la TDT los codecs "basicos" van a terminar adheridos a esas normas.

---

### Post by z37a on 2011-05-31
Me imagine que habia un problema con el codec, aun asi el video en 1080p de un mkv descargado en internet tambien lo hace a veces. Apenas llegue del trabajo coloco la placa de video que compre hace un rato a ver que tal andan los video 1080p tanto lso mkv como los quicktime y les comento como resulto, compre la unica placa que consegui con low profile, una ati radeon hd4670, la version de 1GB, a ver como funciona, igualmente como comente, creo, necesitaba una placa de video para otra PC (una cosa rara que voy a hacer luego, entre 3 pcs sacar 2 mas copadas (y justo una tiene pci express con onboard VIA!!!! que horror). Asi que bueno la placa ya la compre, apenas la instale comento que sucedio, como se ven los videos.

PD: Youtube en 1080p tambien medio que se ve mal, pero puede ser pro el flash, igualmente en html5 no se pro que lo veo aun peor tanto en 720p como 1080p!!!!

---

### Post by z37a on 2011-05-31
Antes que nada perdón por el doble post, pero es una continuación, no puedo editar al anterior sin borrarlo!

Bien la placa ya esta instalada, e hice las pruebas que quería hacer con resultados mas o menos buenos!

El video en Youtube en 1080p dispara al CPU y no hay forma, es el maldito flash, y el html5 no se por que pero no anda bien con el webm en FF4!

El video de las series bajadas en 720p mejoro muchísimo! en 1080p mejoro algo, peor cada tanto se traba.

El video en h264 de quicktime sigue igual de mal, peor como dijeron mas arriba es el codec, no hay con que darle!

Creo que con un CPU un poquitin mas potente ya tendría todo andando de 10! Flash me come al CPU!!!!

Por otro lado me estoy ahorrando 256MB mas de RAM (jajaj si teniendo 6GB medio al ....) y bueno la placa va a tener su uso luego, no probe aun con el regnum online como funciona, pero globalmente no es tan desastroso, lo veo positivo comprar la placa!

---

### Post by biale on 2011-05-31
H.264 fue previsto para ahorrar espacio hasta donde se pudiera y optimizar asi las mecesidades del almacenamiento/ ancho de banda de transmision. Hay mucho extracosto de procesamiento. La CPU se va a los caños?  VLC 1.2?

Se podría intentar una conversión que no añada pérdidas. De todas maneras (y como ya dijeron) lo mas sencillo es guardar los videos originales sin tocarlos y generar una version transcodificada que sea visible en HW que este dando vueltas. Suena feo, pero es lo que hacen todos los fotógrafos a la hora de generar versiones que no van a impresas.

El tema es interesante porque vamos a tener mucho material HD para reproducir en HW limitrofe...

---

