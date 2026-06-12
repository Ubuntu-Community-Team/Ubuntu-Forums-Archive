---
title: "Cannot Install any versions of Ubuntu :-("
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by optimistique1 on 2009-04-16
Hi All

I just bought a brand new HP Pavilion DV2-1010ea notebook and couldn't wait to wipe windows off and unstall Ubuntu 9.04.....

But it won't install I am horrified :(:(

It just goes to a black screen when you select install and mentions something about busybox....

Here are the spec and hope someone can help ....

AMD Athlon Neo Processor MV40
(1.60GHz, 512KB cache)
2 GB Memory
320 GB Hard Drive
external optical drive in box
12.1" Screen Size
ATI Radeon HD3410 Graphics Card
512 mb Graphics Memory

PS: I am just using the regular PC Desktop Install CD

---

### Post by baizon on 2009-04-16
Try the "alternate" installation and install the proprietary fglrx driver.

Edit: And check if your Motherboard driver are supported.

---

### Post by optimistique1 on 2009-04-16
Hey thanks for that.  How do I install the fglrx driver?

---

### Post by optimistique1 on 2009-04-16
Sorry to sound dumb but how do I check if my Motherboard driver is supported?

---

### Post by grege on 2009-04-19
I had the same problem with my EeePC. Instead of running the live CD, select install and it should go through.

Jaunty will install the open source ati/radeon driver which will get you started. It supports basic 2d acceleration and xvideo, but no 3d so no compiz effects.

Once you have a running desktop the system will offer to install propriety drivers, so let it do it's thing. If it does not pop up the Hardware Drivers dialog you can install fglrx easily enough through Synaptic.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The fglrx driver is not quite perfect, I prefer to run it without 3d effects as it runs videos in a window in some horrible X11 mode. Without compiz it the videos play in proper xv video. If you are not in the habit of watching videos then the compiz desktop works OK.

Good Luck

---

### Post by spcwingo on 2009-04-19
If that doesn't work you could give the alternate install CD a shot...and if that doesn't work you could give the mini CD a shot (this just takes a wee bit of command line work, but not difficult at all).

---

### Post by optimistique1 on 2009-04-21
Managed to get 9.04 installed with the alternate CD and all seems to be fine, I will now try and install the necessary video drivers so that I can get compiz etc...

One issue I am having is the lack of sound with my IDT High-Definition Audio but I have put another thread in for that....

Hopefully I will get all up and running very soon.:D

---

### Post by richaustin on 2009-04-21
I have had the same problems with my laptops (Compaq and a Samsung something). I found the alternate install 8.04 worked but when I had to re-install it last week, the same CD didn't work! Hmm! Haven't had time to retry tbh.
However, I did find that when it comes up with the "black screen of Death" you can press a combination of Ctrl / Alt and any function key to get to a login window. Ctrl / Alt / F7 gets you to the graphical login where you can, in the bottom left corner, select a session. 
Interestingly XUbuntu worked but refuses to use all of the screen and appears to only allow me to use, I guess, 640 x 480. I did find a fix for this in 8.04 but can't remember what i did!! GRRR!
Jaunty has the same issue but is sooooo slow on the laptops it is no issue anyway.

---

### Post by optimistique1 on 2009-04-22
Tried to install the ATI drivers and this is my response in terminal - 

garry@GARRY:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`

update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
garry@GARRY:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-11-generic/volatile/fglrx.ko': No such file or directory
garry@GARRY:~$


What am I doing wrong?

---

### Post by optimistique1 on 2009-04-22
Tried to install the ATI drivers and this is my response in terminal - 

garry@GARRY:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`

update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
garry@GARRY:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-11-generic/volatile/fglrx.ko': No such file or directory
garry@GARRY:~$


What am I doing wrong?

---

### Post by mtheultimate on 2009-06-08
Did you ever get this resolved? Im having the same problem!

insmod: can't read '/lib/modules/2.6.28-11-generic/volatile/fglrx.ko': No such file or directory

---

### Post by UndeadBob on 2009-08-16
I too cannot understand where this fglrx.ko is supposed to come from:

```

sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

insmod: can't read '/lib/modules/2.6.28-14-generic/volatile/fglrx.ko': No such file or directory

```

---

### Post by presence1960 on 2009-08-16
when you get a blasck screen installing from Live CD you need to hit F4 and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more details.

---

