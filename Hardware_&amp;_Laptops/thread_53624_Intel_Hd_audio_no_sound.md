---
title: "Intel Hd audio no sound"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by Might on 2005-08-01
Hi im using Intel 82801FB ICH6 high audio and after windows reinstall no sound.I start play game and it says: cannot find audio card installed.So what drivers i need can someone give me link?




SORRY FOR MY BAD ENGLISH!THX.

---

### Post by varunus on 2005-08-02
I'm going to assume by the above that Warty isn't making sound, not windows.  Here is not the place to ask windows questions.

Here's a guide on how to install HDA intel sound drivers in Hoary, not sure if it'll work in Warty.  I'd recommend upgrading.
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

---

### Post by Might on 2005-08-02
OK i downladed driver, library, oss, and utils. Now i going to extraxt driver and how to install it?
(The # means you should do this as root, so either use the root-console or "$ sudo su -") 

# apt-get install alsa-source 

i dont no its not exe file.Explain to me please

---

### Post by varunus on 2005-08-02
OK.  Don't download things from the ALSA site.  Ubuntu doesn't use .exe files.  You can install programs by going to "system->Administration->Package Manager".  It has 16000 programs, you can install them all from there.

Here is a step by step howto on how to get your sound working.  Open up a terminal and type everything below in order, enter YOUR password when prompted

```
sudo apt-get install build-essential

sudo apt-get install alsa-source

sudo apt-get install linux-headers-2.6.10-5-686

sudo apt-get install kernel-package

sudo  apt-get install ncurses-dev

sudo dpkg-reconfigure alsa-source ## In this section, choose azx as driver

sudo apt-get install fakeroot

sudo  cd /usr/src

sudo tar jxf alsa-driver.tar.bz2

sudo cd linux-headers-2.6.10-5-686

sudo make-kpkg --rootcmd=fakeroot --append-to-version=-5-686 modules-image

sudo dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb 
```

---

### Post by Might on 2005-08-02
where this system->Administration->Package Manager ? ubuntu is program maybe i dont know i just looked in google and find this forum.Help me for newbie

---

### Post by varunus on 2005-08-02
OK, from your posts, it sounds like you're running windows, not linux.  This is a LINUX forum.  Ubuntu is a type of LINUX, an alternate operating system.  Here's some information about it.
[http://www.linux.org/](http://www.linux.org/)

If WINDOWS isn't making any sound after a reinstall, we can't help you here.  Things like this are why we switched to LINUX.

---

