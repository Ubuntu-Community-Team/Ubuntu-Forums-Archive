---
title: "Intel 915g on-board audio not working"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by tablatom on 2005-03-29
Hi All,

I have the Asus P5GDC-V motherboard, based on the Intel 915g chipset.

I cannot get the on-board audio working.

I downloaded the driver from Intel (AUD_LINUX_1.5_BETA.sh),It got as far as

    Building AZX-DRIVER
    Compiling the AZX-DRIVER for GENERIC Intel HD Audio  Codec, this
    operation may take a while depending on   your system configuration.

And then I got:

    Installing driver..
    Make failed!, module not found!

Not very informative I know :-(

Anyone had any experience with this?

Tom.

---

### Post by tablatom on 2005-03-31
*bump*

---

### Post by tablatom on 2005-04-12
I've fixed it now. For the sake of others, here's what got me going:

[http://www.fedoraforum.org/forum/archive/index.php/t-30914.html](http://www.fedoraforum.org/forum/archive/index.php/t-30914.html)

In case that dissapars, the crucial bit was:

hoggieii
2005-01-19, 01:21 AM PST
Recently acquired an intel D915GVMB board which has the same audio. The issue with Fedora Core 2 is that the version of alsa shipped and the one on yum is only 1.0.3a. The Azalia driver - read Intel HD Audio Driver - got added in 1.0.6. Since I've always had problems with getting Intel's version of drivers working, I wasted no time in download the latest alsa ([www.alsa-project.org](www.alsa-project.org))
- current 1.0.8 and compiled them in the time honoured "./configure --prefix=/usr; make; make install" as root. The order of build and install is Drivers, Lib, OSS-compat & Utils. Then I ran alsaconf - let it amend /etc/modprobe.conf - to my relief the card was picked up first time and now works great. Since you would of overwritten the existing alsa lib, its wise to ensure that yum and up2date don't try to upgrade your alsa lib.

(Note I had to add the g++ package to get it to build)

Tom.

---

### Post by lobsterboy on 2005-05-18
just to add my two bits -- fixed the sound on my Asus P5GDC-V board (intel 915G chipset) by installing the alsa driver 1.0.8 as per the instructions here:

[http://ubuntuforums.org/showpost.php?p=100951&postcount=1](http://ubuntuforums.org/showpost.php?p=100951&postcount=1)

with a few modifications: i changed the configure line to read:

./configure --with-cards=azx

and i didn't have to modify the /etc/modules file at all (actually, i did modify it the first time around, but seemed to be getting some errors -- driver already in use type things -- so i just took the lines out again). 

i then had to change System > Preferences > Multimedia Systems Selector > Audio > Default Sink > output to ESD -- the others didn't work.

but all is great now! didn't even know about these little bongo noises until about five minutes ago -- we'll see how long i leave them as defaults!

btw, just so nobody else gets confused on this (as it did confuse me): it looks like the default install (at least on my system) included alsa drivers 1.0.8 -- but these are the ones i downloaded & (re?)installed to make things work.

---

### Post by scaza on 2005-09-05
You are right, ubuntu comes with version 1.0.8 but for whatever reason they took out the azx driver so you have to download the full version.  Oddly enough I tried doing this with version 1.0.9b which is listed a stable and the ./configure process could not find the dr iver.

Now I have a sound icon and my however I still do not have sound.  GRrrr, and i'm out of ideas and patience for now.  Oddly enough it did list two sound devices in the mixer  reakTek HD and another.  I thought my there is a problem with using the wrong device so I tried to disable one of them but all to no avail.

---

### Post by kennywest on 2005-09-05
I have the same sound card and I upgraded my kernel to 2.6.13, which supports the Intel HD Audio device. I also didn't have any sound. After adding my user id to the audio group (/etc/groups), I got sound working.

---

### Post by scaza on 2005-09-09
And for those who may be interested in what stopped the silence for me:
After following many different instructions that worked for others on how to install upgrades of alsa with little success I discovered realtek driver pack
[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True) 

you will still have to install alsa again but this makes it work for me.

It also looks like alsa-1.0.10 has much new support for HDA 880.  However I was unable to install this version for some reason.

---

