---
title: "[SOLUCIONADO] Requerimientos mínimos de hardware para Jaunty"
date: 2009-06-14
forum: Hardware
---

### Post by Psycopatologic on 2009-06-14
En estos momentos estoy usando ubuntu 8.04 Hardy Heron 64 bits y mi pc es un Athlon64 3000+ 2.0Ghz socket 754, 1.5 Gb DDR PC3200, Nvidia GeForce 5200 256Mb DDR, un disco duro de 80Gb y a veces tengo problemas de rendimiento, cosa que no sucedia en 7.10, quizas por cambios en el kernel o quien sabe por que. La pregunta es, ¿Sera viable instalar ubuntu 9.04?, estoy verde por probar que tal es pero a la vez entiendo que el software de ubuntu evoluciona a la par con los nuevos hardwares pero en la documentacion original de ubuntu 9.04 dice que se requiere un pc de menos de 800Mhz para correr esa distro de ubuntu. En estos momentos estoy usando rythmbox en vez de amarok por que pesan mucho sus funciones, al agregar musica a la playlist desde una particion NTFS, Ntfs-3g ocupaba un 80% de Cpu al revisar el comando top, evaluo cambiar firefox por epiphany y no tengo instalado compiz para no cargar mas el sistema. En definitiva, solo lo estrictamente necesario como Open Office, Kpdf y otros softwares como origin y eso.

Eso, espero que puedan ayudarme, de antemano muchas gracias.:razz:

---

### Post by Carlos C on 2009-06-14
Edité el título del thread porque "Duda existencial" no dice mucho y no facilita que la información sea encontrada fácilmente, te insisto, debes leer acá:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Para no ser tan antipático te respondo la pregunta: sí, puedes instalar Ubuntu Jaunty en ese equipo y debiera correr sin problemas. Ubuntu puede ser más pesado que otras distros y efectivamente ha subido sus requerimientos, pero estos requerimientos tampoco son tan altos como para que Jaunty no corra bien en tu computador. De echo, a mí me corre mejor Jaunty que Intrepid.

Saludos y por favor recuerda lo que te digo, es para que puedas participar del foro sin problemas.

---

### Post by Psycopatologic on 2009-06-14
Jajaja perdon. Y bueno, es lo que pensaba pero a veces me da algunos problemas la 8.04 y de la 8.10 ni hablar. Se me colgaba el sistema a cada rato. Hoy vi un post donde salia que habia que quitar un modulo de power management para la CPU que causaba cuelgues de sistema, lo hice y me ha corrido bastante bien Hardy de 64 bits, en realidad como nunca. 

No habra problemas con las actualizaciones del software para Jaunty? por que se me imagina que debe comer mas recursos que los programas por defecto para hardy.

Muchas gracias por la respuesta. =D

PD: Las instalaciones siempre las hago limpias en una particion formateada y con los discos originales que me llegan por correo.

Saludos =)

---

### Post by Carlos C on 2009-06-14
Desde mi experiencia personal no, Jaunty anda bastante bien, no lo he notado más pesado para nada. Ahora, no he realizado ningún test de rendimiento, sólo hablo desde mi sensación subjetiva. Lo uso todos los días y lo noto más liviano que intrepid y me parece lejos la versión más agradable de usar.

---

### Post by Psycopatologic on 2009-06-14
Entonces siendo asi no deberia tener problemas y en cuanto me llegue el disco de jaunty me cambio. 

Se agradece =)

---

### Post by Jonathan Dud Rodriguez on 2009-06-15
consejo... quedate con hardy
:)

pero bajate la version para 64 bits...
por algo la crearon no???




saludos

---

### Post by Psycopatologic on 2009-06-15
> En estos momentos estoy usando ubuntu 8.04 Hardy Heron 64 bits

Instale Jaunty pero tengo un 100% de uso de procesador cuando uso alguna aplicacion...

volvere a Hardy =(

---

### Post by Carlos C on 2009-06-15
> **Jonathan Dud Rodriguez said:**
> consejo... quedate con hardy
:)
pero bajate la version para 64 bits...
por algo la crearon no???
saludos
La verdad a mí Jaunty me corre bastante bien y conozco mucha gente contenta usando esa versión. Si vas a dar ese consejo, ¿no sería buena idea justificar lo que dices para que la persona que pregunta te entienda? Porque yo usé Hardy en su momento y no me quedan clara tus razones.

