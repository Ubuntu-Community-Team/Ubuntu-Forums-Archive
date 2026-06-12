---
title: "Installing Ubuntu8 onto a flash drive?"
date: 2008-09-20
forum: General Help
---

### Post by mousington on 2008-09-20
Hey everyone. I'm really new to the whole Linux thing, but so far I'm loving it. I've been running it off a Live CD for a while, and now am attempting to install Ubuntu onto a flash drive. I've been following the directions on [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)  but when I get to step 16 (cp -rfv casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu8) I am told "/media/ubuntu8 is not a directory"

Could someone please help. That would be so great. Thanks in advance guys.

---

### Post by RequinB4 on 2008-09-20
The problem is that when you re-inserted your flash drive it wasn't called "ubuntu8" in /media/ it was called something else.

What is the output of ```
mount | grep /dev/sd**_x_**
```

where x is the number you've been using so far in the tutorial

AND what is the output of 

```

cd /media/
ls

```

Edit:  Apparently its simpler than this.  I have little experience otherwise with booting from a flash drive.

---

### Post by mousington on 2008-09-20
Thanks for the quick reply. I realized I didn't take out and re-insert the flash drive. But now that I've done that, and I've completed all the steps it still didn't boot up. When I attempt to boot up from the flash drive it just takes me to a black screen with a blinking cursor at the top left corner. I tried to do the suggested note at the bottom of the instructions, but it says permission denied. Any ideas on what I can do?

---

