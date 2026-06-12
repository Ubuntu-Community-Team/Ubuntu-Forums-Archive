---
title: "Bangho Fit H10 Netbook."
date: 2009-11-09
forum: Hardware
---

### Post by Apipote on 2009-11-09
Hola a todos.

Me compré ayer en Falabella este netbook en 1750 pesos, luego de mucho forear.

Me gustaría leer sus opiniones, o si alguien hizo un review con linux. He visto buenas opiniones en taringa, pero para windows.

Parece la ecuación costo beneficio ideal por lo que trae. Viene con win 7 starter que le volé a la hora de tenerla.
Unr anda muy bien, pero no me reconoce el wifi/bluetooth/gprs que viene en misma placa mini pc 3dsp.
En la página oficial los drivers no soportan (aún) Karmic.

Alguna solución?

Gracias por adelantado !

---

### Post by guillermolisi on 2009-11-09
> **Apipote said:**
> Hola a todos.

Me compré ayer en Falabella este netbook en 1750 pesos, luego de mucho forear.

Me gustaría leer sus opiniones, o si alguien hizo un review con linux. He visto buenas opiniones en taringa, pero para windows.

Parece la ecuación costo beneficio ideal por lo que trae. Viene con win 7 starter que le volé a la hora de tenerla.
Unr anda muy bien, pero no me reconoce el wifi/bluetooth/gprs que viene en misma placa mini pc 3dsp.
En la página oficial los drivers no soportan (aún) Karmic.

Alguna solución?

Gracias por adelantado !
Mi mujer tiene una que vino con Vista que duro cinco dias hasta que llego JJ y le paso el trapo.

Los drivers que use para la inalambrica y Bluetooth me los paso mi hermano que tambien tiene una y a el se lo mandaron los chinos que fabrican la interface.

Originalmente era para una de las primeras versiones de kernel de JJ pero esos mismos drivers tambien funcionan en JJ solo que hay que editar un script para que no chille el instalador cuando verifica la version del kernel. Aun no los probe con KK.

[En este thread en Ingles]("http://ubuntuforums.org/showthread.php?t=1234213") hago un intercambio por este tema pero sobre una variante de la misma interface.

Si no da para entender avisame y me vuelvo a explayar en detalle.

---

### Post by Apipote on 2009-11-09
Mmmm en la pag oficial de 3dsp en tu thread, figura el driver para 9.04. 
Esperaré a que salga el 9.10.

Gracias estimado.

---

### Post by guillermolisi on 2009-11-09
> **Apipote said:**
> Mmmm en la pag oficial de 3dsp en tu thread, figura el driver para 9.04. 
Esperaré a que salga el 9.10.

Gracias estimado.
Originalmente el driver habia salido para kernel 2.6.28-11, que en realidad es lo que importa mas alla si fue usado con 9.04 u otra version. Alguien edito el script de instalacion para que no termine por ser otra version del kernel y funciona muy bien con el 2.6.28.15, el ultimo de JJ.

Si llego a probar con la maquina de mi mujer aviso que resultados tuve con KK.

---

### Post by Apipote on 2009-11-09
Gracias Guillermo.
No hay mucha experiencia con esta netbook por lo que veo.
Slds

---

### Post by guillermolisi on 2009-11-09
> **Apipote said:**
> Gracias Guillermo.
No hay mucha experiencia con esta netbook por lo que veo.
Slds
Con kernels hasta 2.6.28-15 la tengo probada a fondo, con ext4, efectos de escritorio, microfono y camara (usando aMSN).

Si suspendes/hibernas la maquina el WiFi se corta y no se vuelve a conectar hasta que reinicias.

La bateria normal que trae de fabrica rinde alrededor de 2:30 Hrs. con display al 50% del brillo maximo, wifi y bluetooth funcionando.

Las teclas de acceso rapido no funcionan todas (tampoco me puse a investigar para configurarlas).

Wifi con muy buen alcance. El driver incluye un gestor de conexiones medio rudimentario pero que funciona. La antena se apaga y enciende por software (no con la combinacion de teclas Fn+<algo>).

El kernel que trae Karmic es bastante reciente.

---

### Post by Apipote on 2009-11-11
Esperaré entonces. Mientras que siga con el Win 7 que trae de fábrica.
Sigo en contacto, y espero tu próxima review sobre Karmic y esta linda máquina.
Gracias Guillermo !

---

### Post by Apipote on 2009-11-25
Hola a todos.

Alguna novedad sobre este thread?

Por mi parte, aún no encontré nada para instalar el wifi en la fit h10 con UNR 9.10.

Slds.

---

### Post by guillermolisi on 2009-11-25
> **Apipote said:**
> Hola a todos.

Alguna novedad sobre este thread?

Por mi parte, aún no encontré nada para instalar el wifi en la fit h10 con UNR 9.10.

Slds.
Muy a mi pesar y por exceso de obligaciones, aun no probe UNR 9.10 con el driver de 3DSP.

En cuanto lo haga comento resultados para la misma maquina y con el ultimo kernel que este vigente en ese momento.

---

### Post by Apipote on 2009-11-25
Sabés Guillermo que está teniendo mucho éxito esta máquina ?

---

### Post by guillermolisi on 2009-11-27
Buenas noticias !

Los fabricantes chinos liberaran los drives para Ubuntu en los proximos dias de Diciembre.

