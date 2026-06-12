---
title: "External Hard Disk Installation Error"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by freddiespagheti on 2009-08-24
This has happened with two different OS's and I'm not sure why. I installed ubuntu to an external HDD and it boots up fine on my netbook, however it didn't work with my other, larger, laptop. So instead, I tried installing through the larger one and got the same error.

Both times the installation is successful but upon booting up after the loading screen it presents this error. 

Here are two pictures of it:

[URL="http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2080.jpg"]http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2080.jpg
[/URL][URL="http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2081.jpg"]
http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2081.jpg[/URL]

The computer with the error is an Acer with Vista on it. 
-AMD 64 processor
-2GB RAM

I'm not sure what other specs will be helpful, so please ask.

Thanks.

---

### Post by lfb on 2009-08-25
I'm getting almost the exact same error trying to boot from my external.  What do you get when you ```
cat /proc/cmdline
``` and explore the directories in /dev?

---

### Post by freddiespagheti on 2009-08-25
```

(initramfs) cat /dev/cmdline
cat: can't open '/dev/cmdline': No such file or directory

```I can't get the entire out put of **ls /dev **because there's too much and I can't scroll the screen.
Here's what I can give you though:

[http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2087.jpg](http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2087.jpg) 
[URL="http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2086.jpg"]
http://i647.photobucket.com/albums/uu195/freddiespagheti/DSCN2086.jpg[/URL]


I know it's not very legible, but it's the best I've got right now.

---

### Post by freddiespagheti on 2009-08-25
OK, new problem, and I need some help badly and ASAP

I was also having a problem with loading Windows without the external HDD attached. I didn't mention it though because I had read about it and seeing it was a common problem, I figured I could take care of it.

So I tried to do so by putting Super Grub Disk on a flash drive with unetbootin. My internet connection wasn't working well so instead of downloading through unetbootin I got ithe ISO separately on another computer and used that. 

It finished and I booted the laptop with the flash drive but when the unetbootin menu loaded, no matter which of the several options I chose, nothing happened.

So I rebooted and chose the internal hdd and now it's giving me a grub error 17 whether the external drive is connected or not.

I can't boot into anything now and it's actually my brother's computer which he needs. I'm leaving town for a number of months tomorrow and he won't be able to fix this. 

I can't leave him with an unbootable computer, please help out if you can.


EDIT:
Sorry for the alarm,

I managed to put Super Grub Disk on a CD by ways of a separate computer. It worked so I then just deleted GRUB and things are normal.

The original problem is still present though: Ubuntu won't finish loading on that computer.

---

### Post by dstew on 2009-08-25
The original error seems to be that the root device specified in the kernel line of the menu.lst file does not exist, or that the UUID is not correct.

You can edit the kernel line by using the grub edit function. If you think that /dev/sdb1 is the correct root file file system, you can use this as the argument for the root designation in the kernel line instead of the UUID, and see if it works. To edit the kernel line, in the grub menu, press 'e' for edit. Use the up-down keys to highlight the kernel line, press 'e' again to edit it. Take out the UUID, and put in just /dev/sdb1. Hit return to save the edit, then 'b' to boot.

You can also boot a Live CD, and check the UUID of the partition in question using the command```
vol_id -u /dev/sdb1
```

---

### Post by freddiespagheti on 2009-08-25
> **dstew said:**
> The original error seems to be that the root device specified in the kernel line of the menu.lst file does not exist, or that the UUID is not correct.

You can edit the kernel line by using the grub edit function. If you think that /dev/sdb1 is the correct root file file system, you can use this as the argument for the root designation in the kernel line instead of the UUID, and see if it works. To edit the kernel line, in the grub menu, press 'e' for edit. Use the up-down keys to highlight the kernel line, press 'e' again to edit it. Take out the UUID, and put in just /dev/sdb1. Hit return to save the edit, then 'b' to boot.

You can also boot a Live CD, and check the UUID of the partition in question using the command```
vol_id -u /dev/sdb1
```

Replacing the UUID with /dev/sdb1 doesn't seem to change anything. It still boots the same way:
It shows the Ubuntu logo with the scrolling loading bar and then gives the errors presented earlier.

typing in ```
vol_id -u /dev/sdb1
``` on a live cd simply gave:
```
/dev/sdb1: error opening volume
```

I'm kind of lost...

---

### Post by dsimages on 2009-08-25
Well for your initial problem. There is a bug in the booting process that is beyond me but i did figure out that if you unplug/re-plug the external hd while at the splash screen of booting, it will boot up.

your second problem.. Boot from a live cd, search for ms-sys, download it and install it. do a quick search on the web on how to run the ms-sys. (i forgot already, sorry)
That will correct the mbr on your brothers laptop and will boot correctly to windows. You will run the ms-sys through a terminal of  the live cd.

Sorry i could be of much help.. good luck

---

### Post by dstew on 2009-08-26
It is possible that the file system on the hard disk is corrupt. Can you mount it to the Live CD system, and see files?

---

### Post by freddiespagheti on 2009-08-26
> Well for your initial problem. There is a bug in the booting process that is beyond me but i did figure out that if you unplug/re-plug the external hd while at the splash screen of booting, it will boot up.

your second problem.. Boot from a live cd, search for ms-sys, download it and install it. do a quick search on the web on how to run the ms-sys. (i forgot already, sorry)
That will correct the mbr on your brothers laptop and will boot correctly to windows. You will run the ms-sys through a terminal of the live cd.

Sorry i could be of much help.. good luck     Your first solution has worked perfectly, thank you very much. I must admit, that is a strange bug.

As for the second solution, I already got the mbr fixed with a Super Grub Disk so it should be fine.

> **dstew said:**
> It is possible that the file system on the hard disk is corrupt. Can you mount it to the Live CD system, and see files?

No, it's not. It can be mounted without a problem and thanks to the above it loads just fine.


Thanks everyone.

---

### Post by dsimages on 2009-08-27
what errors or messages are you getting when trying to boot the external hd on a larger (non-netbook) system.

I should boot up fine (with our unplug/re-plug fix).

---

### Post by freddiespagheti on 2009-08-27
> what errors or messages are you getting when trying to boot the external hd on a larger (non-netbook) system.

I should boot up fine (with our unplug/re-plug fix). 	

I can't give anything more than I already have because I'm back in DC (as opposed to Florida where I was). The funny thing, though, is that it could boot fine on my netbook but **not** my brother's laptop.

---

