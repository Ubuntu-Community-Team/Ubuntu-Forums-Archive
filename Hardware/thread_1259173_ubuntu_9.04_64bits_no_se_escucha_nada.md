---
title: "ubuntu 9.04 64bits no se escucha nada"
date: 2009-09-06
forum: Hardware
---

### Post by tsueseres on 2009-09-06
hola, he instalado ubuntu 9.04 de 64 bits en mi laptop hppavilion dv7-2185dx y he actualizado todo en el gestor de actualizaciones, tmb reiniciado y no se ecucha nada ni el intro de ubuntu, en las canciones mp3 aparece que se estan reproduciendo pero no se escucha nada,

---

### Post by Hei Ku on 2009-09-06
Problema especifico de tu hardware, asi que seria bueno que pegues el resultado de lspci.

---

### Post by tsueseres on 2009-09-06
> **Hei Ku said:**
> Problema especifico de tu hardware, asi que seria bueno que pegues el resultado de lspci.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

### Post by josecuervo86 on 2009-09-06
Primero que nada pone:

```
alsamixer
```

en una terminal y fijate que no haya canales en mute. Segundo, pone:

```
gstreamer-properties
```

Y fijate que las salidas esten bien configuradas

Despues comenta que tal te fue ;)

---

### Post by tsueseres on 2009-09-06
> **josecuervo86 said:**
> Primero que nada pone:

```
alsamixer
```

en una terminal y fijate que no haya canales en mute. Segundo, pone:

```
gstreamer-properties
```

Y fijate que las salidas esten bien configuradas

Despues comenta que tal te fue ;)

ya intente y le di prueba con todas las opciones y con ninguna se escucha nada

---

### Post by Hei Ku on 2009-09-06
Te fijaste este thread? Parece ser tu misma placa, y tuvo que habilitar un par de modulos extra.

[http://ubuntuforums.org/showthread.php?t=1250187](http://ubuntuforums.org/showthread.php?t=1250187)

---

### Post by tsueseres on 2009-09-09
> **Hei Ku said:**
> Te fijaste este thread? Parece ser tu misma placa, y tuvo que habilitar un par de modulos extra.

[http://ubuntuforums.org/showthread.php?t=1250187](http://ubuntuforums.org/showthread.php?t=1250187)

hola, ya lo cheque pero no ni aun con kmix se arregla no se escucha nada

---

### Post by guillermolisi on 2009-09-09
> **tsueseres said:**
> hola, ya lo cheque pero no ni aun con kmix se arregla no se escucha nada
Pregunto .... con otro sistema operativo funciona razonablemente bien el audio en esa maquina ?

---

### Post by Hei Ku on 2009-09-09
Habilitaste los modules que menciona ese thread?

---

### Post by tsueseres on 2009-09-11
> **Hei Ku said:**
> Habilitaste los modules que menciona ese thread?
1.si en windows se escucha muy bien

2.si si habilite los modulos que menciona

---

### Post by guillermolisi on 2009-09-12
Sera que hay algo que falta hacer con PulseAudio o estas utilizando solamente Alsa (PulseAudio desinstalado) ?

---

### Post by tsueseres on 2009-09-15
> **guillermolisi said:**
> Sera que hay algo que falta hacer con PulseAudio o estas utilizando solamente Alsa (PulseAudio desinstalado) ?

ya lo probe de muchas maneras incluyendo alsa con y sin

---

