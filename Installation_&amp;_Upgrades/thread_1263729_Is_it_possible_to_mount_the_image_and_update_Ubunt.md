---
title: "Is it possible to mount the image and update Ubuntu without making a CD?"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by decay85 on 2009-09-11
I'm currently working on Edgy Eft, and I want to upgrade to the most recent version of Ubuntu. What I'm wondering is if it's possible to mount the downloaded iso image on my computer and re-install it without burning a CD first. I assume it won't work work, but I'm asking, just in case, because for some stupid reason I can't burn an ISO image in Ubuntu atm.

Any help would be most appreciated!

---

### Post by ahbart on 2009-09-11
Well mounting an iso image is easy. I love gmount-iso for that. But I'm not sure if it is possible to upgrade from within a running system.

You could try an upgrade via internet though:
```
update-manager -d
```
But from edgy eft? You could try it, but you'd better make/take an image first, with partimage for example.

---

### Post by jrox717 on 2009-09-11
[http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/](http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/)
Look at the 6th post down. It seems like you have to make a new partition, then copy over all the files on the live cd to that partition, then copy boot and kenel files to /boot/, and finally edit menu.lst. Let us know how it works out, I'd be very interested in this.

---

