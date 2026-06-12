---
title: "Cannot Install Ubuntu on Dell"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by landman on 2009-07-14
Hi all,

I have an old[ish] Dell Inspiron 2650 on whcih I wish to install Linux.

Got a copy of Linux Mint 7 yesterday, partioned the HD, rebooted, selected Linux & then nothing other than a rapidly flashing cursor.

So this morning I downloaded Ubuntu 9.04 - did the checksum thing - loaded the CD & rebooted.  Instructed the disk to load Ubuntu & then got the same result as before, just a rapidly binking cursor.

I am intending to get rid of Windoze as the HD is only 20 GB.

Am I being thick & not typing in some mystical command, or is there a reason why Linux will not load.

The Laptop is a 1.7 gHz model with 512 k of RAM and claims to be running on an Intel i845 chipset [with ECC disabled].

Help & advice much appreciated.

Landman

---

### Post by JohnnySage50307 on 2009-07-14
It could be that your graphics processor drivers are not supported.  I've had issues like that with Redhat when I tried installing it on my Compaq, but when I installed Ubuntu, everything worked beautifully.

---

### Post by xinilux on 2009-07-23
Ubuntu, by default, uses a package called "compiz" which does not play nice with the Intel graphics driver. I have an Intel i845GV chip on a Gigabyte 8i845GVM-RZ motherboard and had to follow this procedure to install Ubuntu 8.10 (Intrepid Ibex.)

Boot with the install disk

Hit F4 and choose "safe video mode". 
This uses the VESA driver instead of the Intel.
Hit ESC to return to the main install menu.

Choose to install

After the installation completes, open a terminal and run the following:

```
$ sudo apt-get remove compiz-core compiz

$ sudo cp -iv /boot/grub/menu.lst /boot/grub/menu.lst_original

$ sudo gedit /boot/grub/menu.lst
       Remove all of the "xforcevesa" from the
       ### BEGIN AUTOMAGIC KERNELS LIST section
       except in the recovery mode kernel section

$ sudo cp -iv /etc/X11/xorg.conf /etc/X11/xorg.conf_original

$ sudo gedit /etc/X11/xorg.conf
        change the "Driver"  vesa  entry to 
        "Driver" intel

```

Reboot and hopefully there will be Joy.

Removing the "xforcevesa" from the kernel boot options stops the kernel from automatically using the VESA driver and instead the Intel drivers will be used. I suspect that option is inserted by the installation process when you chose the safe video mode option.

There may well be better approaches to this problem, but this has worked for me.

---

### Post by all_gears on 2009-07-23
what xinilux is suggesting is a good idea. if that fails, you could also try using puppy linux. i've had the same problem on one of my PCs and for some mysterious reason, puppy was the only thing that would give me a desktop (for a while, until ubuntu 8.04).

---

### Post by LADmaticCA on 2009-07-23
Wait, are you saying booting from the install disk is not working? I've read a faulty harddrive or one with a corrupt MBR can produce a black screen with blinking cursor. Might want to check the harddrive.

---

