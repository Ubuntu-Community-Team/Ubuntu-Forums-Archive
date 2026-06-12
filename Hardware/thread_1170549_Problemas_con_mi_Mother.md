---
title: "Problemas con mi Mother"
date: 2009-05-26
forum: Hardware
---

### Post by Daro4887 on 2009-05-26
Hola gente, soy totalmente nuevo en Linux y tengo un problema con mi placa mother (un ASRock P4i45GV)... El puerto de video es AGI (ni AGP ni PCI... AGI) y cuando activo la placa de video desde el bios no me inicia Ubuntu (ni siquiera en recovery mode). Primero pensaba que era la placa de video (una Ati Radeon 9250) pero probe con una GForce de un amigo y tengo el mismo problema. El problema es que ya no se que hacer, tengo instalado linux pero no le puedo poner los efectos pq la placa de video que tengo activada es la onboard. Estoy desesperado!!
La solucion obvia de cambiar el mother la tengo que dejar para un tiempo mas adelante ya que no tengo la guita ahora para renovar la pc, asique si tienen alguna idea es bienvenida!
Gracias.

---

### Post by anarko on 2009-05-26
> **Daro4887 said:**
> Hola gente, soy totalmente nuevo en Linux y tengo un problema con mi placa mother (un ASRock P4i45GV)... El puerto de video es AGI (ni AGP ni PCI... AGI) y cuando activo la placa de video desde el bios no me inicia Ubuntu (ni siquiera en recovery mode). Primero pensaba que era la placa de video (una Ati Radeon 9250) pero probe con una GForce de un amigo y tengo el mismo problema. El problema es que ya no se que hacer, tengo instalado linux pero no le puedo poner los efectos pq la placa de video que tengo activada es la onboard. Estoy desesperado!!
La solucion obvia de cambiar el mother la tengo que dejar para un tiempo mas adelante ya que no tengo la guita ahora para renovar la pc, asique si tienen alguna idea es bienvenida!
Gracias.

Haber si entendi: tenes 2 placas de video ( ademas de la que te presto tu amigo ), cuando le decis que arranque de la placa onboard del asrcok te anda todo bien ( salvo los efectos especiales ), pero cuando le decis al bios que use la placa AGP, ahi en el slot AGP tenes puesta una ati9250 cuando prendes la pc se ve todo, el bios todo, pero cuando llega la hora de que arranque el modo grafico en linux te dice que no puede arrancar por algun motivo, osea : ¿te pone un cartelito en la pantalla, o se cuelga la pc? 

Caso A) Cartelito : hace lo siguiente, arranca con la 9200 hasta el error luego reinicia con la placa onboard y postea lo que esta en el archivo : /var/log/xorg.log.old 

Caso B) Se cuelga : no sabria que decirte, mas que pruebes con otra fuente, o cambies las opciones del AGp en el bios para ver si alguna le gusta mas.

PD: Yo tengo una placa de video de 130U$ y tampoco puedo activar los efectos especiales, no es la muerte de nadie se puede usar linux sin compiz.

---

### Post by Daro4887 on 2009-05-26
El problema es el "Caso B" se ve todo joya hasta que hay q cargar linux, ya sea modo grafico o modo "recovery" (el modo terminal, lo que seria DOS en windows) que es donde se muere la pc. Gracias.

---

### Post by guillermolisi on 2009-05-26
> **Daro4887 said:**
> Hola gente, soy totalmente nuevo en Linux y tengo un problema con mi placa mother (un ASRock P4i45GV)... El puerto de video es AGI (ni AGP ni PCI... AGI) y cuando activo la placa de video desde el bios no me inicia Ubuntu (ni siquiera en recovery mode). Primero pensaba que era la placa de video (una Ati Radeon 9250) pero probe con una GForce de un amigo y tengo el mismo problema. El problema es que ya no se que hacer, tengo instalado linux pero no le puedo poner los efectos pq la placa de video que tengo activada es la onboard. Estoy desesperado!!
La solucion obvia de cambiar el mother la tengo que dejar para un tiempo mas adelante ya que no tengo la guita ahora para renovar la pc, asique si tienen alguna idea es bienvenida!
Gracias.
La placa de video integrada es Intel Extreme Graphics. Eso significa que usa tecnologia de video XA de Intel ?

