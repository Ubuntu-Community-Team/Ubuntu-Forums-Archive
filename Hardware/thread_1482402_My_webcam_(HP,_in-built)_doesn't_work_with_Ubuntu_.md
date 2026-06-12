---
title: "My webcam (HP, in-built) doesn't work with Ubuntu 10.04"
date: 2010-05-13
forum: Hardware
---

### Post by ivanmoraesfilho on 2010-05-13
Hi,

I'm an linux newby and my webcan (HD inbuilt) hasn't worked since I started using the new Ubuntu 10.04. 

I'd be really gratefull if any of you could help me out. I warn you, though: I'm pretty dumb, so you'll have to be very patient and specific on the tips you give.

Thanx already,
ivan

ps/ my notebook is a HP Pavilion dv6750BR. Dunno if it makes any difference...

---

### Post by lrcaballero on 2010-05-13
Open up a terminal and Try this:

CODE:
sudo modprobe uvcvideo
sudo apt-get install cheese
cheese

Luis Caballero

---

### Post by ivanmoraesfilho on 2010-05-13
Sorry for my stupidity, but what is to "open up a terminal"? Where should I insert  that code? I swear I'm not kidding:)

---

### Post by ivanmoraesfilho on 2010-05-13
I typed it on the package manager and it said that package "sudo" has already been installed...

---

### Post by IcarusR on 2010-05-13
These commands need to be run in a terminal window.

Applications > Accessories > Terminal.

Also post output of command lsusb to identify your webcam

---

### Post by ivanmoraesfilho on 2010-05-13
good news is that I found a terminal and typed the code :):):)


bad news is cheese still can't find my webcam (so can't skype, emessene, etc)

---

### Post by Shakey88 on 2010-05-14
I've been having the same problem with my HP DV6 2020sa

However it works in "cheese"
but cant get it to work in any chat client :(

Btw, "lsusb" command, (as far as im aware) only shows up external usb devices, not internal, so that won't bring up his integrated webcam...

If its the same as mine, i think its a quanta computers webcam, i can't be sure tho...

---

### Post by IcarusR on 2010-05-15
> Btw, "lsusb" command, (as far as im aware) only shows up external usb devices, not internal,

Actually "lsusb" will list any device connected to usb bus, it does not know weather devices are internal or external.
Most internal webcams I've come across are usb.

So if the OP posts the output of command "lsusb" we can identify what chipset the webcam is based on & may be able to make further suggestions.

---

### Post by _Seraph_ on 2010-05-31
I'll spare you guys. I have the exact same setup (HP dv6000 laptop) albeit with 9.10 Karmic Koala. Been tinkering around, but nothing's seemed to show up so far.

lsusb provides this:

[COLOR=Navy]Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/COLOR]
The mouse is just a mouse heh.
You can see I tried to 'make install' something from someone's tar.bz2 package, thus the [R5U870]  ??? I don't know if it's messing things up, or how to revert it back to an original state, but that's what it looks like right now!

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam)

This would've helped, but 
[COLOR=Navy]sudo apt-get install luvcview[I]
sudo [/I]modprobe uvcvide*o*[/COLOR]
didn't seem to do anything. =(

This seems to be a popular problem, so if a solution comes up, it'd be greatly appreciated!



:::: EDIT ::::
Okay, I may have found something amazing. The answer appears to lie here: [http://ubuntuforums.org/showthread.php?p=8334410#post8334410](http://ubuntuforums.org/showthread.php?p=8334410#post8334410)
But I think I've only done half of it right. Can anyone give me the list of commands I'd need to install that driver?

---

### Post by _Seraph_ on 2010-05-31
All thanks to David Jurenka, who updated the description to [this thread]("https://bugs.launchpad.net/ubuntu/+bug/120434") only days ago.

The instructions here worked perfectly for me on 9.10. Do exactly those 4 things, and it'll work. Even in Cheese. *Even In Cheese.*


> The packages provided (both source and binary) include only the loader software and do not contain the microcode whose copyright and license status is unclear. Instead, a simple shell script is provided that can download and install the microcode directly from the upstream repository.
 Installation:
** 1. sudo add-apt-repository ppa:r5u87x-****loader/**[B]ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/[/B]**r5u87x/****r5u87x-****download-****firmware.****sh**
 (Step 1 only works on Ubuntu 9.10 and newer. On older releases you will need to add this PPA to your APT sources manually.)
 Note:
The repo also contains packages r5u87x-loader. These now serve only as transitional packages to r5u87x, and they are kept here only because they are referred to in [bug #120434]("https://launchpad.net/bugs/120434").

source: [https://launchpad.net/~r5u87x-loader/+archive/ppa]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa")

---

### Post by ganjarie on 2010-06-28
> **_Seraph_ said:**
> All thanks to David Jurenka, who updated the description to [this thread]("https://bugs.launchpad.net/ubuntu/+bug/120434") only days ago.

The instructions here worked perfectly for me on 9.10. Do exactly those 4 things, and it'll work. Even in Cheese. *Even In Cheese.*


source: [https://launchpad.net/~r5u87x-loader/+archive/ppa]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa")


When i do last step ***sudo /usr/share/r5u87x/r5u87x-download-firmware.sh*** 

i receive this error ***Error: Failed to find any supported webcams.***

please help. how do I resolved this. 

My laptop is hp pavilion dv4-1225dx

---

### Post by ganjarie on 2010-06-28
this is the information lsit when i use ***lsusb*** command

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by salmanmanekia on 2012-06-24
I am also stuck at the same point as the last poster...Any hints

---

