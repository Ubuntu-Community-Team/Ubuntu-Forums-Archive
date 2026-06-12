---
title: "restore original touchpad drivers"
date: 2010-05-26
forum: Hardware
---

### Post by arthurccube on 2010-05-26
Hi,

I am using hp mini 210 and since the two fingers scrolling not work, I've followed the following fix:

[http://ubuntuforums.org/showthread.php?t=1388164&page=2](http://ubuntuforums.org/showthread.php?t=1388164&page=2)

However, my touchpad now totally not working!

How can I restore the original mouse drivers?

The following commands make my touch pad failed after reboot

cd drivers/input/mouse
make
sudo make install

---

### Post by dino99 on 2010-05-26
[http://ubuntuforums.org/showpost.php?p=9355623&postcount=52](http://ubuntuforums.org/showpost.php?p=9355623&postcount=52)

sudo dpkg-reconfigure xserver-xorg-input-synaptics

---

### Post by arthurccube on 2010-05-26
Thanks Dino99!

I added the lines to "/usr/lib/X11/xorg.conf.d/10-synaptics.conf" and typed your commands.

Then restart.

But still not working...

---

### Post by arthurccube on 2010-05-27
one more fact:

I only ran the following commands after i apt-get the linux-source ( i haven't run the patch command), how can I rollback it?

cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install

---

