---
title: "Install Ubuntu on a laptop with no CD/DVD reader"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by neuroneo on 2009-03-04
Hi,

I´ve got the following problem:
I have an old laptop (HP omnibook 900) on which I would like to install Ubuntu. I don´t have any cd/dvd reader on it. So I decided to take its harddrive and set it into a 2,5 external usb box.

I connected this external drive on another laptop and started to install ubuntu on the external drive. It works fine, but finally ends up with erasing the MBR and install grub on the internal drive...grrrr

The idea is of course to FULLY install it on the external drive, so that i can then physically mount the drive in the old laptop and start using it, and not to install it as option on an external drive.

How should I proceed???

---

### Post by albandy on 2009-03-04
you can install ubuntu from usb

here explains step by step how to do it:
[http://www.sizlopedia.com/2008/10/31/install-ubuntu-810-usb-flash-drive/](http://www.sizlopedia.com/2008/10/31/install-ubuntu-810-usb-flash-drive/)

---

### Post by neuroneo on 2009-03-04
The BIOS of the laptop is unfortunately too old to boot from the (1.1!!!) USB port...

---

### Post by albandy on 2009-03-04
try installing it with wubi

---

### Post by neuroneo on 2009-03-04
the hard drive does not contain windows anymore (just ubuntu without the loader so that I get the "operating system not found" warning message at startup)...installing now windows on it to be able to run wubi would raise the same problems..

---

### Post by neuroneo on 2009-03-04
or do you mean I should try wubi on the laptop with cd drive and try to install then on the external drive (that would then become the internal drive of the old laptop)? Would I not get then the same boot loading problems?

---

### Post by albandy on 2009-03-04
try this:
sudo grub-install /dev/usbdeviceatached

for example:

sudo grub-install /dev/sdc

---

### Post by neuroneo on 2009-03-04
ok...this in order to install grub on the external usb disk...
I´ll try this this evening. THX

---

### Post by 4leite on 2009-03-04
not sure what your experience with linux is.

you need to find which device the harddrive is. probably it will be automounted to /media/disk (or similar). in a terminal type
```
mount | grep media
```
This will list something similar to:
/dev/sdXN /media/disk .....

the left hand side is the device (drive and partition), the X will be a letter (probably b) and the N will be a number (probably 1). the next value is the mount point (directory).

cd into the directory and check that there is a folder called 'boot' inside it.

Next type:
```
sudo grub-install --root-directory=[mount point] /dev/sdX
```

replace X with the value from above.

If this does not work, you could try editing [mount point]/boot/grub/menu.lst and replace (hdN,N) with (hd0,N)

ie replace the line
root (hd1,0)
with
root (hd0,0)

and then run the above command to reinstall grub.

I hope this works for you.

---

