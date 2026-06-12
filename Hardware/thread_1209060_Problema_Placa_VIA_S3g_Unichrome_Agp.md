---
title: "Problema Placa VIA S3g Unichrome Agp"
date: 2009-07-09
forum: Hardware
---

### Post by kin6kill3r on 2009-07-09
Buenas, gracias ante todo, tengo un mother asus con una placa de estas caracteristicas pero no logro hacer que Ubunto 9.0.4 lo reconozca por lo que la imagen es grande.
No encontre nada referido.
[B]
Al margen quisiera saber que placas de video puedo usar con UBUNTU que las soporte sin problemas.?[/B]

Asi que si ustedes me pueden guiar en como hacer para que la tome estare muy agradecido.
Saludos.-):P

---

### Post by pmdrago on 2009-07-09
Hola! soy nuevo en ubuntu, estoy migrando de lo de nuestro amigo gates...
acabo de instalar el 9.04. y por ahora solo surgió un problema q a pesar de haber revisado google durante un buen rato no logre solucionar, aunque me di cuenta q muchos tuvieron el mismo problema....

No puedo cambiar la resolucion de  pantalla!! esta en 800x600 (4:3) .Necesitaría ayuda para poder modificar la resolución max a 1024x768.
la verdad es q el problema lo encontré hasta en este mismo foro pero no puede darle solución. Tengo un monitor compaq mv 540. quiza tenga q bajar bien el driver (cosa q no tengo idea de como hacerlo)
 la verdad me mareo los pasos a seguir y termino mezclando, quiza no este siguiendo bien los pasos, pero como verán soy demasiado novato en esto...

si alguien me puede tirar una pista....

desde ya infinitas gracias!!!! especialmente por su paciencia y tiempo!!

---

### Post by staar on 2009-07-10
para que sepamos que placa de video tenés, posteá acá la salida de correr ```
lspci
``` en una Terminal...

saludos

---

### Post by pmdrago on 2009-07-10
Esto es lo q sale al poner lspci en una terminal: 

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


Gracias!

---

### Post by staar on 2009-07-10
el problema es que las placas VIA no tienen un driver decente actualmente en linux, el que provee el fabricante es muy malo, prácticamente inusable, por lo que se termina usando el driver genérico VESA...

igual, hay forma de forzar la resolución que querés, posteá el contenido de tu archivo /etc/X11/xorg.conf y te decimos que le tenés que modificar...

PD: con esa placa, olvidate de los efectos de escritorio (el cubo y esas cosas) y de cualquier juego que requiera aceleración 3D, lo lamento...

las placas que andan bien en ubuntu, sin problemas, son las nvidia...

saludos

---

### Post by staar on 2009-07-10
-

---

### Post by guillermolisi on 2009-07-10
Uni los threads porque ambos se refieren al mismo hardware y posiblemente tambien coincidan en su solucion.

---

### Post by pmdrago on 2009-07-10
> **staar said:**
> el problema es que las placas VIA no tienen un driver decente actualmente en linux, el que provee el fabricante es muy malo, prácticamente inusable, por lo que se termina usando el driver genérico VESA...

igual, hay forma de forzar la resolución que querés, posteá el contenido de tu archivo /etc/X11/xorg.conf y te decimos que le tenés que modificar...

PD: con esa placa, olvidate de los efectos de escritorio (el cubo y esas cosas) y de cualquier juego que requiera aceleración 3D, lo lamento...

las placas que andan bien en ubuntu, sin problemas, son las nvidia...

saludos
Esto es como quedo el xorg.conf despues de tantas idas y venidas pero no funcionaron.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option "DPMS"
    HorizSync 31-54
    VertRefresh 50-120
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device       "Configured Video Device"
   Monitor      "Configured Monitor"
   DefaultDepth   24
   SubSection "Display"
      Depth      1
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      4
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      8
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      15
      Modes     "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      16
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      24
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

A ver q se puede hacer. >Grax!

---

### Post by staar on 2009-07-10
ese xorg.conf tiene un pequeño error, pequeño, pero no por eso menos importante, y creo es la causa de tu problema ```
Section "Monitor"
    Identifier    **"Generic Monitor"** **<- esto**
    Option "DPMS"
    HorizSync 31-54
    VertRefresh 50-120
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device       "Configured Video Device"
   Monitor      **"Configured Monitor"** **<- tiene que ser igual a esto**
   DefaultDepth   24
   SubSection "Display"
      Depth      1
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      4
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      8
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      15
      Modes     "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      16
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      24
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
EndSection
``` porque sino estás configurando dos monitores diferentes, no importa como le pongas, a los dos Generic o a los dos Configured o el nombre que quieras, lo importante es que sea el mismo...

saludos

---

### Post by pmdrago on 2009-07-11
Sigue sin solucionarse...
puse a los dos configure monitor y nada...

Gracias!

---