Mas detalles, con el link a la version que corre con el kernel 2.6.31, [aqui]("http://www.laconsolablog.com/2009/11/07/driver-3dsp-bluew-2310-para-kernel-2-6-31-liberado/").

---

### Post by Apipote on 2009-11-28
Cool !!
Tnx

---

### Post by Sleeping Beauty on 2009-12-01
Gente, tengo que instalar Ubuntu en una Netbook Bangho B-N0X1. Busqué un poco en la red pero no encontré demasiado. Alguno la tiene o la conoce? Que sería mejor Ubuntu desktop  o Remix?
Grazie!

---

### Post by guillermolisi on 2009-12-01
> **Sleeping Beauty said:**
> Gente, tengo que instalar Ubuntu en una Netbook Bangho B-N0X1. Busqué un poco en la red pero no encontré demasiado. Alguno la tiene o la conoce? Que sería mejor Ubuntu desktop  o Remix?
Grazie!
Por ahora te recomendaria Ubuntu Desktop o UNR, ambas en version JJ ya que aun no estan disponibles los drivers WiFi/Bluetooth para el kernel de la 9.10

Esta maquina la probe con Desktop 9.04 y UNR 9.10 y mas o menos la autononia es la misma. No vi gran diferencia a pesar de que UNR deberia estar mas afinado para procesadores Atom.

---

### Post by Sleeping Beauty on 2009-12-01
Gracias Guille!!! Despues te cuento como quedó ;)

---

### Post by tigus on 2009-12-08
Buenas a todos en el foro. Primero que todo me presento, soy Gustavo de Mendoza, Argentina.
Buscando en google sobre instalar ubuntu enun Bangho H10 me topé con este hilo. Les quería consultar si alguien de Uds tuvo problema en la instalación. 
He bajado varias imágenes (.img) de UNR 9.04, ya que es para la versión que están hoy en día los drivers disponibles para la placa de wifi y bluetooh, y en todas a la hora de instalar me da error copiando los archivos, error de I/O. Probé de leer todos los archivos de pen drive copiándolos y no hay problema. Todas la imágenes que he bajado tienen el mismo tamaño, mismo MD5 y cuando las uso como "live" en la netbook funciona todo bien, el problema se me presenta a la hora de instalarla... alguna sugerencia? a alguien le ha pasado?
Un poco más de detalle, mi idea es instalar ubuntu conservando W7 starter ya que hay aplicaciones de cursos de mi sra de preguntas y respuestas , y otras tributarias que corren sólo en él.
Desde ya les agradezco su ayuda y espero no haberlos aburrido.
Saludos
pd: alguna idea de si va a salir el driver de la placa wifi para la UNR 9.10?

---

### Post by guillermolisi on 2009-12-08
Bienvenido.

Para hacer la instalacion en Dual Boot mode tenes [este thread]("http://ubuntuforums.org/showthread.php?t=1280260") que te explica como lograrla.
No se que consideracion especiales habra que tener con Windows 7, de haber alguna por el tema Grub.

Luego, que pasa si en lugar de instalar la version UNR instalas la desktop ?
Probe las dos y la verdad que con la UNR 9.10 en modo Live no note mayor diferencia en el consumo de energia con respecto a la version desktop.

Segun los fabricantes chinos, los drivers para el kernel de la 9.10 estarian por salir. De hecho ya liberaron para las placas USB.

Tambien dijeron que abririan el codigo para convertir los drivers en publicos en poco tiempo mas.

---

### Post by tigus on 2009-12-08
Hola Guillermo, gracias por responder tan pronto!
Aunque parezca extraño y contrario a la mayoría de los comentarios que he leido, nos gustó la interfazde UNR :). De todos modos voy a realizar una prueba con UNR 9.10 y con Desktop 9.04 o 9.10. 
Gracias por la referencia al hilo de dual boot, son los pasos que creo haber seguido, pero bueno... por algo está el error, asique probaré de nuevo.
Saludos y los mantengo al tanto

---

### Post by tigus on 2009-12-09
Buenas a todos, he probado con otra imagen y el mismo I/O error durante la instalación... probé con UNR 9.10 y lo mismo. El mensaje de error aconseja grabar el cd a menor velocidad o limpiarlo, el tema es que en realidad estoy instalando desde un pen drive. Buscando en google, que no encontré mucho por cierto, se aconseja volver a bajar la imagen. 

Si le hago un chequeo a la imagen de MD5 con 
   md5sum -c <imagen> 
me da error de que faltan varios archivos, ahora, si genero el MD5 con  
   md5sum -b <imagen>
me genera el mismo md5 que el publicado junto a la imagen, por lo que estoy aún más perdido...

He probado instalarlo diciéndole que él cree las particiones, creándolas yo a mano y no hay forma que se instale. Podrá ser un error de disco de la netbook? (Espero que no... es recién comprada...)

La imagen del 9.04 es .img por lo que usé el imagewriter, la del 9.10 es .iso por lo que usé el unetbootin en windows.

Alguna sugerencia que me puedan aportar? 
Alguna url de dónde poder descargar las imágenes que tengan su MD5 válido?

En la instalación me genera la estructura de directorios y quedan montados en /target, pero al parecer se está quedando al leer algunos archivos del pen drive. Probé copiar todo el contenido del pendrive a disco como para verificar que no fuera error de lectura de archivos del pen drive y no hubo problemas... estoy más perdido que perro en cancha de bochas...

