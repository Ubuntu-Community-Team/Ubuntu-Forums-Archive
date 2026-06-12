---
title: "[SOLVED] SoundBlaster PCI 128"
date: 2009-08-14
forum: Hardware
---

### Post by GerryEastwood on 2009-08-14
> **josecuervo86 said:**
> Para responder la primera: en una terminal ejecuta

```
lspci
```

y despues pega aca lo que te salga.

```
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

```

Gracias. La Realtek es la "placa" onboard.

---

### Post by Hei Ku on 2009-08-14
Movi el post aparte para tratarlo como corresponde.

PS. movido al foro de hardware.

---

### Post by GerryEastwood on 2009-08-14
OK, gracias.

---

### Post by josecuervo86 on 2009-08-14
Y el problema era? No tenes sonido verdad?

---

### Post by guillermolisi on 2009-08-14
Es que esa maquina tiene dos placas de red > 
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
 y ninguna es SB como se pensaba

---

### Post by josecuervo86 on 2009-08-14
> **guillermolisi said:**
> Es que esa maquina tiene dos placas de red  y ninguna es SB como se pensaba

[quote=GerryEastwood]Mi placa es PCI (más exactamente la SoundBlaster PCI 128 ) y encontré que tengo que buscarla como ES1370[/quote]

Guille, esto lo rescate del post anterior del cual fue cortado este nuevo. Igual, son placas de sonido (a no ser que ahora creative haga placas de red :))

Ahora GerryEastwood, podrias ejecutar en una consola lo siguiente:

```
alsamixer
```

Y fijate si no tenes ningun canal en mute

Otra cosa que estaria bueno es que pusieras esto:

```
gstreamer-properties
``` 

y te fijaras como tenes configurados los canales

Otra cosa que podrias intentar (mas adelante, si no se soluciona con las otras) es desabilitando la placa de audio on-board desde el setup de la BIOS que fue lo que hice yo.

---

### Post by GerryEastwood on 2009-08-15
¡Gracias! :guitar:

Con ```
gstreamer-properties
``` funcó.

No tenía audio porque me tomaba como predeterminada la placa onboard, lo que, de paso, me sirvió para darme cuenta de que no la había deshabilitado desde la BIOS.

Y (ya que estamos) también tengo dos placas de red :lolflag:

---

### Post by josecuervo86 on 2009-08-16
De nada Gerry, suerte!!

---

