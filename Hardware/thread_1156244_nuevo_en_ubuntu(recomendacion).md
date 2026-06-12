---
title: "nuevo en ubuntu(recomendacion)"
date: 2009-05-11
forum: Hardware
---

### Post by kenet on 2009-05-11
buenas, soy nuevo en esto de ubuntu. tengo instalado windows xp en mi mitad del disco y en la otra mitad le acavo de poner ubuntu.

despues de andar toqueteando algo no salio bien y lo quiero instalar de nuevo, pero lo quiero hacer bien.

estas son las caracteristicas de mi pc.





Tipo de ordenador                                 Equipo multiprocesador ACPI
Sistema operativo                                 Microsoft Windows XP Professional
Service Pack del Sistema Operativo                Service Pack 3

Placa base:
Tipo de procesador                                DualCore AMD Athlon 64 X2, 2300 MHz (11.5 x 200) 4400+
Nombre de la Placa Base                           Acer F690GVM
Chipset de la Placa Base                          AMD 690G, AMD Hammer
Memoria del Sistema                               3328 MB  (DDR2-667 DDR2 SDRAM)
     

Monitor:
Tarjeta gráfica                                   ATI Radeon HD 3400 Series  (256 MB)
Tarjeta gráfica                                   ATI Radeon HD 3400 Series  (256 MB)
Acelerador 3D                                     ATI Radeon HD 3450 (RV620)
Monitor                                           Acer AL1751W  [17" LCD]  (ETL1902007)


Multimedia:
Tarjeta de sonido                                 ATI Radeon HDMI @ ATI RV620 - High Definition Audio Controller
Tarjeta de sonido                                 Realtek ALC888/1200 @ ATI SB600 - High Definition Audio Controller


Almacenamiento:
Controlador IDE                                   Controladora estándar PCI IDE de doble canal
Controlador IDE                                   Controladora estándar PCI IDE de doble canal
Estado de los discos duros SMART                  OK

mi pregunta es:

cual de estos 2 le tengo que poner

Ubuntu Desktop 9.04 i386
Ubuntu Desktop 9.04 amd64

tengo puesto windows xp profesional sp3 32bit

le puedeo poner el Ubuntu Desktop 9.04 amd64 teniendo el xp de 32bit? o seria mejor meter un xp de 64bit y luego el Ubuntu Desktop 9.04 amd64

lo que quiero hacer es dejar la mitad del disco para windows xp y la otra mitad para ubuntu.

acepto cualquier recomendacion de expertos para que mi ordenador ande bien y con el sistema que le pertenece.

muchas gracias

---

### Post by pablo.s on 2009-05-11
> **kenet said:**
> mi pregunta es:

cual de estos 2 le tengo que poner

Ubuntu Desktop 9.04 i386
Ubuntu Desktop 9.04 amd64

Ubuntu 9.04 i386. Si no tenés experiencia
no te recomiendo instalar la versión de 64 bits.

> **kenet said:**
> le puedeo poner el Ubuntu Desktop 9.04 amd64 teniendo el xp de 32bit? o seria mejor meter un xp de 64bit y luego el Ubuntu Desktop 9.04 amd64 

Sin palabras.

---

### Post by kenet on 2009-05-11
soy novato y me esta pareciendo super dificil ubuntu.jejeje

ok, entonces no le pondre el amd64

si quieria instalar solo el ubuntu, pero la mitad de los que uso no creo que esten para ubuntu.

voy a descargarlo ya que avia descargado la amd64.

muchas gracias

---

### Post by pablo.s on 2009-05-11
> **kenet said:**
> soy novato y me esta pareciendo super dificil ubuntu.jejeje

Lleva su tiempo entender un sistema
diferente a lo que estabas usando antes.
Probalo, las dudas e inconvenientes
que se te presenten van a ser resueltas
por mucha gente dispuesta a ayudar. 

> **kenet said:**
> ok, entonces no le pondre el amd64

No te lo recomiendo de entrada porque
en la versión de 64 bits se pueden
presentar problemas que no te van a
agradar si sos nuevo. La versión de 32
bits está mas pulida.

> **kenet said:**
> si quieria instalar solo el ubuntu, pero la mitad de los que uso no creo que esten para ubuntu.

Bueno, te propongo que hagas una
lista con los programas que usas y
muy seguramente te aconsejemos las
opciones de Ubuntu para realizar las
mismas tareas.

---

### Post by kenet on 2009-05-12
muchas gracias

suel usar estos entre otrs cuantos

wise_ftp
nero
WinTV 7
Ares
emule
photoskop
xara 3d
OneClickBlackBerryVideoConverter
Blackberry Device Manager software?

una pregunta que me inquieta. puedo tener conflictos en mi pc por tener los 2 sistemas operativos en el mismo disco?

otra cosita, instale el compiz fusion con este comando

sudo apt-get install  compiz-gnome compizconfig-settings-manager emerald

pero al ir a sistema/preferencias/apariencia/efectos visuales me sigen saliendo 3 opciones, no me sale la de personalizado.

en sistema/preferncia si tento el icono de administrador de opciones compizconfg.

estoy haciendo algo mal?

como puedo borrar lo que instalo ese comando.

ya se que son muchas preguntas pero no la quiero liar de nuevo. saludos y gradias

---

### Post by Hei Ku on 2009-05-12
en realidad el compiz fusion te viene instalado, asi que solo debes haber instalado el emerald. Para administrarlo podes usar el administrador de opciones compizconfg. Creo que todavía se usa ese.

si queres desinstalar algo que instalaste con "sudo apt-get install <programa>", el comando inverso es "sudo apt-get remove <programa>". Tenes que agregar la opcion --purge si queres que ademas de desinstalar el programa, te borre la configuracion. Usalo con cuidado.

No vas a tener conflictos entre los 2 sistemas operativos. Cada uno funciona x separado. Si windows te empieza a andar mal en 2 meses, andá reclamale a ellos, no a nosotros.

---

### Post by milovan1971 on 2009-05-12
Hola,  Sobre los programas para reemplazar los que usas, aca hay una lista bastante completa:  [http://ubuntuforums.org/showthread.php?t=1142336](http://ubuntuforums.org/showthread.php?t=1142336) Suerte!

---

### Post by kenet on 2009-05-12
muchas gracias a los 2, asi da gusto.

 lo desinstalare aunque no se si ara falta. yo lo que quiero es poder usar los efectos de escritorio, etc.
he estado viendo videos que me dejan alucinado. lo que pasa es que cuando me pongo a buscar por interner hay mil cosas distintas de como instalarlo y me vuelven loco.

que si gnome, kde, y un monton de ubuntus distintos y de verdad que viniendo de windows no me entero de nada.jejeje
saludos

---

### Post by josecuervo86 on 2009-05-12
Ejem..no es por hacer autobombo pero el otro dia hice un how-to de como instalar compiz y usar los efectos. Ademas esta explicado como instalar compiz.
El link es este: [http://mglmnc.blogspot.com/2009/04/howto-activar-el-cubo-3d-con-compiz-en.html]("http://mglmnc.blogspot.com/2009/04/howto-activar-el-cubo-3d-con-compiz-en.html")

---

### Post by milovan1971 on 2009-05-12
Para usar el compiz en ubuntu tenes que activar el "Administrador de opciones CompizConfig". 
Aca se explica en detalle como hacerlo:
[http://ubuntu-col.blogspot.com/2009/02/ubuntu-8_306.html](http://ubuntu-col.blogspot.com/2009/02/ubuntu-8_306.html)

Avisa como te va.
:)

---

### Post by kenet on 2009-05-12
muchas gracias a todos, me alegra aver encontrado este foro con tan buen rrollo.

ates de nada queria borrar el que tengo y despues configurarlo desde 0 con los manuakles de arriba.

sudo apt-get remove--purge compiz-gnome compizconfig-settings-manager emerald

estoy poniendo este codigo pero algo estoy poniendo mal.

algien me puede decir lo que esta mal del codigo. 

muchas gracias

---

### Post by josecuervo86 on 2009-05-12
te falta el espacio entre remove y --purege:

```
sudo apt-get remove --purge.....
```

---

### Post by kenet on 2009-05-12
muchisimas gracias ya esta desistalado.

es que desde que vi este video me quede con la boca avierta

[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

a ver si algun dia llego acer eso. jajajaa

---

### Post by josecuervo86 on 2009-05-12
Te digo, que con un poco de conocimiento (que lo obtenes tocando y tocando) y una placa de video decente, podes hacer todo eso. Yo lo logro con una Geforce 8400GS, que es una low-end

---

### Post by kenet on 2009-05-12
yo no se como sera la que tengo, me venia con la pc

Monitor:
Tarjeta gráfica                                   ATI Radeon HD 3400 Series  (256 MB)
Tarjeta gráfica                                   ATI Radeon HD 3400 Series  (256 MB)
Acelerador 3D                                     ATI Radeon HD 3450 (RV620)

---

### Post by Hei Ku on 2009-05-12
Linda placa. Si los drivers te andan bien, no deberías tener problemas en usar Compiz a full.

---

### Post by juancarlospaco on 2009-05-12
> **kenet said:**
> 
suel usar estos entre otrs cuantos

wise_ftp ---> filezilla
nero ---> nero o brasero
wintv 7 ---> tvtime o xawtv
ares ---> ares
emule ---> amule
photoskop ---> photoshop
xara 3d ---> xara lx
oneclickblackberryvideoconverter ---> hay muchos
blackberry device manager software? ---> hay un tuto por ahi en el foro


:p

---

### Post by kenet on 2009-05-13
> **Hei Ku said:**
> Linda placa. Si los drivers te andan bien, no deberías tener problemas en usar Compiz a full.

si, temgo los driver bien enstalados aunque parecca rrado.jejeje

ya pude escribir con fuego, etc.

---