Saludos
__

---

### Post by Apipote on 2009-12-09
Mmmm no es muy científico mi consejo, pero yo que vos formatearía todo el disco con Ubuntu y chau el Starter, de última te sacás la duda y lo reinstalás si lo necesitás. Está por todas partes y es legal porque tenés la clave abajo de la máquina.
Si es radical, pero es lo que haría.
Yo también uso Win7 a la espera de lo que bien escribió Guillermo.

Slds

Pd: Cuando instalé UNR 9.10, salvo la falta del driver wifi, lo demás fue rápido y sin problema alguno.

---

### Post by tigus on 2009-12-09
Hola Apipote, gracias por el consejo. Me parece que voy a ir por ese lado para sacarme la duda. De todos modos les dejo una dirección con gente que le ha pasado lo mismo, al parecer es un bug en ubuntu, al menos así lo plantean.
Una solución que mencionan es dejar sólo un módulo de memoria en el pc, pero no es aplicable a mi caso....

[https://bugs.launchpad.net/ubuntu/+bug/245794](https://bugs.launchpad.net/ubuntu/+bug/245794)

Saludos

---

### Post by tigus on 2009-12-09
Buenas a todos. Les quería contar que pude instalar UNR 9.10 en la Banghó. Usé la misma ISO que estaba usando antes, sólo que la grabé en un pendrive de 4GB en lugar de uno de 8GB y utilicé otro puerto USB, creer o reventar....
Saludos a todos

---

### Post by tigus on 2009-12-09
Probé instalar la versión de los drivers usb para la 9.10 y tomó la placa wifi bluetooh. Si uno mira los dispositivos en windows 7 se puede ver que lo usa como dispositivo usb, al menos así es en la Banghó FIT H10 que tenemos.
Lo único que... siempre hay un pero... se "cuelga" de vez en cuando, aún estoy en pruebas.
Si alguien más prueba lo mismo me gustaría saber qué resultados obtuvo.
Saludos a todos.

---

### Post by Apipote on 2009-12-09
Leí que hay quienes tienen la wifi usb en algunas fit h10.

[http://www.laconsolablog.com/2009/11/07/driver-3dsp-bluew-2310-para-kernel-2-6-31-liberado/](http://www.laconsolablog.com/2009/11/07/driver-3dsp-bluew-2310-para-kernel-2-6-31-liberado/)

No es el caso de la mía, que solo levanta en win7 los drivers miniPci y nada los usb.

A esperar en mi caso.

---

### Post by Apipote on 2009-12-11
Estimados, los drivers para 9.10, finalmente salieron hoy.

[http://3dsp.com.cn/web_html/download.html](http://3dsp.com.cn/web_html/download.html)

Si pueden postear sus experiencias se los agradezco.

Slds.

---

### Post by Mariano Oliveto on 2009-12-29
> **tigus said:**
> Probé instalar la versión de los drivers usb para la 9.10 y tomó la placa wifi bluetooh. Si uno mira los dispositivos en windows 7 se puede ver que lo usa como dispositivo usb, al menos así es en la Banghó FIT H10 que tenemos.
Lo único que... siempre hay un pero... se "cuelga" de vez en cuando, aún estoy en pruebas.
Si alguien más prueba lo mismo me gustaría saber qué resultados obtuvo.
Saludos a todos.

Hola Tigus y gentes en general,

Confirmo que tengo exactamente el mismo problema con la placa wifi bluetooth USB de la Bangho Fit H10 y los drivers recién bajados de la página del fabricante, usando tanto Ubuntu 9.10 y UNR 9.10 (probé dos instalaciones de cero).

Bah, en realidad a mi entender los cuelgues no son erráticos, sino que son cuando me conecto a la red wifi de casa (con WPA2 Personal) y empieza el tráfico por internet (tanto navegando con el Firefox como usando el update manager). El sistema está como sale derecho de la instalación, aún no actualicé nada (podría dejarlo actualizando con el cable de red). No probé conectandome a redes inalámbricas sin protección tampoco.

Lo que voy a probar ahora es ver si se cuelga también con tráfico que no sea por internet (supongo que debería ser lo mismo pero sinceramente no sé tanto como para estar seguro y sería un dato más).

Me pongo a disposición si quieren probar alguna cosa y les agradecería mucho que avisen si tienen alguna novedad al respecto (si yo tengo alguna seguro voy a postear).

---

### Post by tigus on 2010-01-03
Hola Mariano, cómo va todo? Espero vos y el resto del foro hayan empezado muy bien el año.

Tal como lo mencionas, el "cuelgue" sucede cuando comienza el tráfico. En casa, que es donde estoy probando, también tengo la red wifi asegurada con wpa2. No he probado sin seguridad, es que he andado con falta de tiempo :) . 

Si tengo alguna novedad la posteo, mientras me mantengo al tanto de cualquier novedad.

Saludos a todos.

---

### Post by Mariano Oliveto on 2010-01-23
Bueno, finalmente me decidí desde hace un tiempo ya instalar el UNR 9.04 y santo remedio. De todas maneras preferiría poder tener el 9.10 funcionando bien, pero sinceramente ahora no dispongo del tiempo (y probablemente hasta Mayo/Junio la situación no cambie). Cuando pueda voy a volver a probar a ver si resolvieron el problema de los drivers. ¿Ustedes tuvieron alguna novedad?

Por otro lado (espero no estar muy off-topic, pero el título del post es sobre la netbook en general, si no armo otro post), quería saber si alguno se avivó de cómo cambiar la configuración del Ctrl y Shift izquierdos. Vieron que cuando seleccionan con las flechas y el Ctrl y Shift de la izquierda las flechas en realidad se comportan como las teclas Inicio, AvPág, RePág y Fin. Me gustaría configurarlas de tal manera que este comportamiento sea con el Ctrl y Shift de la derecha (que son los que menos uso). ¿Alguna idea?

---

### Post by guillermolisi on 2010-01-23
> **Mariano Oliveto said:**
> 
Por otro lado (espero no estar muy off-topic, pero el título del post es sobre la netbook en general, si no armo otro post), quería saber si alguno se avivó de cómo cambiar la configuración del Ctrl y Shift izquierdos. Vieron que cuando seleccionan con las flechas y el Ctrl y Shift de la izquierda las flechas en realidad se comportan como las teclas Inicio, AvPág, RePág y Fin. Me gustaría configurarlas de tal manera que este comportamiento sea con el Ctrl y Shift de la derecha (que son los que menos uso). ¿Alguna idea?
Si, me parece lo mas indicado abrir un nuevo thread considerando que es mas una cuestion de software que de hardware, ademas de que no esta relacionado con el tema que dio origen al este thread (por mas que el title no sea muy especifico).

---

### Post by tigus on 2010-01-29
Buenas a todos.
Mariano, dices que con el UNR 9.04 no tuviste más el problema del "cuelgue" al activar la red wifi?
Probaste con WPA2?
Pregunta a los lectores en gral, piensan o tienen algún dato de que UNR 10.04 de soporte a nuestras placas?
Saludos a todos

---

### Post by Mariano Oliveto on 2010-01-29
> **tigus said:**
> Buenas a todos.
Mariano, dices que con el UNR 9.04 no tuviste más el problema del "cuelgue" al activar la red wifi?
Probaste con WPA2?
Pregunta a los lectores en gral, piensan o tienen algún dato de que UNR 10.04 de soporte a nuestras placas?
Saludos a todos

Hola Tigus,

Exactamente, no tuve problemas de cuelgues con el UNR 9.04. Probé en la red con WPA2 Personal de casa y sin problemas (salvo alguna que otra perdida de conexión pero me parece que es porque engancha el motor del aire acondicionado... ¿puede ser?)

Y el otro problema que tuve fue que en otra red WPA2 Personal primero se conectó bien y después dejó de poder conectarse. Cuando aparecía el cuadro de diálogo de conexión en vez de decir que era una red con WPA2 Personal decía otro modo (no lo recuerdo). Pero no sé bien, cuando tenga un poco de tiempo investigaré y cualquier cosa posteo.

Espero que sirva la info. Si quieren más detalles (y se los puedo dar) pregunten nomás.

Abrazo!!

---

### Post by guillermolisi on 2010-02-08
Acabo de actualizar, previa verificacion Live con 9.10 UNR, una Bangho del modelo del asunto y note que los fabricantes de la placa inalambrica han mejorado mucho el driver.
Las mejoras que note estan en el alcance y en la facilidad de configuracion y conexion, ademas de una mas completa documentacion.

Los drivers los baje de [aqui]("http://dl.dropbox.com/u/737884/BlueW-2310X_2.3.0_091211_ubuntu9.10_MiniPCI_2.6.31-16.tar.gz") ya que la maquina posee placa miniPCI.

Antes de instalar hay que verificar que version de kernel se esta usando, con "uname -a" (y estar conectado a Internet via cable). Con el dato en mano y si no coincide con la version de kernel que viene por defecto en la distribucion del fabricante, hay que copiar y renombrar el directorio que contiene los drivers originales que se encuentra dentro de otro llamado "drivers". Al renombrarlo se debe ajustar la version del kernel en uso en el nombre de ese directorio, ejemplo:

Si el directorio original se llama 2.6.31-16-generic, copiarlo y nombrarlo como 2.6.31-xx-generic, donde xx debera coincidir con la version del kernel en uso.

Tambien hay que editar el archivo de instalacion, Install_3DSP.sh, para agregar la version del kernel sobre la cual se instalaran los drivers:
```
#For verifing kernel.
function VerifyKernel()
{
  echo -n " * Verifying kernel..."
  CURRENTKERNEL=`uname -r`

  case "${CURRENTKERNEL}" in
      [COLOR=Blue]"2.6.31-16-generic" | "2.6.31-18-generic"[/COLOR] )
        ${PRINTOK};;
      *                   )
        ${PRINTFAIL}
        handle_error "NOTSUPPORTKERNEL";;
  esac
}

#For installing modules
```
En la linea en azul agregue la version 2.6.31-18-generic.

Luego correr con sudo el instalador y listo. No deberian tener problemas.

---

### Post by Mariano Oliveto on 2010-05-02
Hola muchachos. Les comento (por si no sabían) que la gente de 3DSP liberó el código fuente de los drivers de la placa USB. Por lo tanto ya se pueden compilar sin necesidad de esperar que distribuyan los paquetes deb para cada kernel.

Yo estoy corriendo en este preciso momento un Ubuntu UNE 10.04 Lucid Lynx en la Banghó Fit H10 desde un Live USB y pude compilar los drivers, el UWB (el programita para habilitar la placa) y el WiFi radar y están funcionando bien (por ahora... estoy posteando desde ella misma). 

Les dejo el link de donde me enteré que habían liberado los drivers y donde hay links para bajarlos:

[https://answers.launchpad.net/ubuntu/+question/78047](https://answers.launchpad.net/ubuntu/+question/78047)

Lo único que me trajo problemas fue que luego de hacer el make hay que renombrar el directorio "new_bluetooth" a "bluetooth" y el "private/new_bluetooth_priv/" a  "private/bluetooth_priv". Eso lo saqué de la siguiente página:

[http://ubuntuforum-br.org/index.php?topic=60512.750](http://ubuntuforum-br.org/index.php?topic=60512.750)

Si tienen alguna duda posteen, no sé si voy a poder ayudar pero trataré.

Prueben el 10.04 UNE, está mucho mejor adaptado que el 9.04 para pantallas de 10" (no probé mucho el 9.10 porque se me tildaba el S.O. cuando usaba la WiFi).

Ahora les hago una pregunta, ¿con el código fuente liberado, existe posibilidad de que lo incluyan en la distro para que la placa esté soportada sin necesidad de instalarlos (como ocurre con la mayoría del hardware)? ¿Saben a quién habría que pedírselo?

Abrazo!

---

### Post by del_Brujo on 2010-05-07
> **Mariano Oliveto said:**
> Hola muchachos. Les comento (por si no sabían) que la gente de 3DSP liberó el código fuente de los drivers de la placa USB. Por lo tanto ya se pueden compilar sin necesidad de esperar que distribuyan los paquetes deb para cada kernel.

Me sale error al querer instalar el driver. UNR 9.10 con el driver que habían compilado ellos andaba bien.
Esto es lo que sale después del make install

```
cp -f bus/3dspusbbus.ko /usr/local/3DSP/usb/
cp -f bluetooth/3dspusbbt.ko /usr/local/3DSP/usb/
cp -f wlan/3dspusbwlan.ko /usr/local/3DSP/usb/
cp -f private/bluetooth_priv/3dspusbbtpriv.ko /usr/local/3DSP/usb/
cp -f private/wlan_priv/3dspusbwlanpriv.ko /usr/local/3DSP/usb/
cp -f tdspusbcardinit /etc/init.d/
chmod 755 /etc/init.d/tdspusbcardinit
Inserting modules...
insmod /usr/local/3DSP/usb/3dspusbbus.ko
sleep 1
insmod /usr/local/3DSP/usb/3dspusbwlanpriv.ko
sleep 1
insmod /usr/local/3DSP/usb/3dspusbwlan.ko
sleep 1
insmod /usr/local/3DSP/usb/3dspusbbtpriv.ko
sleep 1
insmod /usr/local/3DSP/usb/3dspusbbt.ko
insmod: error inserting '/usr/local/3DSP/usb/3dspusbbt.ko': -1 Unknown symbol in module
make: [install] Error 1 (no tiene efecto)
sleep 1
Creating devices file for 3DSP driver...
mknod  /dev/tdspusbbus c `awk '$2=="3dspusbbus" {print $1}' /proc/devices` 0
```

---

### Post by tigus on 2010-05-07
Buenísimo el dato Mariano, a probar compilar los drivers entonces.
Muchas gracias.

Saludos

---

### Post by Tobisc on 2010-05-08
Hola gente!
 Les comento que estoy en la netbook fit h10 y un flamante lucid actualizado desde karmic.
 Traté como mariano de compilar los drivers para esta tarjeta wireless pero obtengo el mismo error que del_brujo. Es mas, seguí todos los pasos posteados [[COLOR="Red"]aquí[/COLOR]]("http://www.vivaolinux.com.br/topico/OTRS/3dsp-no-Ubuntu-10.04") y tampoco me funcionó.
 Podrías mariano o alguien, tirar alguna idea de qué es lo que puede estar fallando?
 Hace unas horas que estoy bsucando una solucion pero no encuentro nada.
 Desde ya gracias!

---

### Post by tigus on 2010-05-09
Buenas a todos! Probado compilar en Ubuntu 10.04 y todo de primera, ya tenemos wifi 3dsp en la Fit H10, gracias Mariano por el dato.

Para quienes les esté dando error, se me ocurre que podrían probar, si es que no lo están haciendo y espero no me abuchen por proponer esto..., ejecutar todos los comandos del README como root.

Saludos

---

### Post by tigus on 2010-05-09
Buenas a todos, seguimos la cronología... Quedó todo funcionando, aunque el tema de íconos en Accesorios, desaparecieron... quedó todo instalado pero nada de íconos.
Aunque "todo" funciona, salvo bluetooh por el tema del error en el módulo que comenta del_Brujo.

Pregunta tal vez un poco fuera del hilo, para dejar que se levante el driver (/usr/bin/uwb) y el wifi-radar en el inicio del SO, dde debería colocarlos? En /etc/rc.local o en /etc/init.d como script? Qué aconsejan?

Saludos

---

### Post by Tobisc on 2010-05-09
Trato de ser mas específico: 3DSP Uwb y wifi-radar si están instalados, lo que sucede es que Uwb queda gris el icono y wifi-radar no encuentra la placa. ¿Será ésto que los drivers no están instalados correctamente?
 Tigus, voy a probar compilar e instalar todo con sudo, hasta ahora solo lo hice en make install.-

---

### Post by Mariano Oliveto on 2010-05-09
Perdonen muchachos si los hice ilusionar por un momento. A mí la compilación me da exactamente el mismo error que a del_Brujo. El tema es que no obstante ese error, luego de la compilación el uWB carga bien y el WiFi Radar ve la placa y permite conectarse sin problemas. El único drama es que hay que compilar los drivers cada vez que iniciás la máquina.

Como workaround lo que hice es armar un script para compilar los drivers y abrir el uWB secuencialmente, así, en vez de abrir el uWB desde el ícono del menú, armé un nuevo ícono que corre el script. Sería prácticamente lo mismo. Ahora les paso el código del script por si alguien lo quiere. Lo que habría que hacer es pegarlo en un nuevo archivo de texto (ej script_UWB) guardado en algún lugar donde se tiene permisos (ej /home/usuario) y marcarlo como ejecutable (botón derecho sobre el archivo, Propiedades, permitir que se ejecute el archivo). Luego arman un nuevo ícono en el menú y en el comando le ponen la ruta de acceso al script (ej /home/usuario/script_UWB). Le seleccionan un ícono lindo y le ponen un nombre.

El script es este:

```
#!/bin/bash
# Script para instalar los drivers de la placa interna USB wireless bluetooth 3DSP y el programa uWB

cd ~/Downloads/BlueW-2310U_2.0.0/driver_src/
gksudo make install
uwb
```

En la línea "cd ~/Downloads/BlueW-2310U_2.0.0/driver_src/" pongan la ruta de acceso a los drivers de la placa.

Si alguien tiene alguna idea de por qué aparece el error de compilación y puede echar una mano sería buenísimo



Les paso acá unas instrucciones que pasé por PM a un usuario que me consultó. Son las mismas instrucciones que se encuentran en un foro de Ubuntu en portugués (no sé el idioma, pero creo que decía algo por el estilo o se deducía fácilmente):

> Yo estoy usando el kernel 2.6.32-21 que es el que viene por defecto con el 10.04, y la placa que instalé es la wireless bluetooth USB interna (fijate que hay otras que son miniPCI).

Para compilarlos lo que hice fue lo siguiente:

1) Descargar el rar en alguna carpeta donde tengas acceso, ejemplo /home/usuario/Descargas/ (donde usuario es tu nombre de usuario)

2) Abrir una consola para tipear los comandos. Está en Aplicaciones &#8594; Accesorios &#8594; Terminal

3) Por las dudas recomiendan iniciar el servicio de bluetooth antes de compilar:

```
sudo /etc/init.d/bluetooth start
```

o

```
sudo service bluetooth start
```

4) Tendrías que tener instalado el gcc compiler y un par de librerías de development antes de compilar porque no vienen con la instalación predeterminada (vas a necesitar internet probablemente así que tendrías que tener acceso por cable):

