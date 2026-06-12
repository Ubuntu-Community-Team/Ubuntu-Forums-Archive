---
title: "Ubuntu on a HP Mini 110-1125NR"
date: 2009-12-01
forum: Hardware
---

### Post by iHax on 2009-12-01
Will Ubuntu run properly out of the box on a HP Mini 110-1125NR?

Can someone give me some information on installing Ubuntu on a HP 110-1125NR?

Thanks.

---

### Post by mörgæs on 2009-12-01
A quick start is to give it a live CD and see how it works, plain and simple.

---

### Post by iHax on 2009-12-01
Okay. Thanks.

---

### Post by beloved88 on 2009-12-01
I have an HP Mini 1101, which is pretty much the same as i understand, except that i got mine off the HP Business website because of the features it had.&#8203;&#8203;I installed Easy Peasy, and it was pretty much easy, but i turned of Maximus window manager because i didn't like that so much.  Everything except for wireless worked out of the box, which was a simple fix to download and intstall the correct drivers from broadcom, although your hardware could be different.  since there is no optical drive, you'll either have to use an external drive to use a CD or us a program to make a live usb disk.  The one that worked for me was imagewriter, for some reason usb startup disk creator didn't work at all.  I pretty much love it as is right now!

---

### Post by Agent1134 on 2010-01-15
I got the HP Mini 110-1125NR last week. Currently running 9.10 UNR with 2GB Ram. It ran flawless on installation. No complaints as far as OS is concerned... But, I wish I would have gotten another EeePC instead. The mouse buttons are separated on the sides of the track pad. VERY ANNOYING. You can't really do the "One handed click & drag/scroll" with the thumb and index finger. I know this may sound minuscule, but it really is a product breaker. Also, if you're a hater of the "tumor batteries" I suggest buying a smaller 3 cell, or getting another netbook. This one comes with a 6 cell... but it's setup to elevate the netbook. Good for keeping everything cool underneath. But, the "L" shape of the netbook makes it tough for putting into a netbook bag or sleeve. I got a 10" incase neoprene sleeve for it but it doesn't fit due to the awkward battery. So, I took my girlfriends Case Logic E-Sling and tried that. No luck unless you remove the battery. This is my 3rd HP computer and I am becoming more disappointed with them after every product I purchase.

I suggest getting an Asus EeePC, or the Samsung GO N310 series. 
Asus makes a great machine for a great price. I got the Samsung GO N310-13GMB for my girlfriend for Christmas and I wish I could get her to trade for this HP. It's currently running 9.04 UNR flawlessly. Had one minor issue with the wireless driver on installation. It would begin installing the driver, then just stop. So, I force installed in Terminal and it did the trick.

---

### Post by rasmith3530 on 2010-02-24
I loaded Karmic Live on my HP Mini 110-1125NR, and it ran, sans WiFi. Unfortunately, when I went to try an install, it died out right about where the partitioner begins. The screen just went black, and both hard drive and CD activity stopped. I'll have to try a thumb drive routine. This was using an official, Canonical-supplied, Ubuntu CD.

The machine is currently stock, although I do plan to up the RAM to 2GB tomorrow.

---

### Post by spectralblue on 2010-02-26
Works like a charm I tried UNR but did not like it at all, because I  wanted to manage my windows myself. I had the desktop edition instead, and rearranged the panels a bit (see attachment - the upper right is the main gnome menu instead of the menu bar).

You'll have to do a few steps to get this baby to run properly, but they're pretty easy.

Next, step: Get the internet working!

In the Live CD environment, you can activate the internet simply by going to System>Adminstration>Hardware Drivers and activate the Broadcom STA driver and reboot. However, after you install ubuntu to your harddisk, it won't install it by default.

I recommend connecting your netbook via ethernet cable and go to the terminal (Accessories>Terminal)

> sudo apt-get update
sudo apt-get install bcmwl-kernel-source

Then go to System>Adminstration>Hardware Drivers and activate the Broadcom  STA driver and reboot. If it says something like "This driver is activated but not in use" click on Remove to disable the driver and reboot, and then activate it again and then reboot AGAIN! It should work after that. 

Once wifi works, you'll want to update your system. On the terminal type:

> sudo apt-get upgrade

If you don't have an ethernet cable, download the following package from another machine (or OS) and run it in ubuntu:

> [http://archive.ubuntulinux.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu2_i386.deb](http://archive.ubuntulinux.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu2_i386.deb)

I have not tried this though to see if it works. 


Next, to get the audio working go here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)

> Confirmed this works on Karmic, kernel  2.6.31-14, does NOT WORK for 2.6.31-19, using Hp Mini 110.
 If kernel 2.6.31-14 does not appear in your boot menu, install it via  synaptic. Search for  install linux-image-2.6.31-14-generic.
 Next
 - install linux-backports-modules-alsa-karmic-generic
- reboot
- open a terminal, enter "alsamixer", press "tab", and set both internal  and front mic sliders to 100%
- press "esc"
 Wifi not working?
 Make sure bcmwl-kernel-source is installed (check in synaptic). Next  go to System>Administration>Hardware Drivers. If  Broadcom STA is activated, it will probably say "The driver is activated  but not currently in use." Disable the driver, then reboot. After  reboot, enable the driver, then reboot AGAIN. Your wifi should work now!
 Thanks ke4jgx and Franz!

        



To get the module you have to enable the following repository in synaptic:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main universe multiverse restricted

You can get instructions for that here: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)



TIP: Set your workspaces to at least 2 Rows. Some applications will go beyond the vertical resolution of the screen, and some of these applications do not have scroll bars, so you won't have access to the buttons for example. If you have a workspace at the bottom, all you need to do is switch to it to access other parts of the window.

---

