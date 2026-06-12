---
title: "Here's a challenge for you..."
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by hayden78 on 2009-01-12
Hi. 

I was wondering... could anyone point me in the direction of an idiots guide to insatlling Linux (any distro) on a usb?  I have read a few of these guides, but they all assume I can do things I cannot. 

Here is the problem:

I am having a hard time fdisking my usb. I was told , during fdisk, to make it fat16, so I did this. I also did that flag as bootable thing. Did everything I was told to do. Now I can't figure out how exactly to do everything else. 

I have done the stuff, such as renaming isolinux folder to syslinux, and then changed isolinux.cfg to syslinux.cfg. When I did this before, it brought me to the splash screen (for fedora), now I can't even get that far. The usb won't even boot. 

I can't use UNetbootin, the pc I wish to install to won't boot, the o.s. is all screwed up. thus no connection to net, to use UNetbootin. I also tried my ubuntu 'create usb start up disk', but whenever I attempt to direct it to an .iso, it tells me it is not a desktop iso? I know the iso is not a bad one, as shown by the fact I had gotten to the splash screen before. 


Thank you for reading.

---

### Post by gettinoriginal on 2009-01-12
Well, considering there is no such thing as an idiot using linux, (just less experienced :p)  try this:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by hayden78 on 2009-01-12
AHH! I may FINALLY have it. I hope. 


I went to the website for ubuntu download, downloaded the .iso.. 

I started my usb disk creator... loaded the .iso... and now something is happening that didn't before. It's actually creating it. question is: Will this process allow me to just remove the usb, place it in my other pc, and install?? Something else happened... it gave me an option, on the usb startup disk creator, to format the usb, which it did. 

man, this better work. I have spent more hrs than I care to admit to, considering I am not one to sit at my computer. 

Man, I love this linux stuff, as much of a pain in the **** it is to learn. Better than windows, which does everything for you, crushing your creativity, etc. =D


edit* I noticed a file that is on the usb now, it is a dos/windows exe? Hm.

---

### Post by hayden78 on 2009-01-12
NOOOOOOOOO


I can't believe this, as far as I have gotten.. 

I go to set up Ubuntu, and get told there's not enough room. (Tried to install to a 2 gb usb flash, argh) . Anyway. I try to just install it on my hd, which has NO o.s., and when it gets to the part where it is doing the partition thing, it doesn't list my hd. Any ideas??? I'm guessing my hd needs to be formatted? If so, can't be done , no o.s. :(

---

### Post by aeronotix on 2009-01-12
Okay, you could use a bootable version of Parted Magic or GParted to format the drive in question. 

I prefer Parted Magic but your mileage may vary. The ubuntu installer should detect it and then format itself. There may be an actual problem with the hard drive causing the installer not to pick it up. 

Could you explain more about the problem you have with the hard drive? Like why is the OS all screwed up.

---

### Post by 5BallJuggler on 2009-01-12
Have a read of this:-

I had to go to a 16Gb USB to make a persistance version.

[http://ubuntuforums.org/showthread.php?t=1022708](http://ubuntuforums.org/showthread.php?t=1022708)

Hope it helps

---

