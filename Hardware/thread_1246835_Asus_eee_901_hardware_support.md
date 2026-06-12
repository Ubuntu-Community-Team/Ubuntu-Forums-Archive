---
title: "Asus eee 901 hardware support"
date: 2009-08-22
forum: Hardware
---

### Post by Strange_Movement on 2009-08-22
I have been using my Eee **901** 20GB (please note, **_NOT_** 900, 900A, 904HD or any other 90x series other than **901** 20GB) with standard Jaunty except with the kernel from [array.org]("http://array.org/ubuntu/"). Unfortunately the [array.org]("http://array.org/ubuntu/") kernel never seems to get updated which means that I am now quite a few kernel updates behind the standard Jaunty kernel. I believe the only reason I have to use the [array.org]("http://array.org/ubuntu/") kernel is because the wireless card driver in the standard Jaunty kernel will not work with WPA/WPA2 connections. I would really appreciate it if someone could tell me if the WPA/WPA2 connection problem using the eee **901** standard wireless adapter problem has been fixed in more up to date kernels. In fact any advice on hardware use/changes/configuration/replacement/etc... on the eee **901** would be greatly appreciated.

Thanks in advance.

(please can replies stick only to dealing with the Asus eee **901** as I have found it very confusing looking elsewhere when someone asks about one version of the eee and gets answers regarding virtually all of the eee series. The hardware is different from version to version and I would like to have a thread dealing **_ONLY_** with the **901** hardware)

---

### Post by eltoozero on 2009-08-25
I've got the 901 and I <3 it, that said I know what you're talking about when it comes to getting buttons to work, then using the array kernel, then dealing with weird wifi bugs.

The good news is that no hacks are needed in 9.10 Karmic Koala, everything works out of the box, which is marvelous.

If you cannot wait I seem to recall getting some helpful info from this thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891)

Good luck.

---

### Post by Strange_Movement on 2009-08-29
eltoozero, you are a star ! Thank you for the response with the good news. I'm willing to wait until the official release, but that's fantastic news ! I had been considering a new wireless adapter, but getting decent information on a "good" one that works seems really difficult. I too love my 901 and having standard Ubuntu installed on it (all be it with symlinks to move half of it onto the second SSD).

Thank you, thank you, thank you !
:grin:

---

### Post by eltoozero on 2009-08-29
Cool dude, glad to hear it's been working well for you, but there may be a slightly more elegant way to take advantage of the Dual SSD's:

I have four partitions defined:

4GB SSD:
/dev/sda1 - All but 8MB go to root (/)
/dev/sda2 - 8MB from the end as EFI type for Boot Booster (In Eee BIOS)

16GB SSD:
/dev/sdb1 - All but 2GB for home (/home)
/dev/sdb2 - 2GB from the end as Linux Swap

That way all my user files wind up on the big disk, no symlinks needed, I find that with 2GB ram zero swapping occurs, however swap space is required for hibernation to function.

Good luck out there.

---

### Post by Strange_Movement on 2009-08-30
I couldn't find the 4GB SSD big enough for the system I wanted to have so I have partitions similar to yours, ie:

4GB SSD:
***/dev/sda1*** - All but 8MB go to root (***/***)
***/dev/sda2*** - 8MB from the end as EFI type for Boot Booster (In Eee BIOS)

16GB SSD:
***/dev/sdb1*** - All for home (***/home***)

Both ***/*** and ***/home*** are formatted as ext2 and there is **_NO_** Linux Swap partition to attempt to cut down unnecessary SSD writes and I have never felt the need for hibernation. System logging is also switched off for the same reason.

Then what I do is move the contents and symlink the following folders:

***/usr/share*** => ***/home/.fs-ext/usr/share***
***/var/cache/apt*** => ***/home/.fs-ext/var/cache/apt***

The symlinking causes a minor missing icon on the top panel problem for Firefox everytime Firefox gets an update because of a symlink ***/usr/share/pixmaps/firefox-3.0.png*** that gets messed up from pointing to ***/usr/lib/firefox-3.0.XX/icons/mozicon128.png*** (where **XX** is the new version number), but that's easily enough sorted.

Now I have enough space to install pretty much any applications I want. The only upgrades I really want are 2GB of RAM and one of those faster and larger Runcore SSDs to speed things up a little.

Roll on Karmic though, then no more messing with the separate kernel.

---

### Post by cuby on 2009-09-11
I bought a class 6 SD card (20MB/s) for my eee 901. I've made 2 partitions. One for swap and one normal ext2 partition to install some stand alone programs like eclipse or Jboss (Yeah... the sucker can run jboss with portgres. :) ).

The point is, after booting you can activate the swap on the sd card using:

```
sudo swapon /dev/sdXX 
```
the device is where your swap is.

It cannot hibernate, but I've never needed that because the eee can be several days in suspension :D
This way you can have swap in a disposable card that  you can replace if it is overused.

---

