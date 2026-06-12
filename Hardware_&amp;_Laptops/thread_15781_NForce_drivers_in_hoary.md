---
title: "NForce drivers in hoary"
date: 2005-02-16
forum: Hardware &amp; Laptops
---

### Post by pagefault on 2005-02-16
I was wondering if anyone has gotten the nforce system drivers working (network and sound) with ubuntu. I really would like to make use of the the 4 speaker output and hardware mixing supported in the nvidia driver. Thanksl

---

### Post by songochain on 2005-02-17
Hi dude, i've a nforce mobo too. I found nforce drivers in nvidia web for linux64bits but i dont know how to compile it

---

### Post by Kevin on 2005-02-17
I've managed to install the nForce drivers finally, but I don't know how to enable them yet.  Running the nvidia .run file doesn't work, I had to follow these instructions:    

[http://www.nvnews.net/vbulletin/showthread.php?t=43177](http://www.nvnews.net/vbulletin/showthread.php?t=43177)

If anyone knows how to just turn the things on that would be great!  :wink:

---

### Post by Kevin on 2005-02-17
Ok, so I seem to have gotten them working!
However, I'm not really all that sure what I did  :roll: 

I'll try and explain what I did for you though.

After installing the drivers the same way listed on that nvnews posting, I rebooted my computer.
Then I changed my default sink to OSS in the Multimedia Systems Selector.

In order to run nvmixer, I need to do:
sudo apt-get install libqt3c102-mt

Then from the terminal I ran nvmixer and set up my speakers and now they work!

So hopefully that helps! No guarantees though :-)

---

### Post by dewey on 2005-02-18
I'm using a DFI Lanparty NForce3 250gb motherboard (socket 754) and it runs fine, without any official drivers, I'm using the onboard sound and lan, and it seems to be working perfectly.
[edit:]Although, I'm using Warty with backport repos.[/edit]

---

### Post by pagefault on 2005-02-18
I managed to get the driver installed but gnome continues to lock up after playing a few sounds now. Anyone have a similar problem?

---

### Post by roka on 2005-02-20
To build the nforce driver i need the kernel source, but the source wasent included in the ubuntu installation what should i write to download the kernel source code from apt-get?

EDIT: ive downloaded the kernel-headers and i have compiled the nForce driver but sound isent still working=(. When i boot my computer i hear a sound while gnome is starting, but the boot i cant hear sounds in doom3 or in xmms, do someone have an idea what the problem can be?
( I run hoary amd64 version )

---

### Post by songochain on 2005-02-21
[QUOTE=roka]To build the nforce driver i need the kernel source, but the source wasent included in the ubuntu installation what should i write to download the kernel source code from apt-get?

EDIT: ive downloaded the kernel-headers and i have compiled the nForce driver but sound isent still working=(. When i boot my computer i hear a sound while gnome is starting, but the boot i cant hear sounds in doom3 or in xmms, do someone have an idea what the problem can be?
( I run hoary amd64 version )[/QUOTE]
I've kernel headers to but when i do sh NVIDI*.run, it says i havent precompiled kernel ... How did u install nforce drivers for amd64 hoary??

---

### Post by songochain on 2005-02-21
[QUOTE=Kevin]I've managed to install the nForce drivers finally, but I don't know how to enable them yet.  Running the nvidia .run file doesn't work, I had to follow these instructions:    

[http://www.nvnews.net/vbulletin/showthread.php?t=43177](http://www.nvnews.net/vbulletin/showthread.php?t=43177)

If anyone knows how to just turn the things on that would be great!  :wink:[/QUOTE]
I've installed nvsound module but what have i do to set default??

---

