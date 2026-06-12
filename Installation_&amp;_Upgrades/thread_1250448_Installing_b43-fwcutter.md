---
title: "Installing b43-fwcutter"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Jordii on 2009-08-26
I just tried to use wubi on my usb. (1gb) I used Unetbootin for this.
I haven't install Ubuntu yet. When I try to install b43-fwcutter I get the following message:
**E: b43-fwcutter: subprocess post-installation script returned error exit status 1**
 
Hmm, now I check my settings for Synaptic. The CD option was checked (I used the CD before but when I try to install from it, I get the erno 5 error or something, so I use the usb for now.
 
I unchecked the CD option, but the b43-fwcutter package still exists, and I get the same error.

---

### Post by Jordii on 2009-08-27
Anyone?

---

### Post by aitjcize on 2009-08-27
goto system -> admin -> hardware driver
or type jocky-gtk in the terminal

after updating
check the driver broadcom b43 wireless driver
and it will do everything for you.

good luck

---

### Post by Jordii on 2009-08-27
I went to the hardware driver place, clicked on activate for the broadcom b43 wireless driver. Then everything seems fine, after 100% the window closes but nothing changed. It's still not activated :S

---

### Post by aitjcize on 2009-08-27
You must restart your computer..
if you are using something like live-cd... it may not work

perhaps you can [customize the live cd image]("https://help.ubuntu.com/community/LiveCDCustomization") to make it work...

---

### Post by Jordii on 2009-08-27
I currently use the usb.. and I tried to restard but it's still not activated. But I'm gonna try to use the customized iso for my usb
if that doesn't work, I'll install everything. (If I don't get the same error as with installing from the cd -__-)

---

### Post by Jordii on 2009-08-27
I just found a special usb iso at the ubuntu releases

---

