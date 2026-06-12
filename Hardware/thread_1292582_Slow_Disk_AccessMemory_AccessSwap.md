---
title: "Slow Disk Access/Memory Access/Swap"
date: 2009-10-16
forum: Hardware
---

### Post by jmate24 on 2009-10-16
Hi, I have Been using Ubuntu 9.10 Alpha 6 and Ubuntu 9.10 Beta and have found that generally disk access, memory access, and swap access have been really slow because swappiness is set to Default at 60 and I went and searched back to my old posts about swap and how to change the swappieness of Ubuntu using:
```
gksudo gedit /etc/sysctl.conf
```
and adding this line to the bottom to allow Ubuntu to use memory more instead of swap:
```
vm.swappiness=20
```
but that still made my disk access, memory access and swap access really slow so i played around with the swappiness and found that a swappiness of 40 is the best "vm.swappiness=40" and i have had the fastest disk and memory access that i have ever had. it really shows when i use synaptic to install packages, it used to start by (Reading the database...10% and incrementing by only 1% really slowly about 1% every 5-7 seconds but now it takes less than 3 seconds to 'read the database'.

I hope this helps someone or maybe a few people who are having the same problem or similar problems.

My Build:

Lenovo ideapad Y510
15.4" widescreen
3GB 5300 SODIMM RAM
400GB HDD
20x DVD-RAM
Realtek ABG Wi-Fi
100 M LAN
V.90 56k modem
S-Video TV Out (actually works in 9.10)
3 USB ports 2 on left 1 on right
Next Gen PCMCIA (note no cards are made for it)
Media touch responsive keys (mute, play/pause, stop, back, and forward, and volume work but not the mixer keys)
MMC, MS, MSpro, SD, SDpro, xD (SD and SDpro work and i am not sure about the others)
Blutooth is installed but Ubuntu cannot see the card let alone connect to it.
IR port is not installed it needs a module from Lenovo and a remote.
Both mics work the array and the jack. in 9.10 i am able to play 5.1 on 4.1 speakers. (yes, it has a sub on the bottom next to the screen hinge on the right.
and the touch pad works but in the system>preferences>mouse the button to 'enable' the touch pad to disable while you type does not work but the horizontal scrolling works.

i hope that this helps...
jmate24 --

---

