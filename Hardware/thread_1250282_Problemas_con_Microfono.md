---
title: "Problemas con Microfono"
date: 2009-08-26
forum: Hardware
---

### Post by krakc on 2009-08-26
Hola

les comento que he querido usar mi microfono paragrabar (como hacia en windows) y ahora en ubuntu he tenido problemas...

Resulta que abro el grabador de sonidos, pongo a grabar y la barra siempre se ve en la mitad y cuando hablo no se mueve... entonces gritoooo!!!! para ver si se escucha algo... y la verdad si, pero tengo que subirle todo el volumen a los parlantes para que se escuche tenuemente lo que he grabado (un gritoooo)...

entonces esto quiere decir que el micro esta bueno y que me lo reconoce pero yo quiero es poder grabar sonidos que se escuchen sin tener que !!! gritar !!! XD ...

sera que tengo que instalar el open sound system ??? me quedo con los ALSA... que hago???

gracias.

EDITO: al correr lspci

> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
03:06.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)
03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


---

### Post by guillermolisi on 2009-08-26
> **krakc said:**
> Hola

les comento que he querido usar mi microfono paragrabar (como hacia en windows) y ahora en ubuntu he tenido problemas...

Resulta que abro el grabador de sonidos, pongo a grabar y la barra siempre se ve en la mitad y cuando hablo no se mueve... entonces gritoooo!!!! para ver si se escucha algo... y la verdad si, pero tengo que subirle todo el volumen a los parlantes para que se escuche tenuemente lo que he grabado (un gritoooo)...

entonces esto quiere decir que el micro esta bueno y que me lo reconoce pero yo quiero es poder grabar sonidos que se escuchen sin tener que !!! gritar !!! XD ...

sera que tengo que instalar el open sound system ??? me quedo con los ALSA... que hago???

gracias.

EDITO: al correr lspci
Revisaste el nivel del control de captura y ganancia del microfono en el mixer y/o alsamixer ?

---

### Post by krakc on 2009-08-26
Me voy a: Sistema -> Preferencias -> sonido

alli dejo todo en autodetectar y en captura de sonido dejo: 
INTEL82801DB-ICH4 WITH CMI9761A+ INTEL82801DB-ICH4 (ALSA)

mas abajo en mezclador dejo: INTEL82801DB-ICH4 (Alsa mixer)

ahora me voy a Control de volumen y hago lo siguiente:

dispositivo: INTEL82801DB-ICH4 (Alsa mixer)
preferencias : activo todas las opciones

** Pestaña reproduccion: 

Maestro - al maximo 
PCM - al maximo
Center - al maximo
LFE - al maximo
Entrada de linea - al maximo
CD - al maximo
microfono -  3/4 del maximo : Si subo todo empieza a zumbar.
IEC958 Playback AC97-SPSA - al maximo
Altavoz del equipo - al maximo
Aux - al maximo

** Pestaña grabacion:

Capturar - Al maximo - icono de micro con una x roja : al hacer click alli me aparece un microfono, si cierro y vuelvo a entrar, otra vez esta la x roja.

** Pestaña conmutadores: (activadas)

microfono capturar - mic boost (+20dB) - IEC958 - IEC958 capturar - External amplifier

** Pestaña opciones:

Surround jack mode: Shared : otra opcion es Independiente
Mic selec: mic 1 : En mic 2, no se escucha ni gritando.
IEC958 playback source: SPDIF-In : otras opciones son AC-link y ADC
Mono auotput select : mix : otra opcion es mic
Channel mode: 2ch : otras opciones son 4ch y 6ch

---

### Post by krakc on 2009-08-27
sigo sin poder usar mi microfono... alguien me ayuda??

---

### Post by guillermolisi on 2009-08-27
Por las dudas y dado que el tema viene ciertamente complicado, leiste [este thread]("http://ubuntuforums.org/showthread.php?t=1197870&highlight=pulse+audio") ?

---

### Post by krakc on 2009-08-27
He hecho todo eso

cuando reinicio la pc, me aparece en silencio el sonido, vuelvo y le subo el volumen a todo y sigue el mismo problema

tengo que gritar para que mi voz la capte el micro...

---

