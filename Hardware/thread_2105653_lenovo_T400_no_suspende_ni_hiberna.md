---
title: "lenovo T400 no suspende ni hiberna"
date: 2013-01-16
forum: Hardware
---

### Post by licurgox on 2013-01-16
Hola a todos! Mi primer post+thread!

A ver si me pueden dar una mano con esto:
Con  una notebook lenovo T400 del laburo estoy teniendo el siguiente  problema, no suspende ni hiberna, la pantalla se pone oscura pero no  queda ni hibernada o suspendida dependiendo del caso, usando la opción  correspondiente del menu "Apagar"

Ubuntu 11.10,  nunca pude volver exitosamente de una hibernacion/suspend.

Ahora estoy usando una  instalación que tenía con una lenovo T61 a la que le saqué el disco  rigido y lo tengo puesto en la T400. De todas formas probé con ubuntu  live-cd's e incluso una instalación en otro disco para probar y pasa lo  mismo.

Estuve probando como root desde la terminal con estos dos comandos:
pm-hibernate
pm-suspend
Hacen lo mismo que desde el menu "Apagar".

Estuve probando cambiando la configuración de opciones de la bios.
No  se si fue eso, ahora esta peor, queda como suspendida/hibernada, y no  vuelve con nada (touchpad, teclado, botón de encendido).

Hay que apretar  el botón de encendido de la notebook 4 segundos para apagar la notebook,  y prender nuevamente para que bootee.

googlie un poco y salen posts viejos no muy relevantes.

Acepto sugerencias...

---

### Post by mad2-814 on 2013-01-16
Puedes poner el resultado del comando

```
sudo lspci
```

Lo siento por mi espanol, soy un estudiante en la universidad :)

---

### Post by aromo on 2013-01-16
Si tu particion swap es menor que tu memoria RAM, nunca te va a hibernar.  Pero deberia al menos suspender...

A mi me pasa lo mismo con Lubuntu 12.10, nunca supe como arreglarlo :0(

---

### Post by licurgox on 2013-01-16
No mencioné que esta misma instalación de ubuntu (enchufo el disco en la T61) hiberna y suspende casi perfectamente, sin problemas en la T61.

~% lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
~%


Hay 6,1 Gb de partición de swap, y 2Gb de memoria, debería funcionar pero no... :(

~% free -m
             total       used       free     shared    buffers     cached
Mem:          1956       1810        146          0         31        484
-/+ buffers/cache:       1295        661
Swap:         5863        341       5522
~%

#tamaño de partición de swap:
~% sudo fdisk -s /dev/sda6
6004736
~%

---

### Post by guillermolisi on 2013-01-17
No me queda claro que version de Ubuntu estas usando en esa maquina (y por lo tanto, no se de que version de kernel se trata).

Si no suspende e hiberna porque no hay un buen reconocimiento ACPI (y por lo tanto un deficiente manejo de consumo/potencia), posiblemente encontremos algo en /var/log/dmesg (desde el boot hasta el final del arranque).

---

### Post by EnriqueK on 2013-01-18
1.- Ejecuta
     sudo blkid 
     copiar el valor de la UUID de la swap y reeplazarlo en
     sudo gedit /etc/fstab
     y en 
     sudo gedit /etc/initramfs-tools/conf.d/resume
2.- sudo /usr/sbin/update-initramfs -u
3.- sudo init 6
Además swap debe ser como mínio del tamaño de la ram si no lo tienes así, te puedo indicar como crear un archivo swap para no tener que modificar tu tabla de particiones.

---

### Post by licurgox on 2013-01-21
> **guillermolisi said:**
> No me queda claro que version de Ubuntu estas usando en esa maquina (y por lo tanto, no se de que version de kernel se trata).

Si no suspende e hiberna porque no hay un buen reconocimiento ACPI (y por lo tanto un deficiente manejo de consumo/potencia), posiblemente encontremos algo en /var/log/dmesg (desde el boot hasta el final del arranque).

guillermo, aca esta la información que faltaba,

~% uname -a
Linux miura 3.0.0-30-generic #47-Ubuntu SMP Wed Jan 2 22:39:01 UTC 2013 i686 i686 i386 GNU/Linux
~% lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
~%



~% dmesg | egrep -i 'acpi|energ|susp'    
[    1.892784] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.892789] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.892873] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.892879] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.943585] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.943590] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.943692] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.943697] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.269487] ata4.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.270396] ata4.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.280886] ata4.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.281792] ata4.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[   30.257054] i915 0000:00:02.0: power state changed by ACPI to D0
[   30.257060] i915 0000:00:02.0: power state changed by ACPI to D0
[   30.310062] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   30.310065] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   30.310067] thinkpad_acpi: ThinkPad BIOS 7UET56WW (2.02 ), EC 7VHT12WW-1.01
[   30.310069] thinkpad_acpi: Lenovo ThinkPad T400, model 6474AV4
[   30.331579] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   30.333717] thinkpad_acpi: radio switch found; radios are enabled
[   30.339079] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   30.340414] Registered led device: tpacpi::thinklight
[   30.340470] Registered led device: tpacpi::power
[   30.340987] Registered led device: tpacpi::standby
[   30.341504] Registered led device: tpacpi::thinkvantage
[   30.343814] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   30.344502] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   30.345870] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input4
[   31.113762] acpi device:02: registered as cooling_device2
[   31.113911] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[  697.056274] thinkpad_acpi: EC reports that Thermal Table has changed
[  698.275332] thinkpad_acpi: EC reports that Thermal Table has changed
[104981.284992] thinkpad_acpi: EC reports that Thermal Table has changed
[104982.785163] thinkpad_acpi: EC reports that Thermal Table has changed
[184611.703844] thinkpad_acpi: EC reports that Thermal Table has changed
[187691.675504] thinkpad_acpi: EC reports that Thermal Table has changed
~%


