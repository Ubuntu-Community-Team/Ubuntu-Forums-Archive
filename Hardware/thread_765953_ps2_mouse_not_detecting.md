---
title: "ps/2 mouse not detecting"
date: 2008-04-24
forum: Hardware
---

### Post by masticate on 2008-04-24
Hi all,

I just installed Ubuntu 8.04 and it won't detect my ps/2 mouse. But it detects the USB mouse fine. Ubuntu 7.10 detects both the mice fine.


Has anybody else run into a similar problem with ps/2 mouse? Or any hints?

I tried to determine if the kernel even detects the mouse. The following does NOT display data for the ps/2 mouse:
> 
sudo cat /dev/psaux
sudo cat /dev/input/mouse0
sudo cat /dev/input/mice
sudo cat /dev/ttyS0
sudo cat /dev/ttys0
sudo cat /dev/ttys1
sudo cat /dev/ttyS1


The following displays data for the USB mouse
> 
sudo cat /dev/psaux
sudo cat /dev/input/mouse1
sudo cat /dev/input/mice



My relevant portion of the xorg.conf :
> 
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection



---

### Post by carleton on 2008-08-08
having same problem, any help appreciated

---

