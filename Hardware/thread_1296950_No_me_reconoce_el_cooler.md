---
title: "No me reconoce el cooler"
date: 2009-10-21
forum: Hardware
---

### Post by Paul Erdos on 2009-10-21
Hola , tengo una toshiba satellite instalé los sensores , pero no me reconoce el fan (cooler) y me gustaría saber si se pueden controlar externamente , ya que por lo que noté , en mi caso deja que se cocine a 80ºC y ahí se enciende el cooler al mango (Control on-off),me parece muuuuuy rudimentario , vista en cambio se enciende unos segundos y varía las revoluciones de acuerdo a la temperatura y al uso de los micros.

---

### Post by sergiom99 on 2009-10-21
Yo empezaria por aca> [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by Paul Erdos on 2009-10-22
Hola , como obtengo el famoso archivo dsdt?¿
otra cosa , que quiere decir cuando pongo :```
martin@martin-laptop:~$ fan
fan: laptop does not have cooling fan or kernel module not installed.
martin@martin-laptop:~$ 

```
y tambien:
```
martin@martin-laptop:~$ cat /proc/acpi/thermal_zone/THRM/cooling_mode
0 - Active; 1 - Passive
martin@martin-laptop:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             62 C
martin@martin-laptop:~$ cat /proc/acpi/thermal_zone/THRM/state
state:                   ok
martin@martin-laptop:~$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
polling frequency:       2 seconds
martin@martin-laptop:~$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           110 C
passive:                 110 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices=
```
el cooling_mode, que es?¿
Gracias , perdón por las molestias.

---

### Post by Paul Erdos on 2009-11-10
Lo saqué del foro de ubuntu españa .
[Solución]

cd /boot/grub
sudo gedit menu.lst

Y en la parte de kernels instalados en el grub(por ejemplo la de acontinuación):

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid 05fc44ae-4f6e-4f2c-94f1-aefc56948fe7
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=05fc44ae-4f6e-4f2c-94f1-aefc56948fe7 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

Añadir acpi_osi="Linux" al final de la linea kernel , de tal manera, que quede así;

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid 05fc44ae-4f6e-4f2c-94f1-aefc56948fe7
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=05fc44ae-4f6e-4f2c-94f1-aefc56948fe7 ro quiet splash acpi_osi=Linux
initrd /boot/initrd.img-2.6.28-15-generic
quiet

y Guardar
Espero que os sea de utilidad;)

---

