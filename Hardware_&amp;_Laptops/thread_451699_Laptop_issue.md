---
title: "Laptop issue"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by avidreader on 2007-05-22
I have installed Feisty on a Fujitsu Lifebook C, about 3 years old. Video is ATI Radeon M340.
No problems except the screen won't recover after suspend. Goes into suspend just fine. 
I have tried all below, and mixed and matched all of these changes:

adding noapic nolapic to end of #kopt in /boot/grub/menu.lst
adding #nonaloption+quite splash resume=/dev/hda ---my swap drive to same file
adding option "no accel" to video device section of /etc/X11/xorg.conf file
changing Post_Video=true to false in /etc/default/acpi-support
changing Save_VBE_state to both true and false in same file
changing Use_DPM to both true and false in same file
changing mem to standby in same file
adding VBRestore to option section of xorg.conf file in same section as above

All without luck. The machine goes into standby, but does not recover screen. I have to hold power button to restart. 
I have not tried hibernate, don't need it. I have run out of things to try, so thought I would ask here. 
Thanks in advance.

---

### Post by Kobalt on 2007-05-22
I believe it's a driver problem... I think you need to use the [radeon drivers]("https://help.ubuntu.com/community/RadeonDriver") here.

---

### Post by avidreader on 2007-05-25
Thanks - I am running that driver. I tried Envy and it says my card isn't supported. 
I guess I will live with things the way they are or put this OS on another computer.

---

### Post by EXCiD3 on 2007-05-25
> **avidreader said:**
> I guess I will live with things the way they are or put this OS on another computer.


Ouch, :( I hope that you dont give up on Ubuntu just yet...

---

### Post by avidreader on 2007-05-25
Not yet - might try Edgy. From the posts that seems to work better with ATI video and power management. But I can see how many people would not put in the time and effort when Windows is everywhere. Hard to get away from it no matter how much we want to. Will keep on trying.

---