Cito resumen tecnico de la placa:> 

[LIST]
[*]Socket 478 for Intel® P4 processor
[*]Intel® 845GV chipset
[/LIST]
 								
[LIST]
[*]Worldwide Patent - ASRock A.G.I. 8X A gift for VGA upgrade on i845GV
[*]FSB 533/400MHz, DDR 333/266
[*]Supports Hyper-Threading Technology
[*]Integrated Intel® Extreme Graphics
[*]ASROCK I/O - default 4 ready-to-use USB2.0 ports on rear panel, default Game/MIDI port.
[*]5.1 Channel audio.
[*]default 10/100 Ethernet PCI LAN.
[*]Multi-languages Quick Installation Guide.
[*]Bundle CD includes Anti Virus Software, ASRock PC DIY Live Demo, Audio Player, etc..
[/LIST]


---

### Post by staar on 2009-05-26
jojo, las cosas que inventa AsRock, al parecer, el puerto AGI es un híbrido entre los antiguos AGP y los actuales PCI-E, osea que en teoría soporta placas diseñadas para ambos puertos XD :P, dicho en cordobé, una harriada total, propio de una compañía sin el menor respeto por los estándares...

como te imaginarás, esto solo funciona en win$, en nuestro SO, solo da problemas...

pero parece que ya funciona, aunque requiere ciertos hacks, en este blog [0] está bien explicado como es el tema, y como solucionarlo, al menos con intrepid (supongo que valdrá para jaunty), eso si está en idioma Imperial :-D, si no lo entendés, chiflá que traducimos...

saludos

