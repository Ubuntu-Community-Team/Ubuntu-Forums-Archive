---
title: "nVidia 9500M GS driver"
date: 2008-05-06
forum: Hardware
---

### Post by Burkey on 2008-05-06
Hi, I have been using Hardy for a few weeks now and am very happy with it.  I do my development as well as play World of Warcraft on it with no hassles.  Thank you.


I have an nVidia 9500M GS graphics card in it and was told the newer beta 171.06 driver from nVidia would properly support this and run faster than the 169.12 driver Ubuntu provides.

Has anyone got any experience or advice on this?  I could try to muddle my way through installing it (unless someone has a link to a Hardy guide..) but that means I will have to update it every kernel upgrade wont I?

So please anyone with a 9 series card, can you please reply with some info for me.

---

### Post by fain on 2008-05-06
Yes you will have to upgrade the driver with every kernel upgrade but in gutsy and feisty this didn't happen too often. Its easy to install really. you just need your kernels source and the nvidia sh package from their website then drop down in a terminal by

(ctrl-alt-f1)
 
then stop gnome by
```
sudo /etc/init.d/gdm stop
```
then run the package by 
```
./nvidia*****.sh
``` 
(replace stars with file name of course) from the directory the package is in. You might have to 
```
chmod +x nvidia*****.sh
``` If the file doesn't execute properly.

Or you can get envy and it should do it all for you. 
edit:I just thought of something. I don't think envy will get beta drivers, Not really sure though.
I prefer the manual way.

And sorry I don't own a 9500m but i plan on owning one in the near future

---

### Post by Burkey on 2008-05-06
Thanks for the reply.  I might bite the bullet and give it a shot.  If it can push my card a little faster would be great.

btw. I notice you have an Asus PC (mobo+vid) my Pc is an Asus laptop, M51 woth everything (even blueray) and it pwns.

---

### Post by fain on 2008-05-06
> **Burkey said:**
> Thanks for the reply.  I might bite the bullet and give it a shot.  If it can push my card a little faster would be great.

btw. I notice you have an Asus PC (mobo+vid) my Pc is an Asus laptop, M51 woth everything (even blueray) and it pwns.
ya asus is good :) thats the laptop i was planning on getting actually.

---

### Post by Burkey on 2008-05-06
Installing.. this is how I got it going:

Downloaded NVIDIA-Linux-x86-171.06-pkg1.run

switch tty1 (ctrl+alt+F1) and stopped X (sudo /etc/init.d/gdm stop)

Edit /etc/default/linux-restricted-modules-common
and add DISABLED_MODULES="nv nvidia_new"

I then deleted:
/lib/linux-restricted-modules/.nvidia_new_installed
/etc/init.d/nvidia-kernel

then run the installer (sudo ./NVIDIA-Linux-x86-171.06-pkg1.run)

*reboot*

Gnome come up, logged in and verified it is loaded with glxinfo

this is a somewhat messy transcript and may not be perfect for everyone but if I get some replies I will come back and redo it or start a new thread with it all formatted and a bit mroe readable.

---

### Post by simon_w on 2008-05-15
@Burkey:

Hi - what has your experience been with the newer (beta) drivers?  Is it worth the fuss, and the maintenance if/when kernel upgrades occur?

Also, will the newer drivers be available via the update manager or the restricted drivers manager once they graduate from 'beta' status?

Thanks for this thread!

Simon

---

