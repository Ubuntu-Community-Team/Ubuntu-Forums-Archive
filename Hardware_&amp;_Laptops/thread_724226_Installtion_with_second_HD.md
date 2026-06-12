---
title: "Installtion with second HD"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by PremiumPete83 on 2008-03-14
I currently have my main disk setup as a SATA which is currently the main drive with Vista installed.  I want to install Ubuntu on a second partition which is connected by a PCI IDE controller card (High Point Rocket 133SB).  But, when I get to step 7 on the installation, my drive shows up but only 253 MB of the entire 80G drive is free.

Windows shows the drive as 80G of space. 

Is there anything that can be done to help Ubuntu pick it up?

---

### Post by taurus on 2008-03-14
While you are still in LiveCD, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

---

### Post by PremiumPete83 on 2008-03-14
Doesn't show up..

---

### Post by PremiumPete83 on 2008-03-14
gpartition shows it as being 200MB

---

### Post by PremiumPete83 on 2008-03-17
I believe I need to install the drivers from High Point but when I try I get compilation errors..

I tried adding a third hard disk to see if Ubuntu would recognize it but it didn't, so it seems as if the issue is with the controller card and not the disks themselves.

---