[quote=Psycopatologic]Instale Jaunty pero tengo un 100% de uso de procesador cuando uso alguna aplicacion...

volvere a Hardy =(      [/quote]
¿Qué aplicación corres?
Por favor escribe en el terminal "top" y verifica cuál es el proceso que mantiene el procesador ocupado.

---

### Post by moreback on 2009-06-16
> **Psycopatologic said:**
> Instale Jaunty pero tengo un 100% de uso de procesador cuando uso alguna aplicacion...

volvere a Hardy =(

Eso del 100% de seguro es por el driver privativo que estás usando de la tarjeta Nvidia, de seguro top te va a indicar que el que ocupa la mayoría es el servidor X. El otro que ocupa harta cpu es el indexador Tracker, los efectos del compiz también.

De todas maneras creo que estás exagerando con lo del uso del procesador, las aplicaciones están hechas para usar el procesador.

Saludos.

---

### Post by Psycopatologic on 2009-06-16
La verdad no exagero, esta bien que las aplicaciones pero teniendo el rythmbox funcionando y nada mas el uso de cpu es 90% por lo bajo. No uso drivers privativos, uso el driver libre de nvidia que viene con ubuntu, no uso compiz y no tenia los efectos de escritorio activados, el servidor de las X me ocupa un 2% de CPU. Con rythmbox y firefox juntos el uso es 100%, no se pone lento el pc ni nada pero las estadisticas lo muestran je. Al utilizar el comando top el proceso que ocupa mas cpu es rythmbox.xxx (no recuerdo que decia en las xxx) pero por lo bajo ocupaba 79% de cpu.   Eso, me quedare por ahora con Hardy que bastante bien me funciona ya que no puedo arriesgar a mi pc a cuelgues ni nada por el estilo por que esto terminando los informes finales del semestre.  Si alguna idea adicional surge se agradece. Muchas gracias por las respuestas.

---

### Post by Carlos C on 2009-06-16
Debes encontrar qué proceso(s) ocupa(n) a ese nivel la cpu. Si dices que al usar rythmbox la cpu se mantiene trabajando a un 79% entonces mi pregunta lógica es si acaso rythmbox es quien ocupa tanto la cpu o es otro proceso asociado. Debes ser específico para poder darte un sugerencia responsable. Esto no es un comportamiento normal en Jaunty ni tiene que ver con los requerimientos mínimos, se trata de un problema puntual que necesita ser solucionado.

Saludos.

---

### Post by moreback on 2009-06-16
A veces los efectos visuales y animaciones que hacen algunas aplicaciones usan bastante CPU. Creo que va por ahí

---

### Post by radixs on 2009-06-16
Creo que deberias usar el comando "top" y pegar lo que muestra aqui, de esa forma te podiramos ayudar, dices que te ocupa 100% del cpu cuando ocupas Rythmbox + firefox..

Consulta: Cuando estas con firefox no tendras corriendo Flash player???

---

### Post by Psycopatologic on 2009-06-16
> **radixs said:**
> Creo que deberias usar el comando &quot;top&quot; y pegar lo que muestra aqui, de esa forma te podiramos ayudar, dices que te ocupa 100% del cpu cuando ocupas Rythmbox + firefox..

Consulta: Cuando estas con firefox no tendras corriendo Flash player???

 No, lo de rythmbox no se lo que pueda ser, baje a Hardy ya a si que no sirve mucho que ponga el reporte del comando Top. Cuando corro firefox trato de no usar muchas paginas en flash, con suerte youtube una vez a la semana. En rythmbox desactive todos los plugins y creo que lo que me ocupaba cpu era el asistente de biblioteca multimedia, es la unica funcionalidad de rythmbox que deje habilitada a parte de las funciones basicas de reproduccion. Cuando este mas libre vuelvo a Jaunty (para ese entonces me habran llegado los Cd's por correo) y vemos que pasa por que por lo que recuerdo las X subian a un 20% de uso con drivers libres (el 1xx.x) pero lo que mas me confunde es que no se colgo ubuntu en ningun momento.   Si quieren podemos dejar el tema en stand by, quizas sea un bug no reportado y veamos que se puede hacer.  Muchas gracias por sus respuestas =).  PD: alguna idea con lo del teclado de mi otro post? =$  EDIT: para que se vayan haciendo una idea, en Hardy este es mi rendimiento con rythmbox, firefox y aMSM abiertos. 

[html]vishnu@vishnu-desktop:~$ top

top - 23:09:13 up  2:41,  2 users,  load average: 0.26, 0.29, 0.16
Tasks: 111 total,   4 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.6%us,  3.7%sy,  0.0%ni, 83.7%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   1546080k total,  1530812k used,    15268k free,   295732k buffers
Swap:  6458088k total,        0k used,  6458088k free,   687600k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5267 root      20   0  175m  62m 9816 R  2.7  4.1   4:30.94 Xorg               
 5836 vishnu    20   0  189m 9816 7888 R  2.0  0.6   0:03.62 multiload-apple    
31126 vishnu    20   0  525m  49m  18m S  2.0  3.3   0:20.44 rhythmbox          
 5785 vishnu    20   0  262m  31m 9464 S  1.3  2.1   2:19.57 compiz.real        
 8337 vishnu    20   0  251m  23m  11m S  1.3  1.5   0:00.62 gnome-terminal     
 5693 vishnu    20   0  155m 7204 3776 R  1.0  0.5   0:49.18 pulseaudio         
 2263 root      15  -5     0    0    0 S  0.7  0.0   0:01.04 scsi_eh_2          
 5530 vishnu    20   0 41436 5656 2032 S  0.7  0.4   0:01.80 gconfd-2           
 8369 vishnu    20   0 18860 1260  932 R  0.7  0.1   0:00.06 top                
23448 vishnu    20   0  145m  14m 7768 S  0.7  1.0   0:01.54 notification-da    
    1 root      20   0  4020  876  592 S  0.0  0.1   0:00.76 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper [/html]

---

### Post by Psycopatologic on 2009-06-17
Chicos, descubri la misma anomalia en hardy...el proceso es rythmbox-metad y se activa cuando inicio rythmbox lo que me da un uso del 100% de CPU por menos de un minuto (lo que en Jaunty era constante).

[html]vishnu@vishnu-desktop:~$ top

top - 01:54:27 up  5:27,  2 users,  load average: 1.19, 1.64, 1.22
Tasks: 118 total,   3 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 76.2%us, 22.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.5%hi,  1.1%si,  0.0%st
Mem:   1546080k total,  1350876k used,   195204k free,   216596k buffers
Swap:  6458088k total,    24996k used,  6433092k free,   673104k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 1029 vishnu    20   0  262m  13m 7928 R 80.1  0.9   0:22.36 rhythmbox-metad                                                                                                     
32678 root      20   0  150m  42m 9312 R  7.6  2.8   0:12.88 Xorg                                                                                                                
  704 vishnu    20   0  261m  25m  12m S  3.2  1.7   0:01.72 gnome-terminal                                                                                                      
  985 vishnu    20   0  525m  49m  18m S  3.2  3.3   0:04.87 rhythmbox                                                                                                           
  399 vishnu    20   0  154m 6572 3732 S  1.4  0.4   0:01.63 pulseaudio                                                                                                          
  412 vishnu    20   0  130m 3072 1816 S  1.1  0.2   0:00.48 gnome-screensav                                                                                                     
  394 vishnu    20   0 21452 1192  736 S  0.5  0.1   0:00.34 dbus-daemon                                                                                                         
  419 vishnu    20   0  293m  25m  14m S  0.5  1.7   0:02.04 gnome-panel                                                                                                         
  483 vishnu    20   0  257m  30m 9416 S  0.5  2.0   0:06.62 compiz.real                                                                                                         
  737 vishnu    20   0 18992 1276  932 R  0.5  0.1   0:00.26 top                                                                                                                 
 1481 root      15  -5     0    0    0 S  0.5  0.0   0:01.20 ata/0                                                                                                               
    1 root      20   0  4020  876  592 S  0.0  0.1   0:00.76 init                                                                                                                
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                         
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 events/0                                                                                                            
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                             
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0                                                                                                           
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                              
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                                        
  124 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                                             
  168 root      20   0     0    0    0 S  0.0  0.0   0:00.40 pdflush                                                                                                             
  169 root      20   0     0    0    0 S  0.0  0.0   0:00.08 pdflush                                                                                                             
  170 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 kswapd0                                                                                                             
  213 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                                               
  386 vishnu    20   0  209m 7916 5024 S  0.0  0.5   0:00.06 seahorse-agent                                                                                                      
  395 vishnu    20   0  250m  11m 8820 S  0.0  0.8   0:00.37 gnome-settings-                                                                                                     
  403 vishnu    20   0 55680 2624 2092 S  0.0  0.2   0:00.00 gconf-helper                                                                                                        
  417 vishnu    20   0  3944  620  480 S  0.0  0.0   0:00.00 compiz                                                                                                              
  420 vishnu    20   0  352m  30m  14m S  0.0  2.0   0:00.70 nautilus                                                                                                            
  427 vishnu    20   0 82072 3604 2620 S  0.0  0.2   0:00.07 bonobo-activati                                                                                                     
  429 vishnu    20   0 44772 2280 1900 S  0.0  0.1   0:00.02 gvfsd                                                                                                               
  484 vishnu    20   0  118m 6568 5308 S  0.0  0.4   0:00.08 bluetooth-apple                                                                                                     
  487 vishnu    20   0  202m  15m 9964 S  0.0  1.0   0:00.18 update-notifier                                                                                                     
  492 vishnu    20   0  116m 6308 5112 S  0.0  0.4   0:00.06 tracker-applet                                                                                                      
  496 vishnu    39  19 74556  10m 2284 S  0.0  0.7   0:00.04 trackerd                                                                                                            
  500 vishnu    20   0  210m  23m  10m S  0.0  1.6   0:00.40 python                                                                                                              
  501 vishnu    20   0  192m  13m 8580 S  0.0  0.9   0:00.26 nm-applet                                                                                                           

[/html]

Algun dato sobre ese proceso? no logro encontrar documentacion en internet sobre eso.

Saludos

---

### Post by nopersona on 2009-06-17
Creo que el error se debe a la versión 64 bits. En todos los links de bugs que encontré sobre rythmbox-metad, se hace alusión a paquetes x86_64, hasta en versiones para redhat. En la de launchpad nombran el error asociado a la reprodución de mp3 y el quiebre de  gstreamer. Por ahí podría ir. Abre rythmbox por terminal y al mismo tiempo una pestaña abierta con top.  Ejecuta las operaciones de costumbre en rythmbox, y si la cpu sube mucho, verifica la salida del terminal de top y de rythmbox. 

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/225252](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/225252)

[https://bugzilla.redhat.com/show_bug.cgi?id=465343](https://bugzilla.redhat.com/show_bug.cgi?id=465343)

Por lo pronto, y para aportar algo más al tema, te recomiendo que uses Banshee en vez de rythmbox, es mucho más estable, nunca (me) ha superado el consumo de cpu más allá de 70% (los 2-3 segundos que demora en abrir) y luego se mantiene en un comodo 3% o 6% También te recomiendo pidgin, el uso de recursos que hace amsn, para la función que cumple, es casi ridículo. Además, ya está implementada la función video conferencia, sólo falta que la liberan este mes o el que viene :p

[http://planet.pidgin.im](http://planet.pidgin.im)

Saludos!

---

### Post by Psycopatologic on 2009-06-17
Con respecto a banshee fue una belleza y un acierto, la verdad no lo conocia y es identico a rythmbox pero mas funcional. aMSN la verdad no me molesta, nunca da problemas.

Amigo nopersona, tu que arquitectura usas para jaunty? 32 o 64?

---

### Post by Carlos C on 2009-06-17
Perdón, pero, ¿podemos dar el problema por solucionado? Lo pregunto antes de que el thread se desvíe a otra cosa.
Saludos.

---

### Post by Psycopatologic on 2009-06-17
si que si señor...muchas gracias

---

### Post by nopersona on 2009-06-18
> **Psycopatologic said:**
> Con respecto a banshee fue una belleza y un acierto, la verdad no lo conocia y es identico a rythmbox pero mas funcional. aMSN la verdad no me molesta, nunca da problemas.

Amigo nopersona, tu que arquitectura usas para jaunty? 32 o 64?

YO también tengo 64 bits, athlon 64 3200+ 2 ghz, y siempre he usado 32 bits. Una vez intenté, allá por la 6.06, pero no me funcionó muy bien. Voy a ver si en karmic hago el cambio, parece que ya muy pocas cosas están no soportadas en 64 bits.

Saludos.

---

