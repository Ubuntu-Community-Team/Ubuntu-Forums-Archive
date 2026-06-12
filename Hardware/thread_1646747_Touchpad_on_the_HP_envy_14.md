---
title: "Touchpad on the HP envy 14"
date: 2010-12-16
forum: Hardware
---

### Post by Romu on 2010-12-16
Hi all,
Yesterday I installed Ubuntu 10.10 64 bits as the only OS on my new HP Envy 14. Fortunately, most of the hardware is recognized out of the box or by installing specific drivers, very nice.

Now, there is 2 remaining issues: the Webcam support with Skype (I alredy know how to fix it) and the multi touch touchpad.

This touchpad is similar as the ones found on the MacBook, a single clickable surface with some drawings to figure out the buttons.

The touchpad works pretty well out of the box, except there is no need to make a right click, and this is the issue. I installed the touchpad and synaptics utility but there is nothing related to the right click.

I dream of a fix to allow the 2 fingers right click, but I would also accept another solution.

Anyway, any idea to fix this?

Thanks.

---

### Post by Romu on 2010-12-16
Here are some messages found in dmesg result regarding the touchpad:

```
[   15.953679] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000/0x5a0400
[   15.968011] CE: hpet increased min_delta_ns to 7500 nsec
[   15.988608] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10

```

lspci returns nothing about the touchad.

So any idea how to get a right click?

Thanks.

---

### Post by guakeke on 2010-12-16
Hi there, I got my Clickpad working using this package:

xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb 

It's available here [http://sites.google.com/site/andyeyre/files](http://sites.google.com/site/andyeyre/files)

It enables side-scrolling, two-finger scrolling, tap to click, right click and tap to right click in the bottom right hand of the Clickpad.

User [mpdava]("http://ubuntuforums.org/member.php?u=1195531") has shared a whole load of useful tips for the Envy 14, including an alternate package for the Clickpad, in this thread:

[http://ubuntuforums.org/showthread.php?p=10235323](http://ubuntuforums.org/showthread.php?p=10235323)

Good luck!

---- 

EDIT 
Since I wrote this post I find that Andy Eyre's package is no longer enabling multitouch features on its own. I also need a package called synaptics-dkms to get my clickpad working nicely. 
It's available here along with an explanation of how to install it: [http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/)

---

### Post by Romu on 2010-12-17
Nice, thanks for the links, some things to read and fix the issue :D

---