Como el output del dmesg es largo grepeé eso, si hace falta grepear otra cosa, o poner todo, decime.

---

### Post by guillermolisi on 2013-01-22
Disculpa la pregunta, pero existe alguna razon para seguir usando la 11.10 ?
Mi primera sugerencia, en caso de que no exista razon alguna, es actualizar a la 12.04.1. Fundamentalmente porque cambia el kernel y el 3.2 viene con muchas mejoras para la administracion de energia (y reconocimiento ACPI).

Digo la 12.04 porque es de soporte extendido pero nada impide que actualices a la 12.10 (cuyo kernel es aun mas moderno)

---

### Post by licurgox on 2013-01-24
Si bien ando con poco tiempo, todo lo que me pasen me sirve, si no lo veo ahora, lo veo luego.  Puede tardar un poco en responder.
Sigo con este problema. Les aviso si lo soluciono!



> **EnriqueK said:**
> 1.- Ejecuta
sudo blkid
copiar el valor de la UUID de la swap y reeplazarlo en
sudo gedit /etc/fstab
y en
sudo gedit /etc/initramfs-tools/conf.d/resume
2.- sudo /usr/sbin/update-initramfs -u
3.- sudo init 6
Además  swap debe ser como mínio del tamaño de la ram si no lo tienes así, te  puedo indicar como crear un archivo swap para no tener que modificar tu  tabla de particiones.



~% blkid    
/dev/sda5: UUID="d0d83088-1523-4f47-a77f-4a10fc41d917" TYPE="reiserfs"
/dev/sda6: UUID="ade02858-8bef-4518-b325-f22591880547" TYPE="swap"
~%


                   /etc/fstab
  7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  8 proc            /proc           proc    nodev,noexec,nosuid 0       0
  9 # / was on /dev/sda5 during installation
 10 UUID=d0d83088-1523-4f47-a77f-4a10fc41d917 /               reiserfs notail          0       1
 11 # swap was on /dev/sda6 during installation
 12 UUID=ade02858-8bef-4518-b325-f22591880547 none            swap    sw              0       0


    /etc/initramfs-tools/conf.d/resume
  1 RESUME=UUID=ade02858-8bef-4518-b325-f22591880547
~

Me parece que esta todo bien, no? Todos los UUIDs matchean, así que no hay nada que editar me parece.

Lo  del swap ya conté y expliqué con outputs arriba, la notebook tiene 6gb  de swap vs. 2gb de ram menos el IGP intel, debería sobrar.



> **guillermolisi said:**
> Disculpa la pregunta, pero existe alguna razon para seguir usando la 11.10 ?
Mi  primera sugerencia, en caso de que no exista razon alguna, es  actualizar a la 12.04.1. Fundamentalmente porque cambia el kernel y el  3.2 viene con muchas mejoras para la administracion de energia (y  reconocimiento ACPI).

Digo la 12.04 porque es de soporte extendido pero nada impide que actualices a la 12.10 (cuyo kernel es aun mas moderno)