```
sudo apt-get install build-essential libgnomeui-dev libnotify-dev
```

5) Ya tendrías todo listo para empezar con la compilación. Tenés que ir al directorio donde extrajiste los archivos y meterte en el subdirectorio donde están los drivers, en el ejemplo que te dí sería:
Code:

cd Descargas/BlueW-2310U_2.0.0/driver_src/

6) Luego ejecutás los siguientes comandos:

```
sudo make
mv new_bluetooth/ bluetooth/
mv private/new_bluetooth_priv/ private/bluetooth_priv/
sudo make install

```

El tema es que, a esta altura me tira un error al compilar que ayer no me di cuenta porque era tarde y tenía sueño. El error que me tira es el siguiente:

insmod: error inserting '/usr/local/3DSP/usb/3dspusbbt.ko': -1 Unknown symbol in module

Ahora, no obstante ese error cuando corro el UWB y el wifi radar anda todo 10 puntos (bah, el bluetooth aún no lo probé).

7) Faltarían compilar el 3DSP uWB, uWBtool y 3DSP WiFi Radar:


```
cd ..
cd applications/
cd uwb/
sudo make
sudo make install
cd ..
cd uwbtool/
sudo make
sudo make install
cd ..
cd 3dsp-wifi-radar/
sudo make
sudo make install
```

