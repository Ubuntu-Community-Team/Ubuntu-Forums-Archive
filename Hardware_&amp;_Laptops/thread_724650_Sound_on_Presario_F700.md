---
title: "Sound on Presario F700"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by red_hax0r on 2008-03-14
I'm using Ubuntu 7.10 on a Compaq Presario F700, and I've been having a lot of trouble with the hardware.  I've gotten everything to work except the sound card now.  It acts like it's working and the volume is fine (i.e. not muted).  The device is recognized and everything.  But no sound!

I'll give you my lspci -v.  Any more information you need along with the commands to obtain the information, just ask.  

> 
        00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping


---

### Post by red_hax0r on 2008-03-14
Here's aplay -l if you need that too:

> 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by superprash2003 on 2008-03-14
try this.. may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by red_hax0r on 2008-03-14
Actually, I already tried that. I tried again just to make sure and it still doesn't work

---

### Post by red_hax0r on 2008-03-15
Any more ideas?

---

### Post by red_hax0r on 2008-03-15
I got it to work using OSS version 4, but I still have to make a custoim applet or something, because the volume control applet doesn't work now.

---

### Post by Yellow Pasque on 2008-03-15
> **red_hax0r said:**
> I got it to work using OSS version 4, but I still have to make a custoim applet or something, because the volume control applet doesn't work now.
Use this patch:
x86 Ubuntu: [http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=)
amd64 Ubuntu: [http://ubuntuforums.org/attachment.php?attachmentid=55770&d=1199848927](http://ubuntuforums.org/attachment.php?attachmentid=55770&d=1199848927)

---

### Post by red_hax0r on 2008-03-15
Thanks, it works great, but now I have another problem: the speakers won't shut off when I plug the headphones in.

---

### Post by red_hax0r on 2008-03-15
Well, I found out that I can manually shut off the speakers using ossxmix, but I wish there was a script for that...

---

### Post by Yellow Pasque on 2008-03-16
I don't have a lot of spare time right now, but perhaps you'll find the scripts here useful:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