Hay  una razón, es la notebook del laburo, (hace poquito me pasé a la 11.10!  casi que todavía me estoy acostumbrando. Si, vengo lento con los  updates).

Preferiblemente tengo que hacerlo en un momento que no me genere "downtime" en mi laburo.
Muchas  veces si no hay apuro prefiero, si funciona, seguir usando mientras se  pueda. Es cierto que prontito voy a tener que actualizar, y así lo haré,  a una LTS.

Lo que me da un poquito de bronca por así decirlo, es  que la T61 hiberna y suspende de lujo, con ubuntu instalado, livecd,  etc. y esta T400 es rebelde con eso (a pesar de ser mejor máquina). Y  ambas son notebooks con años en la calle como para que esto funcione  bien.

---

### Post by guillermolisi on 2013-01-24
> **licurgox said:**
> 
Lo que me da un poquito de bronca por así decirlo, es  que la T61 hiberna y suspende de lujo, con ubuntu instalado, livecd,  etc. y esta T400 es rebelde con eso (a pesar de ser mejor máquina). Y  ambas son notebooks con años en la calle como para que esto funcione  bien.
El problema del reconocimiento ACPI del BIOS por parte del kernel Linux tambien hace años que viene tratando de resolverse y ha mejorado mucho pero a partir de las versiones 3.2/3.5 en adelante, por eso mi pregunta sobre si habia una razon para mantenerse en la 11.10.

Considerando que es la maquina del laburo, y sin lograr comprender bien que restricciones pueden jugar, mi sugerencia es actualizar a la 12.04 o a la 12.10 (esta ultima utiliza un kernel mas nuevo aun que la .04)

---

### Post by licurgox on 2013-02-27
malas noticias,

recién instalé ubuntu 12.04.2 i386 en la T400 de cero, pisando todo:
1. si suspendo no vuelve del suspend (igual que antes)
2. no tengo la opción de hibernar en el menu de arriba a la derecha de unity
3. si hiberno por terminal "sudo pm-hibernate" no vuelve del hiberne

el kernel nuevo no arregló esos problemas :(


[FONT=Courier New]miura400:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
miura400:~$

miura400:~$ uname -a
Linux miura400 3.5.0-25-generic #39~precise1-Ubuntu SMP Tue Feb 26 00:11:13 UTC 2013 i686 i686 i386 GNU/Linux
miura400:~$

configuré 8Gb de partición swap:
miura400:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    7811068    0    -1
miura400:~$
[/FONT]


se les ocurre algo?

---

### Post by guillermolisi on 2013-02-27
Esa maquina tiene colocada una tarjeta SD ?
Si es asi, retirala y proba suspender/hibernar.

Si no tiene ni nunca tuvo una SD card colocada, volvemos a empezar.

El tema con la SD card viene de [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550479](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550479)

---

### Post by licurgox on 2013-02-28
no che, no tiene lector de SD.
Tiene un lector de SIM atrás de la  batería, vacío, que no se si esta conectado a algo (venden un módulo  para 3G que no se si este modelo lo tiene adentro, no creo).

solo para probar instalé en otro disco rígido en la misma T400, ubuntu de 64, ubuntu 12.04.2 amd64
con malos resultados:
-no  vuelve del suspend, hay que apagar la notebook presionando 4 segundos  el botón de power y arrancarla de vuelta; con "sudo pm-suspend-hybrid",  tampoco vuelve del suspend, pasa lo mismo que con suspend
-corriendo "sudo pm-hibernate" se apaga, no hiberna

---

### Post by hictio on 2013-03-01
Mirá yo tengo y tuve varias Thinkpads, y nunca tuve mayores problemas con Linux (y menos todavía usando Ubuntu específicamente).
No tengo ni tuve una T400, pero fijate este link (en inglés): [My new test box - and how it wasn't](http://www.dedoimedo.com/computers/my-new-new-test-laptop.html).

---

### Post by licurgox on 2013-03-01
> **hictio said:**
> Mirá yo tengo y tuve varias Thinkpads, y nunca tuve mayores problemas con Linux (y menos todavía usando Ubuntu específicamente).
No tengo ni tuve una T400, pero fijate este link (en inglés): [My new test box - and how it wasn't]("http://www.dedoimedo.com/computers/my-new-new-test-laptop.html").

Gracias por el link, no tiene ninguna solución para el problema de suspender/hibernar.

---