8 ) Listo, con esto lo último que faltaría es ir a Aplicaciones &#8594; Accesorios y abrir primero el "3DSP uWB" y luego el "3DSP WiFi Radar"

9) Cuando reinicies (si te pasa lo mismo que a mí) el 3DSP uWB, pero volviendo a instalar los drivers funciona:

```
cd Descargas/BlueW-2310U_2.0.0/driver_src/
sudo make install
```

Después repetís el paso 8 para abrir los programitas.


---

### Post by Tobisc on 2010-05-09
Hola gente! 
 Gracias Mariano por la ayuda. Lamentablemente a mi no me funciona esta solución. El icono de uWB sigue gris y triste.
 ¿Tendrá algo que ver los viejos drivers usados en karmic? (Raro ya que no es el mismo kernel).
 No se cómo seguir.... Alguna idea?

PD: Esta máquina es la de mi novia y si no le hago andar la wifi se pudre todo! Je...:rolleyes::rolleyes:

---

### Post by Mariano Oliveto on 2010-05-09
> **Tobisc said:**
> Hola gente! 
 Gracias Mariano por la ayuda. Lamentablemente a mi no me funciona esta solución. El icono de uWB sigue gris y triste.
 ¿Tendrá algo que ver los viejos drivers usados en karmic? (Raro ya que no es el mismo kernel).
 No se cómo seguir.... Alguna idea?

