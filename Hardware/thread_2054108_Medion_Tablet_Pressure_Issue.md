---
title: "Medion Tablet Pressure Issue"
date: 2012-09-06
forum: Hardware
---

### Post by JustForAGlance on 2012-09-06
I know this has probably been done over a million times, but i am a newbie to Ubuntu all in general. Several days ago my XP crashed and decided to have my friend install Ubuntu. I am amazed at how smooth and convenient everything is.... except for small minute things like getting drivers and such.

I have a Medion Tablet (Purchased from Aldis) 

The Model: MD 85637 USB Graphics Pad P82012

My version of Ubuntu:  ubuntu 12.04 LTS

Im hoping someone could maybe take the time out of their day to at least try to help me get pressure working on my tablet. Everything else works fine, but the pressure just doesn't register.

P.S. I am a Newb, so go easy on me, although i do know what terminal and sudo is. 

Any help would be appreciated, thank you!

---

### Post by Favux on 2012-09-06
Hi JustForAGlance,

Welcome to Ubuntu forums!


Because these sorts of tablets are often rebranded lets find out the OEM and product ID of the tablet.  Open a terminal and run the following command:
```
lsusb
```
and please post the outputs.

What application(s) are lacking pressure?

---

### Post by Incarnadine on 2012-09-06
I searched the net for some possible Linux drivers, but found nothing. I did find that tablets are normally plug and play, so the fact that not all features on the tablet are working doesn't sound good. I checked out the official Medion website and noticed that they have "MEDION recommends Windows® 7" logos all over the place. I'm going to make a guess that their tablets have propietary drivers for Windows.

I'm sorry to say, but it looks like Medion could give a rats *** about Linux. ](*,) I really despise companies like this.

---

### Post by JustForAGlance on 2012-09-06
The ID is " ID 172f:0034 Waltop International Corp. Slim Tablet 12.1"

the output in the terminal looked like this:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 002 Device 003: ID 172f:0034 Waltop International Corp. Slim Tablet 12.1"

And i am missing Pressure in GIMP (2.6), if gimp is the issue i could probably switch to a different application, but i mostly know how to use GIMP.

---

### Post by JustForAGlance on 2012-09-06
> **Incarnadine said:**
> I searched the net for some possible Linux drivers, but found nothing. I did find that tablets are normally plug and play, so the fact that not all features on the tablet are working doesn't sound good. I checked out the official Medion website and noticed that they have "MEDION recommends Windows® 7" logos all over the place. I'm going to make a guess that their tablets have propietary drivers for Windows.

I'm sorry to say, but it looks like Medion could give a rats *** about Linux. ](*,) I really despise companies like this.
Well i did get it to work on my old Windows XP after finding the drivers online.

---

### Post by Incarnadine on 2012-09-06
> **JustForAGlance said:**
> Well i did get it to work on my old Windows XP after finding the drivers online.

Yeah, I was trying to say that Medion seems to only make drivers for Windows, but there still seems to be hope.

I'm going to try and find a generic driver for a Waltop International Corp. Slim Tablet.

---

### Post by JustForAGlance on 2012-09-06
Thanks! :D

---

### Post by Favux on 2012-09-06
Alright good.  You have a:
```
Bus 002 Device 003: ID 172f:0034 Waltop International Corp. Slim Tablet 12.1"
```
which is supported according to the DIGI*mend's [Tablet support status page*]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status") site.  What that means is the kernel driver is working and it should set up automatically on the Wacom X driver.  Work out of the box in other words.
Vendor ID = 172f = Waltop
Product ID = 0034

So this probably means you just need to configure the extended input devices in Gimp or Inkscape to get pressure.  Is it one of those apps that lacks pressure?  You should have pressure without doing anything in MyPaint.

---

### Post by JustForAGlance on 2012-09-06
Forgive me for my ignorance, but how would i setup the extended inputs in gimp?

---

### Post by Favux on 2012-09-06
With Gimp opened:  Edit > Preferences > Input Devices > Configure Extended Input Devices... > click on the Device drop down and select the line with stylus.  Then click on the Mode drop down and select Screen.  Save and you should be configured for pressure.

More information is available on the "Tablet setup in applications" page at the [DIGI*mend* site's wiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend").

---

### Post by JustForAGlance on 2012-09-06
Thanks! IT WORKS. phew, i thought this was gonna be  complicated.

---

### Post by Favux on 2012-09-06
Good!  :)

Please mark the thread as Solved.

---

