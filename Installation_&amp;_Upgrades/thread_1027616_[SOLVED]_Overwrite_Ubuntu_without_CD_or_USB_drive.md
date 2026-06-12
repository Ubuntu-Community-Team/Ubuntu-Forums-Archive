---
title: "[SOLVED] Overwrite Ubuntu without CD or USB drive?"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by vegetarianshrimp on 2009-01-01
I have the Dell Inspiron Mini 9, and I did this thing that was suggested on Ubuntu Forums to allow me to download i368 applications like Skype. It worked, but it completely messed up my computer. Openoffice.org does not work, updating stuff doesn't work, and I just want to do a fresh install of Ubuntu.

So I right now have a messed up 8.04..1, and I want to install Ubuntu (preferrably 8.10) over the internet (without a CD, DVD, or LiveUSB). 

Is there a way to overwrite my mesed up Ubuntu with the regular default settings one that is on the internet?

Thanks in advance,
vegetarianshrimp

---

### Post by logos34 on 2009-01-01
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> UNetbootin allows for the installation of various Linux/BSD distributions to a partition or USB drive, so it's no different from a standard install, only it doesn't need a CD. It can create a dual-boot install, or replace the existing OS entirely.

...

Features

UNetbootin can **install to your local hard disk** or make a bootable liveUSB drive. It can also load floppy/hard disk images, or kernel/initrds, or (some) ISO (CD image) files, for installing other distributions. 

There's also this method:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

good luck

---

### Post by vegetarianshrimp on 2009-01-01
Thanks. I think I'll use UNetbootin, but before I do anything, do you know how to delete my current OS afterwards, or just overwrite? I'm not sure how to...

---

### Post by logos34 on 2009-01-01
what you'll have to, I believe, is make a small partion just big enough to hold the .iso, then overwrite 8.04 with 8.10 installation...The problem is you need to work from live session (live cd, usb) to shrink / to create new partition, and you say you can't do that.  It would be so much easier if USB was an option for you

---

### Post by vegetarianshrimp on 2009-01-01
Thanks, but that sounds pretty complicated, and I'm just a newbie...can you please tell me how to do that exactly?

p.s. I do have a USB drive, but it's only 2GB. Is that big enough?

---

### Post by logos34 on 2009-01-01
> **vegetarianshrimp said:**
> p.s. I do have a USB drive, but it's only 2GB. Is that big enough?

oh, ok.  yes thats more than enough.  As long as your computer supports booting from USB you can use that option.  So make sure to put the unetbootin installer on the usb, [as illustrated]("http://unetbootin.sourceforge.net/#install") on the unetbootin page

---

### Post by vegetarianshrimp on 2009-01-01
Ok i'll try that, thanks

---

### Post by vegetarianshrimp on 2009-01-01
It worked! Thank you sooooo much!

---

### Post by logos34 on 2009-01-01
no prob.  

enjoy ubuntu and mark as 'Solved' (->thread tools)

---

