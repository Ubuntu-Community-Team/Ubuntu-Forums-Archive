---
title: "Ubuntu on Compaq Presario 1700"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by Dev0205 on 2007-08-14
I've came across an older Compaq Presario 1700 that I want to install Linux "Preferably Ubuntu" on for school. It has 800mhz, 256mb, and Win ME installed already "ME runs smoothly I should add". Anyways, I popped in a 7.04 Ubuntu CD and fired up the install. It loaded pretty slow as expected but then it really bogs down once you start the Install. 

We're talking 10mins before the text updates on the first Welcome Screen. You can hear the CD drive churning but nothing seems to be going on. Even when moving the mouse, it takes about 2mins until you see it move. I'd really appreciate any help you guys can throw my way. Is there another Distro or another way to install Ubuntu on here that I can try? I currently do not have a pin drive "Just incase that is suggested".

Thank you,
Dev0205

---

### Post by pbcartwright on 2007-08-14
try xubuntu ( xubuntu.org)
Xubuntu is a complete GNU/Linux based operating system with an Ubuntu base. It is lighter on system requirements and tends to be more efficient than Ubuntu with GNOME or KDE, since it uses the Xfce Desktop environment, which makes it ideal for old or low-end machines, thin-client networks, or for those who would like to get more performance out of their hardware.

---

### Post by Dev0205 on 2007-08-15
pbcartwright,

The Xubuntu install loaded much quicker! Thanks. I have to admit, I ran into some problems at the start with the ext3 File System not wanting to install but I managed to get around it. I can't wait to get Linux up and running on this system. :)

Thank you again!:)

---

### Post by Dev0205 on 2007-08-15
Hmm. I understand Xubuntu is meant to be lighter on the system but I'm not getting anything from my Ethernet port or sound. Is there something I'm missing here?

---

### Post by EXCiD3 on 2007-08-15
What ethernet and sound card do you have? They may not work out-of-the box and may require a little bit of work to get working correctly. There would not be any difference between using Kubuntu, Ubuntu, Xubuntu, as the only differences are the window managers of the system, Xubuntu is defintely the flavour of Ubuntu you would want to use on that computer.

---

### Post by Dev0205 on 2007-08-15
EXCiD3,

I wish I knew for sure. This is an old system my parents had and it eventually made itself to me. There isn't any paperwork on it but I do remember using it at lan parties back in the days of Quake II and such. I was tinkering with the system for a long time and eventually was able to get the Ubuntu 7.04 install to load correctly. For some reason, the system shows that it has a wired connection, even when there is nothing hooked up. I "disable" networking and then the install loads up just like any other. 

I know my way around Ubuntu better so I figure if I can get it loaded, I'll knock out the other problems in time. Here is the biggest thing stopping me. I think the partitions are all jacked up from the multiple times I've tried installing Linux on it. Is there a simple Live CD kind of program that can format this puppy to EXT 3 with no questions asked? Just getting Ubuntu on the Laptop would be one hell of an accomplishment. I just need Open Office and the network to work "For taking notes at school".

I appreciate the support!

---

### Post by logos34 on 2007-08-15
use Gparted live cd to format it. 

Google around for the manual to that presario.

For sound troubleshooting you could try this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

To track down what drivers your hardware uses for networking and sound, you could run

**lspci -n**

then copy the output to removable media, use another machine to go [this site]("http://kmuto.jp/debian/hcl/") and paste it in the box there.  Then go back to your Xubuntu install and see if you can load any of the modules.  Worth a shot.

---

### Post by EXCiD3 on 2007-08-15
Try this for formating: [http://partedmagic.com/]("http://partedmagic.com/")

I use Hiren's boot CD for any partitioning, and any problems i have. You can try and download it, or check this out: [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by msdemarchi on 2007-08-18
Have the same model (compaq presario internet zone 1700 US) and installed kubuntu feisty fawn. Works flawlessly. everything, including the mousepad, the buttons, network, etc... even got cel web usb modem (HUAWEI) working ok. Sound, video etc ok! Didn´t do anything. PnP! (except for the usb cel modem which takes a little bit of command lines. Nothing scary though!). Try Kubuntu and you probably won´t have to do anything!

---

### Post by Dev0205 on 2007-09-03
Woah, I've been hella busy since classes started. Thank you all for the many replies. I've been able to install Ubuntu 7.04 on the system but have no internet and the battery monitor doesn't work. As soon as I get some more helpful information I'll post it. Thank you all again for the support.

---

### Post by EXCiD3 on 2007-09-03
Since you are running a Presario laptop, check out my howto here: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

It covers most of the HP/Compaq laptops. Hopefully some of the information/links there will help you out!

I'm having a hard time playing with Ubuntu now that classes have started too! Its really hard to find time to sit down and play with this between friends and class... I say we just skip class! ;)

---

