---
title: "AMD64+Realtek880: Problema de sonido (Alt+Tab/Compiz)"
date: 2009-06-09
forum: Hardware
---

### Post by miorda on 2009-06-09
Hola, qué tal?
Hace unos meses que empecé en GNU/Linux con la versión Intrepid Ibex de Ubuntu como LiveCD, luego con Ubuntu Studio, Luego Ubuntu Jaunty Jackalope y, actualmente, con Linux Mint 7 (también basado en Ubuntu).
Pregunto esto porque no encontré este problema en particular en ningún foro (en español y en inglés), de estar en algún lado, avisen nomás, no es la idea hacer mil posts sobre lo mismo, en fin.
Mi problema puntualmente es el siguiente:
En ninguna de las distribuciones y versiones que instalé me anduvo bien el sonido a pesar de haber instalado todos los drivers y códecs que encontré. El problema se da siempre que estoy escuchando música (ya sea en Totem, Rythmbox, Audacious) cuando hago Alt+Tab el sonido se entrecorta, se acelera, o bien se detiene. Con Compiz, lo que ocurre es que al hacer zoom, por ejemplo, durante el tiempo en el que está ampliado el escritorio, el audio se ralenta (se escucha mucho más lento y grave, un pitch down podría decirse) y cuando vuelvo del zoom el sonido vuelve a la normalidad.
Mi máquina es un AMD64 (no dual), 1GB de RAM, placa de sonido onboard Realtek 880, placa de video onboard NVIDIA GeForce 6150.
Qué hice para modificarlo y no dio resultado:
- Instalé miles de drivers, códecs, libs, etcétera.
- Instalé distribuciones de 32 bits. (mi amigo tiene un Intel de 32 bits, probó muchas distros, entre ellas, Ubuntu, Debian, OpenSUSE, Linux Mint, Fedora, y jamás tuvo el mismo problema)
- Reinstalé las distribuciones para estar en cero y arrancar de nuevo.
Cómo puedo solucionar este tema? 
Gracias y aguante.

---

### Post by Mauro22 on 2009-06-09
Hola!!

No quiero decir una paparruchada ¿?


:KS


Por lo que vi siempre usaste distros que tienden a Gnome... 

1) No me quedo claro si tenes (y usas) los 64bits
2) Probaste con entornos mas livianos? Desde el punto de vista tecnico no seria problema, pero al tener un mononucleo y 1gb de ram y querer mover gnome, compiz y la zarta de efectos que trae, se me ocurre en que ocurre "un cuello de botella"
3) Si podes, proba un LiveCD... con ello descartas el hardware, asi que te queda por insultar nomas...
4) Si se me ocurre algo te lo pregunto.

):P

---

### Post by staar on 2009-06-09
pregunta, con distros no basadas en ubuntu probaste?, se me hace que es un problema con ese chip de audio y linux (o alsa), posteá la salida de poner ```
lspci
``` en una Terminal, para que sepamos el modelo exacto de la placa de audio...

saludos

---

### Post by miorda on 2009-06-09
Antes que nada, gracias por responder y por hacerlo tan rápido, buena onda.

Mauro22: 
1) Tengo 64 bits y probé distros preparadas tanto para 64 como para 32 (en este momento estoy con Linux Mint 32)
2) Siempre usé GNOME, KDE es más liviano? Casualmente hoy estuve probando SLAX (el live USB basado en Slackware) que viene con KDE. Con respecto al Compiz no me parece fundamental usarlo, puedo prescindir tranquilamente de él, eso no es problema (a propósito, necesita más de 1GB de RAM?). El tema es que, con o sin Compiz activado, al hacer Alt+Tab o scrollear con el mouse en una página, un PDF o en una aplicación (por ejemplo, Inkscape) el sonido se entrecorta.
3) LiveCD probé sólo el de Ubuntu Intrepid Ibex de 32 bits pero no recuerdo haberme puesto a escuchar música y, a la par, usar otra aplicación. Igual, no me entusiasma la idea de tener el SO en LiveCD, prefiero tenerla en el rígido.

staar:
Probé lo que me dijiste y me tiró esto (pongo todo el log porque sinceramente no sé si lo que no dice "audio device" influye también, perdón si no era así por las sobras):

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

Muchas gracias otra vez, aguante :D

---

### Post by guillermolisi on 2009-06-10
> **miorda said:**
> Antes que nada, gracias por responder y por hacerlo tan rápido, buena onda.

Mauro22: 
1) Tengo 64 bits y probé distros preparadas tanto para 64 como para 32 (en este momento estoy con Linux Mint 32)
2) Siempre usé GNOME, KDE es más liviano? Casualmente hoy estuve probando SLAX (el live USB basado en Slackware) que viene con KDE. Con respecto al Compiz no me parece fundamental usarlo, puedo prescindir tranquilamente de él, eso no es problema (a propósito, necesita más de 1GB de RAM?). El tema es que, con o sin Compiz activado, al hacer Alt+Tab o scrollear con el mouse en una página, un PDF o en una aplicación (por ejemplo, Inkscape) el sonido se entrecorta.
3) LiveCD probé sólo el de Ubuntu Intrepid Ibex de 32 bits pero no recuerdo haberme puesto a escuchar música y, a la par, usar otra aplicación. Igual, no me entusiasma la idea de tener el SO en LiveCD, prefiero tenerla en el rígido.

staar:
Probé lo que me dijiste y me tiró esto (pongo todo el log porque sinceramente no sé si lo que no dice "audio device" influye también, perdón si no era así por las sobras):

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

Muchas gracias otra vez, aguante :D
No veo ninguna placa de sonido Realtek en esa maquina.

---

### Post by Mauro22 on 2009-06-10
> **miorda said:**
> 
**00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)**


Esa es la placa de sonido... Es un mother con chipset Nvidia.

---

### Post by miorda on 2009-06-10
Es raro. cuando estaba en windows tenia una interfaz gráfica de realtek para configurarla y funcionaba perfecto, o sea, siendo el soft de Realtek y la placa nVIDIA, según lo que me saltó aca. 
De todas formas, sabiendo ahora que la placa es nVIDIA qué tendría que hacer? 
En este momento estoy corriendo desde USB una versión de Puppy Linux (Pupitup) pensada para hacer música y el audio suena genial, no se traba ni se corta, nada. Creo que el escritorio es Xfce, estuve averiguando que es más liviano q Gnome y KDE.
Che, gracias de nuevo, a todo/as, posta :)

---

### Post by staar on 2009-06-10
la mother es Nvidia (por cierto, que modelo exacto es?), pero el codec de audio es Realtek (como en casi todas las placas integradas), si con XFCE no te pasa, podrías probar xubuntu, que es la versión de ubuntu con ese escritorio...

saludos

---

### Post by miorda on 2009-06-10
staar:
El modelo exacto de la placa es K8NGM2.
Aaaah, Realtek era el códec de audio, perdón, no sabía, pensé que era la placa.
Me bajé el Xfce para el Linux Mint e inicié sesión con Xfce pero peor, el sonido suena como si estuviera apretando el FF. Quizás tendría que hacerlo más limpio e instalar de una Xubuntu y no el desktop Xfce, no?

---

