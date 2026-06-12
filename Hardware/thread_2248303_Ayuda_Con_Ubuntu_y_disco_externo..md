---
title: "Ayuda Con Ubuntu y disco externo."
date: 2014-10-13
forum: Hardware
---

### Post by jpicehockey27 on 2014-10-13
Hola soy nuevo con Ubuntu y me surgio el siguiente problema.

Tengo conectado un disco externo de 500g que la maquina lo leia sin problemas al igual que mi cel, pero de un dia para el otro los dejo de leer. Me fije en otras maquinas (windows) y el disco aparece sin problemas.
Si pongo el comando lsusb me figuran como conectados los 2.
Trate de hacer lo que vi en otras partes del foro pero no lo pude montar ni nada.

Desde ya agradezco todo tipo de ayuda ya que en el disco externo tengo cosas importante y me gustaria poder volver a verlas....

---

### Post by euzkoarima on 2014-10-15
Si los ve el lsusb supongo que el error está al montarlos.
Podrías copiar el intento de montarlo y la respuesta con el error ?

---

### Post by jpicehockey27 on 2014-10-15
Al tratar de montarlo me sale esto....

mount -t ntfs-3g /dev/sdb /media/usb
Error reading bootsector: Error de entrada/salida
Failed to mount '/dev/sdb': Error de entrada/salida
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Esto ya no entiendo que hacer

---

### Post by euzkoarima on 2014-10-16
En el mensaje dice que pueden ser dos cosas, pero, a partir de lo que contás supongo que ese disco no está en RAID, no ?
(si no sabés que es RAID te pregunto: en windows lo usas junto con otro disco??? si es así averiguo como chequear bien si está en RAID o no, si lo usas solo en ppio es que no está en RAID).

Volviendo, si no es RAID lo que sugiere es que desde windows abras una consola (programa CMD) corras el comando chkdsk /f sobre ese disco, no se que letra le tocó en windows). Que luego reinicies en windows 2 veces y vuelvas a probar en ubuntu a ver si se arregló. Aclara además que es importante el uso del parámetor /f

Pregunta adicional, por qué "media/usb" ? digo, nombre raro para un disco.

---

### Post by jpicehockey27 on 2014-10-16
el disco lo uso como disco externo, nada de en conjunto con otro disco. En la maquina que tengo Ubuntu lo estaba utilizando sin problemas hasta que lo dejo de detectar.
pongo media/usb porque asi lo decia la guia que encotre para montar el disco.

ahora esto mas perdido jajaja 

PD: Mil gracias por la ayuda y disculpa mi ignoranciia en el tema esque soy muy nuevo con Ubuntu

---

### Post by euzkoarima on 2014-10-17
Ok, pero proba entonces de hacer la reparación desde windows a ver si funciona, parecer ser el camino razonable.

---

