---
title: "Integrated webcam HP x2 210 G1"
date: 2020-05-02
forum: Hardware
---

### Post by juanromero on 2020-05-02
[COLOR=#000000][FONT=Verdana][FONT=Verdana]The system cannot find webcam. This is the information that it shows me.

[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]juan@juan-HP-x2-210:~/Escritorio$ lsusb [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Bus 001 Device 003: ID 04f3:074d Elan Microelectronics Corp. [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Bus 001 Device 002: ID 8087:0a2a Intel Corp. [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]juan@juan-HP-x2-210:~/Escritorio$ lspci [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:0a.0 Non-VGA unclassified device: Intel Corporation Device 22d8 (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 22) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81) [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]juan@juan-HP-x2-210:~/Escritorio$ [/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-05-02
Welcome.
This hardware ```
[COLOR=#000000][FONT=Verdana]Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 22)[/FONT][/COLOR]
``` is terrible. I'm surprised you're only compalining about an undetected webcam.

Please consult [Linuxium]("http://linuxiumcomau.blogspot.com/"), your best chance of having things working.

---

### Post by juanromero on 2020-05-03
Thank's, I'm going to try respin iso for Atom...

---

