---
title: "Gutsy on Gateway Solo 9500"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by sy278 on 2007-11-06
Hi Guys,

I'm a complete linux noob. I am trying to install Gutsy on a Gateway Solo 9500XL

I have an i386 install CD and on boot I initally tried the normal start-up however this resulted in the PC switching itself off, I rebooted and selected the start in safe graphics mode, this time success. Once it completed booting I decided to let it do a full install, it got to about 87% and bang sitch off again.

Now I can't get it to load at all, from either HDD or CD. When booting from CD I am again selecting the safe graphics mode, it gets to a certain point in its boot then switches off again, the last message I see on screen before the switch off is "Loading Hardware drivers..." it switches off before [OK] appears.

Spec is:

384Mb RAM
P3 800MHz

Can anyone help me with this, I'm at a total loss.

Thanks

---

### Post by g2g591 on 2007-11-06
I'd say try the alternate install cd, 384Mb of ram is a bit low for the live cd (the whole system afik gets loaded into it) , but should be fine for normal use, however if you want to try a lighter weight version, try Xubuntu, it has lower system requirements and is ment to be very light.

---

### Post by sy278 on 2007-11-13
Any other suggestions to this as the alternat cd of Ubuntu and Xubuntu have the same issue?

---

### Post by jquigley2 on 2007-11-20
Had the same problem, after messing with it for a few hours, I just let it run, I have 512 meg on the 9500 with 20 gig HD. When I just left it alone it booted and ran just fine. I now have Ubuntu 7.10 on my Solo 9500, but it says I have 2 monitors and shows them on the same screen. It is almost impossible to read. :confused:

---

### Post by dabone on 2008-01-14
Old thread but I had the same problem today with a solo 9500.

To boot I had to take out that old dead battery, or put


noapic nolapic acpi=off 

on your boot parms.

(This was after I installed from text mode on the alt disc 7.10)

after I installed, i used the xorg from this thread and it works well.


[http://ubuntuforums.org/showthread.php?t=322192&highlight=9500+solo](http://ubuntuforums.org/showthread.php?t=322192&highlight=9500+solo)


DRI is enabled!

203.425 fps in glxgears.


Thanks for the help guys, I just had to grab these answers from 2 different threads.


Later,
dabone

---

### Post by sy278 on 2008-03-12
> **sy278 said:**
> Hi Guys,

I'm a complete linux noob. I am trying to install Gutsy on a Gateway Solo 9500XL

I have an i386 install CD and on boot I initally tried the normal start-up however this resulted in the PC switching itself off, I rebooted and selected the start in safe graphics mode, this time success. Once it completed booting I decided to let it do a full install, it got to about 87% and bang sitch off again.

Now I can't get it to load at all, from either HDD or CD. When booting from CD I am again selecting the safe graphics mode, it gets to a certain point in its boot then switches off again, the last message I see on screen before the switch off is "Loading Hardware drivers..." it switches off before [OK] appears.

Spec is:

384Mb RAM
P3 800MHz

Can anyone help me with this, I'm at a total loss.

Thanks

Well guys, I still can't get this to install.

Very very occaisonally it will load to live cd, then the install will run to 86% where it says "loading module ide-cd..." then it switches off.

It does the same in the laternate install version too.

Can anyone help? please?

---

### Post by sy278 on 2008-03-13
Ok, finally got this to install with the alternate CD. However, it now shuts down during boot. Out of about 30 attempts to boot the system has only managed to succesfully load once.

I have tried booting in recovery mode and it is switching off when "loading hardware drivers..." the one time it did successfully boot, the desktop was distorted - it had a kind of tear down the middle of the screen which was actually one edge of the dektop, the rest was shown to the left of the "tear" and repeated to the right.

Does anyone have any more suggestions??

---

### Post by bapper on 2008-03-22
I also have had problems with my Solo 9500. It freezes and shutsdown during boot/init. After some testing and trouble-shooting I did this:
1. removed the battery
2. booted up the xubuntu 7.10
3. Chose 2. Start Ubuntu in safe graphics mode
4. Pressed F6 and removed "splash quiet --" from the command line, pressed enter
5. It booted up just fine... I am currently installing it so I guess I have to reply to my own post if it does not work. But if it works I might not reply.

---

### Post by bapper on 2008-03-22
:( nope that did not work. My solo 9500 shut down at 90% of installation.

---

### Post by scitesy on 2008-04-17
@Bapper
Try [ubuntulite]("http://ubuntulite.tuxfamily.org/") for your machine.  It require the alternate ubuntu CD and then you do a wget for the software packages.  Ubuntulite is designed for old, low power machines.

I use it on my Gateway Solo 9500.  The install is smooth and easy.

The only issue I've had is that sometimes I have to reboot 1-3 times before it makes it to the login.  Once you login all is stable.

Good luck!

---

