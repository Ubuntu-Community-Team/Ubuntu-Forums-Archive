---
title: "Grub2 blew up my Jaunty"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by rjackson1969 on 2009-10-26
Installed Grub2 on my HP mini and now when my grub boot loader comes up it says "Chainload into GRUB 2"

When I hit enter I get-
[INDENT]Error 11: Unrecognized device string

Press any key to continue...
[/INDENT]Go back to Grub menu try to choose ANY Debian kernal to boot from and I get the same-
[INDENT]Error 11: Unrecognized device string
  
Press any key to continue...
[/INDENT]I choose C to get a command line and no matter what I put in the command line I get-

[INDENT]Error 27: Unrecognized command
[/INDENT]Therefore I decided to reinstall ubuntu netbook remix off a live thumb drive because netbooks do not have ROM drives. I tell my boot order to go from my thumb drive and it skips and instead goes back into the grub2 bootloader that I can do nothing with except boot into my windows XP.

I'd really like to get my mini back into working order with Ubuntu netbook remix if anybody has any idea what to do with this seemingly circular flaw.

Thanks in advance.

---

### Post by wilee-nilee on 2009-10-26
So your hitting f12 or whatever the key is to boot from the usb, it seems that you are from the description.

---

### Post by QIII on 2009-10-26
When you hit enter at "Chainload into GRUB 2", it should land on a line that says something like

```
root (some long UUID)
```Press "e" to edit, and replace "root" with "uuid" and press enter.  Select the uuid entry you just edited and press "b" to boot.

Open a terminal and finish the upgrade to GRUB2 by 

```
sudo upgrade-from-grub-legacy
```You will get a series of messages.  It may take a few minutes.

When it is done, type 

```
sudo reboot
```If you are running a dual boot system then you can update GRUB2 after you have gotten back into Karmic by:

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```

---

### Post by rjackson1969 on 2009-10-26
> **wilee-nilee said:**
> So your hitting f12 or whatever the key is to boot from the usb, it seems that you are from the description.

Yes. I hit my F9 key which takes me to a menu of where to boot and it gives me the option of harddrive or my USB. I choose USB and it still goes to the Grub 2 menu. I'd just like to wipe all of the Grub and ubuntu install and install again.

I'm currently running Ubuntu Jaunty and want to install Karmic beta that I have as a live image on my thumb drive.

---

### Post by rjackson1969 on 2009-10-26
> **QIII said:**
> When you hit enter at "Chainload into GRUB 2", it should land on a line that says something like

```
root (some long UUID)
```Press "e" to edit, and replace "root" with "uuid" and press enter.  Select the uuid entry you just edited and press "b" to boot.

Open a terminal and finish the upgrade to GRUB2 by 

```
sudo upgrade-from-grub-legacy
```You will get a series of messages.  It may take a few minutes.

When it is done, type 

```
sudo reboot
```If you are running a dual boot system then you can update GRUB2 after you have gotten back into Karmic by:

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```


QIII

Spot on! Thanks for the babysitting on this. Got booted into my Jaunty and my grub is working.

Now I'm going to try to over-write my jaunty by installing Karmic in its place and play around.

:*crosses fingers for compatiblity with idiot broadcom drivers on network card*:

---

### Post by rjackson1969 on 2009-10-26
one big problem remaining apparently. GRUB 2 has preempted my bios. I can go into my bios and change my boot order and all to boot off my USB first but it pretty much ignores that and goes into GRUB. So I can't install any image from a live USB.

Any way to regain control of my boot order so I can install OS' from my thumb drive?

I haven't had a chance to do the update grub2 portion of your instructions. I'm currently at work and don't have access to internet for personal hookup. Would this update then allow me to take command of my boot order again?

---