PD: Esta máquina es la de mi novia y si no le hago andar la wifi se pudre todo! Je...:rolleyes::rolleyes:

Hola Tobisc,

Antes que nada, la placa es la USB interna, ¿no? Porque en la miniPCI parece no andar esta solución (es coherente dado que los drivers son para la USB).

Yo probaría con el Ubuntu 10.04 Lucid Lynx. Particularmente yo estoy usando la Ubuntu Netbook Edition. Lo que podés hacer (es lo que hice yo para probar si funcaba antes de volar la 9.04), si tenés dos pendrives mejor (uno de 2 o más GB) es armar en uno el LiveUSB de UNE 10.04 asignándole algo de espacio para guardar archivos en el home y en el otro copiate la carpeta de las fuentes de los drivers. También necesitarías tener conexión a internet con cable de red. Cargás el 10.04 desde el pendrive y tendrías que seguir los pasos de compilación que dejé en la respuesta anterior. Vas a tener que bajar los paquetes para compilar (por eso necesitás la conexión por cable). Alternativamente si no tenés el segundo pendrive podés bajar los drivers en este momento. Luego probá a ver si con el 10.04 podés compilar y que funque al menos como me funca a mí.

Espero que sirva.

Al margen de todo, repito algunas preguntas:
[LIST=1]
[*]¿Alguien sabe de qué se trata el error de compilación y cómo solucionarlo?
[*]¿A quién podríamos escribir para pedir que incluyan estos drivers en las futuras ediciones para que las placas estén soportadas desde la instalación?
[/LIST]

