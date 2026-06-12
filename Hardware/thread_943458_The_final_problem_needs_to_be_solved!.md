---
title: "The final problem needs to be solved!"
date: 2008-10-10
forum: Hardware
---

### Post by pederson on 2008-10-10
Hey everyone!

Okay over the last few days I have been making my transition from Windows XP to Linux Ubuntu. So far, I love it. It's been fun and everything has improved. Even just the simple tasks of getting things 'the way i like it' has been seamless and improved in every aspect. 

However, my final mission to complete the goal of a 'successful' transition to linux is becoming frustrating. It's been hard to get a straight answer to my questions on the net, and it's throwing me in circles. So I've just decided to create my own thread, full with details, hoping for help. 

So here's the problem...

I have a Dell Inspiron 6400. Intel Core Duo T2400 1.8GHZ(?), 2GB RAM, 120GB HDD, ATI Radeon x1400. I want to play World of Warcraft. I've installed WINE, and have installed World of Warcraft. Now what? I've been primarily having problems with what drivers to use, how to get them, how to install them, and then what tweeks do I have to make in order to play WoW effectively?

I hope someone can help! It seems like this problem has been solved, but the maze of forums and links I have to navigate, there's no solid step by step answer on what to do in my particular situation!

Thanks for any help!

---

### Post by Forbees on 2008-10-10
dont get your hopes up, while many people have gotten WoW to work with wine, it's not a garentee . . .apparently wine works better on some computers than others >,<

if no one is able to help you, stick to dual booting ubuntu and XP

i use XP for lightscribe and counterstrike: Sorce

---

### Post by Kinetic_lord on 2008-10-10
have you installed you're video card? Check out my tutorial if not...

---

### Post by pederson on 2008-10-10
> **Forbees said:**
> dont get your hopes up, while many people have gotten WoW to work with wine, it's not a garentee . . .apparently wine works better on some computers than others >,<

if no one is able to help you, stick to dual booting ubuntu and XP

i use XP for lightscribe and counterstrike: Sorce
Installing/Playing WoW isn't a NEED for me. I can live without it, in fact I don't even play anymore, I will only start if I can get this to work. And it would just be a neat accomplishment of a goal I've seem to set for myself.


Basically, if someone could direct me on how to install the ATI catalyst 8.5 drivers, that would be a great start. I can only find out how to install the 8.6 drivers, which apparently don't work very well with WoW.

---

### Post by pederson on 2008-10-10
> **Kinetic_lord said:**
> have you installed you're video card? Check out my tutorial if not...
Envy is, however useless in my situation. "WINE WoW's" have serious graphical glitches/artifacts/etc. with the 8.6 drivers - which are all the current version of Envy offer.

---

### Post by Kinetic_lord on 2008-10-10
Check out the bugs at the Wine database

---

### Post by pederson on 2008-10-10
I'm just asking how I can install the older ATI catalyst 8.5 drivers...

---

### Post by Kinetic_lord on 2008-10-10
So WHY isn't Envy good for that???:|

---

### Post by pederson on 2008-10-10
> **Kinetic_lord said:**
> So WHY isn't Envy good for that???:|
Envy only offers 8.6, I need 8.5.

Or, if there's a way to add 8.5 to the manual install option of Envy, that would work even better.

---

### Post by Kinetic_lord on 2008-10-10
Tell me if this works:

Step 1. Download ati-driver-installer-8-5-x86.x86_64.run
Step 2. sudo apt-get update
Step 4. sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

Step 5. sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/8.04
Step 6. sudo vim /etc/default/linux-restricted-modules-common
in string "DISABLED_MODULES" add “fglrx”
resul: DISABLED_MODULES="fglrx".
save files
Step 7. sudo dpkg -i xorg-driver-fglrx_8.493*.deb fglrx-kernel-source_8.493*.deb fglrx-amdcccle_8.493*.deb
Step 8. Restart X server.
Step 9. Check:
$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X600 Series
OpenGL version string: 2.1.7537 Release

---

### Post by pederson on 2008-10-10
I type...
```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/8.04
```
I get...
```
sh: Can't open ati-driver-installer-8-5-x86.x86_64.run
```

I downloaded ati-driver-installer-8-5-x86.x86_64.run to my desktop, if that matters...

---

### Post by Idefix82 on 2008-10-10
Have you got Ubuntu 64 bit? Otherwise you need to download the 32 bit version of the driver.

Also, check out the strategy games in the Synaptic Package manager. Some of them are really quite good, like FreeCiv and Wesnoth.

---

### Post by pederson on 2008-10-10
haha oops...

Could someone give me the link to the 32bit 8.5 Catacylist drivers and a guide on how to install it..? Doesn't anyone know how to do this?

---

### Post by Idefix82 on 2008-10-10
You can try this:
[http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat85.html]("http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat85.html")

Google is your friend :)

---

### Post by Kinetic_lord on 2008-10-10
btw.. you need to remov ethe old drivers before installing new ones...

---

### Post by Kinetic_lord on 2008-10-10
[http://ubuntuforums.org/showthread.php?p=5937103#post5937103](http://ubuntuforums.org/showthread.php?p=5937103#post5937103)

---

### Post by pederson on 2008-10-10
uh yeah... still having trouble installing... I have no idea how to go about installing (those links wheren't too helpful). I just don't understand why installing this driver is so complicated, why isn't there just a solid guide somewhere? Oh well, maybe there is and I'm just not knowledgable enough.

So I'm trying the stuff Kenetic put up:
```

Step 6. sudo vim /etc/default/linux-restricted-modules-common
in string "DISABLED_MODULES" add “fglrx”
resul: DISABLED_MODULES="fglrx".
**save files**
Step 7. sudo dpkg -i xorg-driver-fglrx_8.493*.deb fglrx-kernel-source_8.493*.deb fglrx-amdcccle_8.493*.deb
Step 8. Restart X server.
Step 9. Check:
$ fglrxinfo
```
I got to the point of disabling those modules, and then is just says 'save files'. What? Is that a command? What does that even mean? That's what I'm talking about, why isn't these a simple, solid guide with explanations? If I figure this out, I'll be writing one... hahah

---

### Post by pederson on 2008-10-10
I may just give up and wait till someone finds a fix for 8.6 (Envy) or Envy updates it's support for older or newer drivers.

---

### Post by markbuntu on 2008-10-11
You can use these instructions, I think the only thing that has changed in them is the driver numbers and the addition of cdbs for 8.8 and above:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Release notes for 8.5

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

I am not sure when, but somewhere along the line the ati drivers adopted DKMS. This makes regression to drivers before DKMS was adopted very very difficult.

---

