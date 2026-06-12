---
title: "Ndiswrapper, wireless card problems"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by morningblur on 2006-03-06
Hi everyone, this is my first post on the forums, though i've been a lurker for a good while.

About a week ago, I bought a new Dell laptop (inspiron b120) and it came with a broadcom wireless card. I installed Ubuntu that same day and, after some initial frustration with ndiswrapper, got everything working. (of particular note: i had to compile my own Ndiswrapper and ndiswrapper-utils, i also had to use the graphical front-end, as the command line wasn't working for some reason)

Today I tried changing my kernel to 686, but found that it broke ndiswrapper. I tried reinstalling ndiswrapper, but it still didn't work. So, i eventually gave up and switched back to 386, but found that ndiswrapper no longer worked.  After much frustration i eventually recompiled everything like i had done initially, and everything was working again. No more than half and hour later, while i was surfing the internet on it, the machine froze up, i restarted, thinking nothing of it, and found that ndiswrapper no longer worked again.

I've tried recompiling and uninstalling ndiswrapper many times and the laptop keeps giving me weird problems.  Initially it would allow me to reinstall the driver, but it would say the hardware wasn't present. Then eventually, the command line version would say both were detected (but the connection wouldn't work). Finally, the graphical front-end will no longer respond to my wanting to install the driver, it just locks up the machine as soon as i select the file. 

The wireless card itself has two lights on it, one showing it it connected into the minipci slot, the other showing whether or not it has a wireless signal. The  minipci light is on, but the wireless signal light remains off, from boot-up to desktop.

So, to say the least, i am very confused, and a little frustrated (especially considering how everything was working absolutely fine until today).  

Any advice or help that can be given is greatly appreciated. Also, sorry for the  long-windedness of this post, but i thought some background might help diagnose the problem.

Thanks in advance to anyone that can help me out.

---

### Post by nmsa on 2006-03-07
I have the same problem.
 While connected with a lan cable the network is working
 I run sudo modprobe ndiswrapper and my system sees the wireless card, the signal is at 100% but I can't select none of the networks I have available.
 If I remove the cable and try to enable only the wireless, the system will become frozen and I'll have nothing else to do but to stop the system or remove the battery, nothing works no more.
 A few days ago I managed to get my wireless working, but anytime I reboot my system I have to runt modprobe ndiswrapper which frozen my system.
 I have a Dell Latitude D600 with a Dell Wireless 1450 Dual Band WLAN Mini-PCI (Chipset: BCM4309/BCM2050/BCN2060)

---

### Post by morningblur on 2006-03-07
Well, now my laptop hangs at "Setting up Asla Card 0 ... Ok" too. I'm probably just going to try and reinstall Ubuntu tomorrow, to see if that will fix anything.

So, moving forward on that train of thought... should i try and upgrade it to Dapper, considering how it supports broadcom wireless natively? 

Any suggestions at this point would be greatly appreciated.

---

### Post by nmsa on 2006-03-08
I got the solution from [wiki.ubuntu.ro]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")

edit /etc/modules and add the ndiswrapper line; in my case:
cat /etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
ndiswrapper

morningblur: your Alsa has no problem,
just try another reboot and should be ok (or reboot one+)
I know I did some reboots myself and works.
not sure if this is going to happen again, I'll see and I'll post again here in case of problems, else no news is good news.
let me know :)

I am using Linux since '95 and ubuntu since Warty.
I upgraded to Hoary and was ok (actually I just performed a new install)
Upgrading from Hoary to Breeze, was not a smooth operation in my case and what I have learned is that I have to wait a month or so until apt-get distro upgrading when most problems are solved.
what I do is install new releases in diff partitions or emulators for test purposes, but I don't upgrade a "live" desktop. My suggestion is to wait, try and solve the problems and will work, yet again is your choice :)
Good Luck and Best Regards

---

### Post by roachk71 on 2006-03-08
[LEFT]Hi morningblur,

This appears similar to a problem I had with my new Atheros-based Belkin card. The version of ndiswrapper you have is probably 1.1; you can check that with:

```

dmesg|grep ndis

``` 
The version you're looking for with good Broadcom (and in my case Atheros) support is version 1.10. Check out the two links at the top of my signature; I had to compile a custom kernel *and* the latest stable source for ndiswrapper to get a reliable connection.

Be sure to follow _all_ of the directions carefully, especially when building the new kernel.

Version 1.1 is a rather old build, and is shaky at best with these chipsets. I did manage to get a Linksys WMP11 v2.7 to work flawlessly with it (which has a BCM4301,) but it was still a tad too slow.

It will take between 45 minutes and a few hours to build the kernel, headers and modules. Still, it really is worth the wait for a more efficient system, if you know the options and modules to enable and disable.
[/LEFT]

---

### Post by morningblur on 2006-03-08
Thanks for the help guys, but i think my problem may be the laptop, as now the dang thing won't even boot. I'm assuming my minipci slot burned out too or something, so i'm going to have to contact Dell for a replacement.

I didn't get a chance to try manually adding ndiswrapper, as suggested. So i'm not too sure if it would have worked, but thanks for the suggestion.

And, i was using the current ndiswrapper (1.10), that is how i got it working in the first place. 

Thanks for the suggestions, but this may be a lost cause. We'll have to see.

---

### Post by nmsa on 2006-03-12
very interesting, but this is what I have observed:
I have my Dell Latitude D600 installed with Ubuntu and a small XP partition
I always have to boot first in XP to get the wireless up and then restart pc and boot in Ubuntu. Like this the modules are loaded w/o problems my Broadcom 4309 wireless is recognized and works great. I think is this win wireless very cheap lan device that gets stuck. always when Linux is trying to bring it up.
I have done this 10+ time now and I am sure this is the solution, but can't figure out why nor I have a solution. Lucky I have a XP partition installed.
I shall say my wireless works out of the box, but with a little bit of help.
in conclusion I shall say: Don't buy a Dell as the hardware is not perfect. :-k 
any other ideas?

---

