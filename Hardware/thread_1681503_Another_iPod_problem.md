---
title: "Another iPod problem"
date: 2011-02-04
forum: Hardware
---

### Post by Kexolino on 2011-02-04
The model is Nano 3rd gen, 4GB, silver...
If I plug it in, it shows the Connected screen and all that, but it doesn't appear in the places menu, gtkpod or Rhythmbox.

When I was using Lucid, it was working perfectly for two or three months, then it started going crazy.. Every time I plugged it in gtkpod saw it as a new one (so I had like 7 iPods at the time :D), I couldn't put music on it, but I could copy the music already on it to the computer... Maverick doesn't even detect it when I use Gnome. 

When I use KDE though, it detects it, and I can browse the folders. Amarok sees it too, and wants to initialize it, but it can't. I think there might be some permission problem, because it says "owner: root", but I don't really know...

It works fine on Windows, but the machine I tried it on didn't have iTunes, so I couldn't try that...

---

### Post by snowstorm167 on 2011-02-04
I have found that rythem box has great support for ipods as I load my 160 gig classic.I have tested it on each version of ubuntu since 7.10 all the way to 10.10      it also worked on kubuntu 7.4       i bought my ipod last summer

maybe it the same issue with the x-box 360 and ipods


the nanos and touches have to be connected to the net for them to work on the 360 the rest of the ipods work right out of the box

---

### Post by Kexolino on 2011-02-04
I don't know about the other ones, but a nano 3g can't be connected to the internet, as far as I know. But even if it could, Ubuntu doesn't see it (at least in gnome), so I can't do anything with it..

---

### Post by Kexolino on 2011-02-04
I was told to run ```
sudo fdisk -l
``` (but then I didn't get a reply), and I got this (I'll just paste the iPod part):

```
Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         596     3800580    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(59, 37, 42) logical=(595, 13, 42)
Partition 1 does not start on physical sector boundary.

```Does this help, or mean anything? I'm asking because I didn't get that reply, and I think that this might reveal the problem or something (well not to me unfortunately)...

---

### Post by Kexolino on 2011-02-05
I got iTunes 7.6 to work with wine, but that doesn't see it either. I really have no ideas here. Maybe I'll try to install Windows in Virtualbox, and try it there...

---

### Post by Kexolino on 2011-02-05
Well, here's how it was: I just couldn't get XP (in VirtualBox) to recognize any USB device (yes, I searched for a solution for hours). By this time I was f****** mad, so I installed iTunes on a Windows notebook and restored the damn thing. 

The only thing I can say is: DON'T BUY AN IPOD!!

---

