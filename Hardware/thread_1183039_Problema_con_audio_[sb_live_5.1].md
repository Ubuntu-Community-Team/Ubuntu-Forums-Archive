---
title: "Problema con audio [sb live 5.1]"
date: 2009-06-09
forum: Hardware
---

### Post by shagOx on 2009-06-09
Hola primero que todo, queria contarles que soy nuevo en ubuntu, la cosa es que instale ubuntu y me gusto muchisimo,pero al momento de escuchar una cancion me doy cuenta de que el audio esta muerto, si me pudieran ir ayudando pofavor en los pasos para lograr arreglarlo se los agradeceria, yo he intentado arreglarlo buscando en google, ayer estuve hasta las 5 de la mañana intentando arreglarlo pero nada :(
pd.mi tarjeta de audio es una SB Live 5.1.
pd2. buscando en internet me decian que podia arreglarlo con el ASLAMIX, pero al abrir el ALSAMIX me sale el siguiente error:

[IMG]http://img521.imageshack.us/img521/8762/asdasdi.png[/IMG]



De antemano Muchas Gracias :)

---

### Post by moreback on 2009-06-09
Que yo sepa el comando es alsamixer y se ejecuta en una consola. La idea de este comando es que primero verifiques que los volúmenes están todos al 100%.

Igual el mensaje es poco, necesitamos modelo del pc, versión de Ubuntu y la salida a los siguientes comandos:

```
**lspci**
```

```
**aplay -l**
```

Péganos esa información y te podremos orientar.

---

### Post by shagOx on 2009-06-09
Mi pc es un pentium 4 / 3.07 ghz / 1gb de ram y estoy con la version 9.04

```
santiago@santiago:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
00:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```



```
 santiago@santiago:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:27:1:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/santiago/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Argumento inválido
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:226: control open (0): Argumento inválido
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:27:1:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/santiago/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Argumento inválido
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:226: control open (1): Argumento inválido

```
eso es lo que me sale

---

### Post by kamus on 2009-06-11
> **shagOx said:**
> Mi pc es un pentium 4 / 3.07 ghz / 1gb de ram y estoy con la version 9.04

```
santiago@santiago:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
00:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```



```
 santiago@santiago:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:27:1:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/santiago/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Argumento inválido
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:226: control open (0): Argumento inválido
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:27:1:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/santiago/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Argumento inválido
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:226: control open (1): Argumento inválido

```
eso es lo que me sale

Estimado, has modificado algo en alsa o/y actualizado de version? Intenta borrar el archivo /home/santiago/.asoundrc y reinicia tu equipo.

Salu2

---