[0] [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")

---

### Post by Daro4887 on 2009-05-27
gracias staar!! funcionó de maravilla!! ahora lo unico que me falta hacer es instalar los drivers de la placa (que por algun motivo no me deja, pero le voy a preguntar a un amigo q sabe) y listo!!

---

### Post by hernan blau on 2009-05-27
Por el título ¿no será un problema como el de Edipo?:D:D

---

### Post by Hei Ku on 2009-05-27
> **hernan blau said:**
> Por el título ¿no será un problema como el de Edipo?:D:D

Off-topic. Por favor, posteá solo si tenes algo que aportar.

---

### Post by hernan blau on 2009-05-28
Ruego disculpas entonces. El problema del compañero ya estaba solucionado y mi comentario sólo fue una inocente broma, que no se repetirá. Cordialmente, HB

---

### Post by juanma10 on 2009-10-27
> **staar said:**
> otra vez una el dichoso puerto AGI? en estos threads se trata este tema, que tiene solución: [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi")

saludos
hola staar!!
 
te queria consultar algo.
el ubuntu ya lo tengo instalado.
pero me faltaria hacer lo de la placa de video.
con estos dos links lo podria solucionar:
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.p...&highlight=agi")
 
slau2

---

### Post by juanma10 on 2009-10-27
> **staar said:**
> otra vez una el dichoso puerto AGI? en estos threads se trata este tema, que tiene solución: [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi](http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi)
[http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi](http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi)
 
saludos
 
con estos links deberia funcionar??
 
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.p...&highlight=agi")
 
salu2

---

### Post by guillermolisi on 2009-10-27
> **juanma10 said:**
> con estos links deberia funcionar??
 
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...&highlight=agi[/COLOR]]("http://ubuntuforums.org/showthread.p...&highlight=agi")
 
salu2
Con lo que se comenta en el primero, particularmente la referencia que hace Starr a [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/) deberias poder utilizar tu placa de video nVidia.

---

### Post by juanma10 on 2009-10-27
> **guillermolisi said:**
> Con lo que se comenta en el primero, particularmente la referencia que hace Starr a [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/) deberias poder utilizar tu placa de video nVidia.
hola guillermo.
te cuento que ubuntu ahora anda bien pero no me deja instalar los drivers de la placa nvidia.
intente hacer algunos pasos que encontre por el foro pero no hay caso.
se podra hacer algo mas??

salu2

---

### Post by juanma10 on 2009-10-27
> **staar said:**
> otra vez una el dichoso puerto AGI? en estos threads se trata este tema, que tiene solución: [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi")

saludos
hola staar:

te cuento que ahora ubuntu anda bien pero no me deja instalr los drivers de la nvidia.
intente hacer algunos pasos que encontre por el foro pero no hay caso.}
podre hacer algo mas??

salu2

---

### Post by staar on 2009-10-28
como intentaste? tenés que ir a Sistema > Administración > Controladores de hardware y darle a instalar (la barra de progreso puede que no funcione, pero lo mismo instala, solo hay que esperar), sino, buscando en Synaptic el paquete *nvidia-glx-173* (la versión de los drivers para estas placas) e instalándolo...

para que funcionen primero tenés que cerrar sesión y volver a entrar, para reiniciar el servidor gráfico...

si después de eso, te sigue diciendo en Controladores de hardware que están desactivados, probá corriendo, en una Terminal, el comando ```
sudo nvidia-xconfig
```

saludos

---

### Post by juanma10 on 2009-10-28
> **staar said:**
> como intentaste? tenés que ir a Sistema > Administración > Controladores de hardware y darle a instalar (la barra de progreso puede que no funcione, pero lo mismo instala, solo hay que esperar), sino, buscando en Synaptic el paquete *nvidia-glx-173* (la versión de los drivers para estas placas) e instalándolo...

para que funcionen primero tenés que cerrar sesión y volver a entrar, para reiniciar el servidor gráfico...

si después de eso, te sigue diciendo en Controladores de hardware que están desactivados, probá corriendo, en una Terminal, el comando ```
sudo nvidia-xconfig
```

saludos
le cuento que no me funciono.
hize los pasos y despues ni siquiera me dejo abrir el ubuntu, se queda negra la pantalla y no arranca.
depues saque el monitor de la placa de video, lo puse al omboar del mother, y me deja acceder a ubuntu con la opcion de low graphips o algo asi.
pero cuando voy a controladores de hardware me dice que esta activo pero que no se esta usando.
asi que despues.....nose.

---

### Post by staar on 2009-10-28
tenés que desactivar en la BIOS la placa intel, que arranque con la nvidia...

saludos

---

### Post by juanma10 on 2009-10-28
> **staar said:**
> tenés que desactivar en la BIOS la placa intel, que arranque con la nvidia...
 
saludos
 
 
hola si eso fue lo que hize al principio.
pero de esa manera no me dejo  iniciar mas el ubuntu
 
tuve que dejar activa la intel y de esa manera me dejo iniciar ubuntu.
nose que mas hacer
tendre que usarla sin los drivers

---

### Post by guillermolisi on 2009-10-28
> **juanma10 said:**
> hola si eso fue lo que hize al principio.
pero de esa manera no me dejo  iniciar mas el ubuntu
 
tuve que dejar activa la intel y de esa manera me dejo iniciar ubuntu.
nose que mas hacer
tendre que usarla sin los drivers
Sin el driver de la Intel blacklisted la nVidia nunca funcionara.

---

### Post by juanma10 on 2009-10-28
> **guillermolisi said:**
> Sin el driver de la Intel blacklisted la nVidia nunca funcionara.
 
vos decis que este en la blacklist? laintel
 
eso lo habia echo antes

---

### Post by juanma10 on 2009-11-05
> **guillermolisi said:**
> Con lo que se comenta en el primero, particularmente la referencia que hace Starr a [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/) deberias poder utilizar tu placa de video nVidia.

> **juanma10 said:**
> vos decis que este en la blacklist? laintel
 
eso lo habia echo antes

hola para instalar los drivers de la placa de video, tendre que descargar los drivers de la pagina de nvidia para linux?

---

### Post by juanma10 on 2009-11-05
> **guillermolisi said:**
> Sin el driver de la Intel blacklisted la nVidia nunca funcionara.

hola guillermo:

una opcion puede ser bajar los drivers de nvidia para linux??

---

