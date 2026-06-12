---
title: "No me reconoce webcam en Dell 11z"
date: 2010-04-16
forum: Hardware
---

### Post by chivuntu on 2010-04-16
Tengo una Dell inspiron 11z d30 y no logro instalar la webcam en Ubuntu 9.10.
Soy nuevo en Ubuntu y recien compro la laptop. espero que me puedan ayudar

---

### Post by sajnox on 2010-04-16
Las Dell generalmente soportan todo el hardware para Linux, habria que ver tu modelo en particular.

Como sabes que no te detecta la camara? Con que programas la probaste?

Hace lo siguiente

aplicaciones > accesorios > terminal

en la terminal ejecutas 
```

sudo lspci
```

Ojo que te va a pedir un password, es el que usaste como tu usuario para instalar la maquina y mientras lo tipeas no vas a ver que nada se mueva y parece que no tecleas nada, no te preocupes que lo estas haciendo

A lo que responda de ese comando lo copias y pegas en la respuesta en el foro

---

### Post by chivuntu on 2010-04-16
gracias por la respuesta sajnox. instale  el camorama para tratar de hacer andar la camara pero nada...
en /dev/ no me aparece ningun dispositivo de video.
desde ya te agradezco la pronta respuesta y cada vez estoy más contento con el cambio a linux. después de todo estos pequeños inconvenientes te llevan a aprender y a saber que hay un montón de gente dispuesta a ayudarte.

acá te paso el resultado del lspci:

jorge@jorge-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by guillermolisi on 2010-04-16
Repeti la operacion pero en lugar de usar el comando "lspci" utiliza "lsusb". Hace todo igual que antes pero reemplazando el comando. Sospecho que tu webcam es USB.

---

### Post by chivuntu on 2010-04-18
Este es el resultado del lsusb:

Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 064e:8101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by guillermolisi on 2010-04-19
Bueno, pareceria indicar que la webcam es Suyin pero no encuentro ningun manual en Internet con especificaciones como para saber que chip utiliza y asi ver que driver usar.

---

### Post by chivuntu on 2010-04-19
FUNCIONO!!!!:guitar:

AL HACER EL lsusb QUE ME INDICASTE SUPUSE QUE LA CAMARA ERA SUYIN, Y DESPUES DE MUCHO BUSCAR ENCONTRÉ UNA SUGERENCIA DE INSTALAR UN DRIVER GENÉRICO.
HABLABAN DE Linux-uvc, ASI QUE LO PROBÉ Y FUNCIONÓ!!!
SOLO BUSQUÉ EL PAQUETE EN EL GESTOR SYNAPTIC Y LO INSTALÉ.
MUCHAS GRACIAS POR LA AYUDA Y ESPERO QUE LE SIRVA A ALGUIEN MÁS.

---

### Post by alfplayer on 2010-04-19
Qué paquete instalaste?

El driver Linux UVC está en Ubuntu desde la versión 9.04. En otro hilo de otro foro ([http://forum.notebookreview.com/showthread.php?t=464127]("http://forum.notebookreview.com/showthread.php?t=464127")) el driver de esa cámara carga aparentemente sin problemas. La cámara debería funcionar sin instalar ni configurar nada.

---

