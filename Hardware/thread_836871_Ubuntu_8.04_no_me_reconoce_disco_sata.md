---
title: "Ubuntu 8.04 no me reconoce disco sata"
date: 2008-06-21
forum: Hardware
---

### Post by pelex on 2008-06-21
Hola a todos. Estoy tratando de instalar Ubuntu 8.04 sin éxito.
En mi PC tengo 2 discos rígidos, un IDE de 80 G y un SATA de 160 G.
El problema es que cuando intento instalarlo desde el live CD, no "ve" el disco SATA, que es donde quiero instalarlo. Por el contrario, si detecta sin problemas el otro disco.
En el disco SATA tengo funcionando Windows XP sin problemas. Tengo las particiones hechas y listas para Ubuntu, si es que se deja instalar.
Si alguien me puede ayudar, agradecido.

---

### Post by Hei Ku on 2008-06-21
tenes 2 caminos alternativos para probar. Uno es con Wubi, que se instala desde windows, y el otro es con el alternate cd.

Por otro lado, podrias intentar arrancar el LiveCD con la opcion noapic=off
Eso puede ser que solucione el tema de q no se ve el disco

---

### Post by pelex on 2008-06-22
Gracias Hei Ku, con Wubi ya probé, cuando aparece la primera pantalla, donde te pregunta donde instalarlo, reconoce las 3 particiones, las 2 del SATA y 1 del IDE. He probado de instalarlo en las tres, se instala sin problemas, pero cuando se reinicia me da distintos tipos de errores (según disco y partición) y no puedo avanzar.
Voy a probar con esto que me sugerís > noapic=off a ver que pasa.
Gracias :)

---

### Post by Hei Ku on 2008-06-22
ojo que a linux no lo podes instalar en una particion ntfs. tiene que tener una particion ext3, reiserfs o similar. si bien puede usarlas para escribir y archivos, no puede bootear desde ntfs. Y necesita ademas una particion swap para los archivos temporales, que no tiene formato.

---

### Post by rober-mpp on 2008-06-22
Algunas maquinas tienen un setting para los controladores SATA en el bios, que en mi caso he tenido que tocar para que me reconozca discos a la hora de bootear. No se cual sera tu equipo, pero le podes echar una mirada. 
Suerte con eso!!

---

### Post by pelex on 2008-06-22
> **Hei Ku said:**
> ojo que a linux no lo podes instalar en una particion ntfs. tiene que tener una particion ext3, reiserfs o similar. si bien puede usarlas para escribir y archivos, no puede bootear desde ntfs. Y necesita ademas una particion swap para los archivos temporales, que no tiene formato.

Gracias Hei Ku, las particiones que preparé son 3, 2 Ext3 y una Swap

---

### Post by pelex on 2008-06-22
> **rober-mpp said:**
> Algunas maquinas tienen un setting para los controladores SATA en el bios, que en mi caso he tenido que tocar para que me reconozca discos a la hora de bootear. No se cual sera tu equipo, pero le podes echar una mirada. 
Suerte con eso!!
Gracias rober-mpp, la Bios lo reconoce, de hecho tengo XP instalado

---

### Post by pelex on 2008-06-24
Bueno, quiero darles las gracias por su ayuda, pero no he podido hacerlo funcionar.
Probé de varias formas, instalarlo en el SATA, instalarlo en el disco IDE (con sus particiones correspondientes de Linux), con Wubi dentro de Windows en el disco SATA, con Wubi en el IDE... y nada funcionó.
Incluso hasta metí mano dentro de la máquina, porque tenía el disco IDE como Master y lo cambié a Slave. Tampoco anduvo.
Por si le sirve a alguien que tenga un problema similar, probé con un Live CD de la versión 7.04 de Ubuntu, y desde ahí si puedo ver el disco SATA. Incluso lo pude instalar después de particionar, pero nunca arrancó.
Llevo un par de días intentando, pero creo que acá lo dejo.
Gracias nuevamente.

---

### Post by pelex on 2008-07-06
\\:D/¡¡Problema solucionado!!
Paso a contar por si le sirve a alguien con un problema similar.
Después de intentar en vano instalar Ubuntu en el disco SATA, lo instalé en el disco PATA. Hasta ahí todo bien, la instalación sin problemas.
El problema fue al reiniciar, ya que arrancaba directamente el XP y del GRUB ni noticias.
Entré al BIOS y cambié el orden de arranque de los discos, puse primero al PATA y después al SATA. Apareció el GRUB pero no me aparecía la opción de arrancar con XP.
Después de buscar un rato con San Google encontré esto en un foro y supuse que se podía aplicar a mi problema:

[U]Desde un terminal:
[/U]
sudo gedit /boot/grub/menu.lst

_Y se agrega lo que sigue:_

title Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

y ¡¡SIIII!! Funcionó

Saludos :)

---

