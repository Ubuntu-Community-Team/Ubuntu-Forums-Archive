---
title: "Virtual Box USB HELP!!"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by TranceGodJosh on 2009-05-05
Hey,

Could someone tell me how to install WindowsXP on virtual box and the windows installation setup is on a USB Stick. Just to let you know, my acer aspire one does not have a CD/DVD-ROM Drive.

Cheers.

---

### Post by Sacriom on 2009-05-05
If it's the case, you could try to remove the iso from the usb, and just mount the iso in the virtualbox. 
There's an isue trying to load usb on the virtualbox OSE, if you don't want to get into deeper troubles, i recommend you to just mount the iso from the program. 
Later you can fix the usb iso, once you have windows xp =).

---

### Post by albinootje on 2009-05-05
> **TranceGodJosh said:**
>  Could someone tell me how to install WindowsXP on virtual box and the windows installation setup is on a USB Stick.

You can create an iso image from your usb stick, for example like this in a terminal :
```

genisoimage -o install.iso /media/disk

```
Make sure that the package genisoimage is installed.
After creating the iso image you can use it as a cdrom image inside VirtualBox.

---

### Post by TranceGodJosh on 2009-05-05
Cheers guys.

---

### Post by TranceGodJosh on 2009-05-06
How will i come about mounting the iso in the virtual box, i have installed Gmount-iso but im not sure what to do.

cheers.

---

### Post by albinootje on 2009-05-06
> **TranceGodJosh said:**
> How will i come about mounting the iso in the virtual box, i have installed Gmount-iso but im not sure what to do.


Add the iso image inside VirtualBox in the Guest VM section.
See attached screenshot.

---

