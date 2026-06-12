---
title: "Installed, but cant be accessed"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Pyridoxal on 2009-03-19
Okay, I burnt a Live CD, and when I decided to download Ubuntu, it worked fine until it came to the Black Screen part

When at the black screen, it was doing fine until the black screen disappeared and it went back to the Live Session. After this happened, nothing else happened when it comes to the installer.

Help?

---

### Post by overdrank on 2009-03-19
Hi and welcome, When you boot the live cd are you able to see anything like start or install without any changes?
Or do you just receive a blank screen when booting the live cd?

---

### Post by Pyridoxal on 2009-03-19
I am on Ubuntu atm, Im just on the live seesion though


When I put in the CD, everything comes up, but I have everything installed (I think) because when i tried installing again, it said that there was a ubuntu already installed

---

### Post by overdrank on 2009-03-19
> **Pyridoxal said:**
> I am on Ubuntu atm, Im just on the live seesion though


When I put in the CD, everything comes up, but I have everything installed (I think) because when i tried installing again, it said that there was a ubuntu already installed

Ok is that the install you did with Wubi or from the live cd?
When you boot to Ubuntu from the grub you just receive a black screen?
Also what is the model of the graphics card? If you are using the live cd you can use the terminal located under applications, accessories and enter the command lspci. Then look for VGA and this will be the graphics card.

---

### Post by Pyridoxal on 2009-03-19
> **overdrank said:**
> Ok is that the install you did with Wubi or from the live cd?
When you boot to Ubuntu from the grub you just receive a black screen?
Also what is the model of the graphics card? If you are using the live cd you can use the terminal located under applications, accessories and enter the command lspci. Then look for VGA and this will be the graphics card.

Okay, lspci thing is this

---------
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
---------

I cant boot it without the Live CD (I use the live cd, not wubi)

---

### Post by overdrank on 2009-03-19
> **Pyridoxal said:**
> Okay, lspci thing is this

---------
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
---------

I cant boot it without the Live CD (I use the live cd, not wubi)

Ok do you see the grub when booting and are you able to select Ubuntu or windows?
If you can then select recovery mode which is usually the second choice from the grub.
Then you can choose the xfix option, when it is complete the select to boot normally.

---

### Post by Pyridoxal on 2009-03-19
> **overdrank said:**
> Ok do you see the grub when booting and are you able to select Ubuntu or windows?
If you can then select recovery mode which is usually the second choice from the grub.
Then you can choose the xfix option, when it is complete the select to boot normally.

No, I am not able to select Ubuntu or Windows

and what does the grub look like >_<

---

### Post by Pyridoxal on 2009-03-19
just reviving, because I need to know as soon as possible

---

### Post by overdrank on 2009-03-19
> **Pyridoxal said:**
> No, I am not able to select Ubuntu or Windows

and what does the grub look like >_<

When you installed Ubuntu did you select use the whole disk or resize windows.

---

### Post by weinju on 2009-05-30
Okay, here is my black screen issue: the installation seemingly was fine. However, right after the FIRST reboot: (1) the graphical login loads, username/pwd entered, and (2) the GUI refuses to load and the screen is black with a lonely mouse cursor. Resets do not help.

Identical video: Intel 82915G/GV/910GL Integrated rev 04.

* Reinstalled Jaunty THREE TIMES. Same thing.
* Tweaked xorg.conf to include the full name of the Intel video card under the "Device" portion.
* Uninstalled fglrx packages per [this thread]("http://ubuntuforums.org/showthread.php?t=1172850").
* Followed the "Safe" configuration from the [Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582").

NOTHING. NOTHING. NOTHING. What else can I do? Upgrade the driver? Sue Intel? I am ready for anything radical at this point :)  

Advice and ideas are much appreciated.

---

