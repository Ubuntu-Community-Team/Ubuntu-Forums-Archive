---
title: "Ya volvi al KK y no anda el wIfI"
date: 2010-05-11
forum: Hardware
---

### Post by danetche on 2010-05-11
Buenas Noches a todos...


Amis: Ya pasè la "Lija" y volvi a instalar el Karmik que tan bien me andaba. Comencè por poner el UNRemix, pero al no arrancarme el WiFi, desisti y pase a la version escritorio para mi Lenovo S10e como tenia instalada antes. 
Tengo a Ubuntu compartiendo disco con Wndw$ sin particion.

Vivo en un Club en mi barco, y el wifi es la unica manera de acceder a internet acà. 

No arranco, me lei toda la ayuda de Ubuntu sin exito, y fui al modem de entrada de internet al club y complete la instalacion por cable, esperando que con esto arranque... no fuè asi.
El Network manager no muestra la casilla de "Habilitar red inalàmbrica" (o algo parecido) y sì la de "habilitar red"
Habilite los Orìgenes con toda amplitud, que en alguna instalacion anterior me abrio la puerta al wifi, pero el Broadcomm no resucita.

Alguien que me sugiera alguna cosa, que no tengo ganas de poner el Wndw$ ni para escribirles a Uds...

Antes andaba perfecto, y ahora en esta porqueria tambien anda!

Abrazos,
Daniel

---

### Post by z37a on 2010-05-13
> **danetche said:**
> 
Vivo en un Club en mi barco, y el wifi es la unica manera de acceder a internet acà. 


Algunas chicas y ofrecimiento y llenas al barco de técnicos ubunteros!!!! Jajajaja

Ahora con la WiFi que placa WiFi tenes, si podes ejecuta al comando lspci y publica el contenido, así se ve que placa es bien.

PD: Volvistes a KK desde Lucid? Por esto mismo?

---

### Post by guillermolisi on 2010-05-14
> **z37a said:**
> Algunas chicas y ofrecimiento y llenas al barco de técnicos ubunteros!!!! Jajajaja

Ahora con la WiFi que placa WiFi tenes, si podes ejecuta al comando lspci y publica el contenido, así se ve que placa es bien.

PD: Volvistes a KK desde Lucid? Por esto mismo?
Tambien publica la salida del comando "lsusb" (sin las comillas).

---

### Post by danetche on 2010-05-15
> **z37a said:**
> Algunas chicas y ofrecimiento y llenas al barco de técnicos ubunteros!!!! Jajajaja

Ahora con la WiFi que placa WiFi tenes, si podes ejecuta al comando lspci y publica el contenido, así se ve que placa es bien.

PD: Volvistes a KK desde Lucid? Por esto mismo?

Si, el Lucid me hizo bosta todo lo que andaba, tal como publique, y ahora despues de 4 o 5 reinicios aparecio el network manager y todo funciona.
Igual, acá te pongo lo que me tiro el "lspci"

susanaaguirrezabala@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
susanaaguirre@ubuntu:~$

---

### Post by danetche on 2010-05-15
> **guillermolisi said:**
> Tambien publica la salida del comando "lsusb" (sin las comillas).

Aca te va, y en el otro post ya puse que finalmente KK se conecto.


susanaaguirrezabala@ubuntu:~$ lsusb
Bus 001 Device 008: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15d9:0a4c Unknown 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
susanaaguirrezabala@ubuntu:~$ 

Chasss grxs, y antes de ir a Lucid me van a tener que agarrar entre muchos!
Llevo 3 dias poniendo todo en orden otra vez...

Abrazosss

Daniel

---

### Post by z37a on 2010-05-15
Después de ver esto y muchos casos mas me parece que estaría bueno armar un lista negra donde la encabece VIA, SYS y Broadcom!!!!!!

Por otro lado muy bueno que lo halla tomado después de unos reinicios, capaz alguna actualización o algo te lo tomo!

---

### Post by danetche on 2010-05-15
> **z37a said:**
> Después de ver esto y muchos casos mas me parece que estaría bueno armar un lista negra donde la encabece VIA, SYS y Broadcom!!!!!!

Por otro lado muy bueno que lo halla tomado después de unos reinicios, capaz alguna actualización o algo te lo tomo!

Juaaaa..., ni que lo supieras: me esta esperando la PC de escritorio donde tengo Ubuntu KK en un segundo disco, que tiene VIA!!! (800 x 600, una grosería!)
Y no consigo que me tome el CD de instalacion, ahora estoy bajando el Alternate... mañana te cuento.

Y tampoco me dejo "actualizar" al Lucid, tratare de hacer una inst. limpia. (Si me lee el cd)
Zoabrassss

---