Saludos!

Edit: 

Tobisc: Releyendo me di cuenta que ya tenés instalado el Lucid actualizado desde karmic. Igual yo probaría lo del LiveUSB por las dudas, quizás eso te resuelve el tema y es sólo reinstalar el OS sin tocar el home, no perdés más que tiempo.
Por otro lado, me fijé las instrucciones del link en portugués que mandaste. Ahí agregan unos pasos para resolver el error que nos está tirando, no sé si los probaste pero ahora me voy a poner a ver si me funcan.

---

### Post by guillermolisi on 2010-05-09
Si tienen dudas sobre si la placa WiFi es PCI o USB, abran una consola/terminal e ingresen ```
lspci
``` y luego ```
lsusb
``` En alguna de las dos salidas estara su placa Syntek 3DSP y podran intentar la instalacion del driver especifico y no tirar "a ciegas" :)

---

### Post by Tobisc on 2010-05-09
Bueno, ante todo muchas gracias por la ayuda.
 la verdad que estoy un poco perdido. ¿Puede ser que el mismo modelo de computadora venga con distinta placa, es decir usb o minipci? De todas formas la verdad que no se como interpretar lo que sale de los comandos lspci y lsusb. Los dejo a ver que me dicen.

```
noe@noe-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```





```
noe@noe-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 PCI bridge: Genesys Logic, Inc GL9701 PCIe to PCI Bridge
04:00.0 Ethernet controller: Device 1a47:0003
```

Voy a bajar una imagen de lucid UNR y probar lo que me propone mariano.-
Saludos.-

---

### Post by guillermolisi on 2010-05-09
Si, algunas vienen con WiFi USB y otras con miniPCI Syntek 3DSP.

En las salidas que obtuviste no aparece ninguna interface WiFi asi que te pediria si podes correr en consola/terminal ```
sudo lshw
```y pegas aqui su salida para terminar de ver como es el asunto.

Igual mi apuesta va por el lado USB.

---

### Post by Tobisc on 2010-05-09
Aquí va la salida guillermo. gracias por la ayuda.-

```
noe-laptop                
    description: Computer
    product: Calistoga & ICH7M Chipset
    vendor: Intel Corporation
    version: Not Applicable
    serial: Not Applicable
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: Intel Corporation
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: NAPA0001.86C.0059.D.0906011355 (06/01/09)
          size: 101KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 2048MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=1
        *-cache
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 2GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: M2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0300000-d037ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:d0400000-d043ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0380000-d03fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d0640000-d0643fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:d0100000-d01fffff ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:e0:4c:73:7e:3a
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:26 ioport:2000(size=256) memory:d0100000-d0100fff memory:d0000000-d000ffff(prefetchable) memory:d0020000-d003ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:d0200000-d02fffff memory:80000000-801fffff(prefetchable)
           *-pci
                description: PCI bridge
                product: GL9701 PCIe to PCI Bridge
                vendor: Genesys Logic, Inc
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm bus_master cap_list
                resources: memory:d0200000-d02fffff
              *-network UNCLAIMED
                   description: Ethernet controller
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: latency=120 maxlatency=8 mingnt=15
                   resources: memory:d0200000-d0207fff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0644000-d06443ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18d0(size=8) ioport:18c4(size=4) ioport:18c8(size=8) ioport:18c0(size=4) ioport:18b0(size=16) memory:d0644400-d06447ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXF0A69R6379
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a15b0695
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/sda1
                   version: 3.1
                   serial: 76f4a938-0a8f-d44f-ada7-7b56e7fd6319
                   size: 113GiB
                   capacity: 113GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-06 14:06:52 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 60GiB
                   capacity: 60GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 57GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2572MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/sda3
                   version: 1.0
                   serial: f88db08e-e5eb-4fd9-9d09-c1d760dce5c6
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary journaled large_files recover ext3 ext2 initialized
                   configuration: created=2010-04-07 06:55:10 filesystem=ext3 label=Datos modified=2010-05-09 23:29:28 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2010-05-09 23:29:28 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
```


