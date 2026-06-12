---
title: "Dell E1505 front media buttons"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by HarrisonHopkins on 2007-01-02
Alright, the front buttons on my Dell Inspiron E1505 (Or 6400, both the exact same computer) seem to not work. I  am using Kubuntu 6.06 LTS. I have tried by going into Kmix and setting the buttons, but to no avail. Does anyone know how to set these up in Kubuntu? All I really need are the volume up, down, and mute buttons.

---

### Post by eggdeng on 2007-01-03
Post the output of lspci to see what soundcard you are using.

---

### Post by HarrisonHopkins on 2007-01-03
```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03
)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev
 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio
Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port
 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port
 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1
(rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
(rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3
(rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4
(rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co                 ntroller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg                 e (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial                  ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev                  01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714                 5
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re                 v 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19                 )
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapte                 r (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev                  01)

```

I don't see what that would have to do with the front buttons though? I have sound.

---

### Post by eggdeng on 2007-01-03
The reason I asked is because a lot of us have been having problems with Intel HDA audio and your problem sounded familiar. I'm not sure of my ground here because I don't use KDE and I have a vague idea that KDE apps use arts rather than alsa. I can point you to a couple of threads to get started with alsa if you have the possibility of using it.

Installing alsa (if you haven't already got alsa 1.0.10rc3 or better)
[http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260](http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260)

extra configuration
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383).

---

### Post by nachotronics on 2007-02-17
It sounds to me you just need to adjust the key bindings, in gnome its inside system > preferences,there you can associate the functions to each button, i did this and everything worked fine, even the media direct button, which i use for running RythmBox

Sorry, i don't use KDE, but it shouldn't be that hard to find

Edit:
I found this, it might help

Open up the Control Center
Search Key Bindings
Click on Keyboard Shortcuts

Since i don't have KDE i'm blind gessing, good luck

---