Recuero que en Karmic, la placa funciono con el driver provativo puesto en este mismo hilo, por lo que supongo que la placa es pci..

---

### Post by guillermolisi on 2010-05-10
Veo que en PCI:0 tenes la placa de red cableada, Realtek.

En PCI:1 hay otra placa, Genesys PCIe to PCI, Ethernet de la cual no se visualizan sus caracteristicas funcionales, solo qie es pm bus_master y que no tiene asociado ningun driver. Posiblemente sea esa la placa WiFi en cuestion confirmando lo que vos decis (que es PCI y no USB).

---

### Post by Tobisc on 2010-05-10
El driver liberado no sirve para la placa pci? Una lástima. Habrá que esperar un poco mas. Y me veo reinstalando karmic...
 Gracias por la ayuda de todas formas.

---

### Post by tigus on 2010-05-10
Buenas a todos!
La verdad que una lástima que no te funcione Tobisc, estaría bueno que lo incluyan ya en la distro original...
Por otro lado les cuento que para la placa USB pude compilar el driver y estoy posteando desde la netbook. El módulo que no compila al parecer es de bluetooh, no lo he probado y no tengo idea a qué se debe el error.
Por otro lado, no me está haciendo falta compilar el driver cada vez que reinicio la netbook... dejé que se levante siempre en el arranque el script /etc/init.d/tdspusbcardinit que se encarga de instalar los módulos y crear el dispositivo.
Luego agregué en "Sistemas / Aplicaciones al inicio" dos comandos, uno es sudo /usr/bin/uwb y el otro es /usr/sbin/3dsp-wifi-radar, de manera que levanta todo al inicio, sólo resta una vez iniciado ubuntu darle al wifi radar y conectar. 

Espero les ayude en algo, saludos a todos.

---

### Post by Apipote on 2010-05-10
O cambias la placa como me hicieron a mí en el service, ya que ellos mismos me dijeron que esa placa es una porquería.
De hecho se me colgó todas las vacaciones y no la pude usar...un desastre.
Me pusieron una realtek (porque no conseguían la dsp) y se terminaron los dramas. Me llamaron cuando llegó la placa original y les dije que ni borracho.
Perdí el bluetooth, peró gané en alcance, compatibilidad plena...y en salud.

Sdls.

---

### Post by guillermolisi on 2010-05-10
> **Apipote said:**
> O cambias la placa como me hicieron a mí en el service, ya que ellos mismos me dijeron que esa placa es una porquería.
De hecho se me colgó todas las vacaciones y no la pude usar...un desastre.
Me pusieron una realtek (porque no conseguían la dsp) y se terminaron los dramas. Me llamaron cuando llegó la placa original y les dije que ni borracho.
Perdí el bluetooth, peró gané en alcance, compatibilidad plena...y en salud.

Sdls.
Modelo de la Realtek ? Gracias !

---

### Post by Apipote on 2010-05-11
rtl8187b

Ojalá les sirva como a mí.
Slds.

---

### Post by Blackleker on 2011-04-20
Hola bueno ya he tenido mi experiencia con estos drivers el principal problemas es al actualizar el kernel o tener una versión del kernel muy reciente los módulos no son compatibles con versiones muy recientes asi que al no cargar los modulos no se va a poder levantar la interfaz con el programa uwb (este queda en gris).

Yo recomiendo usar unos de los kernels con que me funcionaron los drivers la info esta aca: [http://bydemon007.blogspot.com/2011/04/archlinux-conectarse-por-wifi-con-una.html](http://bydemon007.blogspot.com/2011/04/archlinux-conectarse-por-wifi-con-una.html) y aca [http://bydemon007.blogspot.com/2010/10/ubuntu-ml-6200-3dsp-conexion-autamatica.html](http://bydemon007.blogspot.com/2010/10/ubuntu-ml-6200-3dsp-conexion-autamatica.html) .

Una forma de verificar si los módulos se están cargando o cargarlos a mano es correr el scritp con este comando:
```
sudo /etc/init.d/tdspusbcardinit start
```para levantar la interfaz si el uwb lo podemos hacer con el comando:

```
uwbtool --download=combo
```

Sobre la placa es usb o pci bueno la placa es mini pci express pero esta ranura mini-pci-e posee un puerto usb asi que la placa lo utiliza incluso hay mods para sacarle un puerto usb adicional a las portatiles por este puerto. Hora sobre los drivers pci esos creo que son drivers para las computadoras de escritorio con ranura pci.

Este es el identificador:
```

Bus 001 Device 005: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter
```Espero que eso le resuelva el problema Saludos

---

