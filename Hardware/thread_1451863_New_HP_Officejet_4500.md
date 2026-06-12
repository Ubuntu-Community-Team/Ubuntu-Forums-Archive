---
title: "New HP Officejet 4500"
date: 2010-04-11
forum: Hardware
---

### Post by StefanElliott on 2010-04-11
I just bought a new HP Officejet 4500 (released in March) which, it was reported, has support for Linux.  I'm yet to find much.  Looked for HPLIP support.  Whatever is there is very sketchy.  I finally got an installation to work using CUPS setup utilities.  So far I've been able to print a test page but I now can't get the scanner to install.  btw, it's an All-in-one Printer/Scanner/Fax/Copier.  At least, now, I can print out my tax forms and, hopefully, make any copies I need.  q:-)

Anyone have more intelligence on this?  It looks like it's going to be a nice addition to my Home/Office, once it works.  Oh, Staples is selling them for $79.99 - wow! :P
But, I suggest waiting until we know all the features will be supported in Linux.  Perhaps HP would like to step up?  - or HPLIP?  HP could sell a boat-load of these in the Linux world if they'd just pay us a little attention.  They should have had Linux utilities and installers ready from the get-go.

Here's what I have so far:
Running CUPS Utilities   [http://localhost:631/](http://localhost:631/)
I added the printer and after several failed attempts lit upon the
hp-officejet_j4500_series-hpijs.ppd
under
Driver hpijs 3.9.8
Found hpijs using Synaptic and searching for HP.
Haven't been able to get any joy out of HPLIP but that is probably because I don't know what I'm doing with that.

---

### Post by kama-rupa on 2011-04-09
So I just got an HP Officejet 4500 and installed it on 2 windows 7 machines in the house. Now I really  really want to use this with my 2 ubuntu machines running 10.04 & 8.10. Did you ever have any luck getting all of the all-in-one features working with ubuntu?

---

### Post by StefanElliott on 2011-04-09
Once I got HPLIP to download and compile it was not too hard.

---

### Post by hudo on 2011-05-10
Hi,

I just installed my new officejet 4500 G510g-m with ubuntu 10.04 (lucid)

Got howto from youtube: [http://www.youtube.com/watch?v=v3rxpX2cgtM](http://www.youtube.com/watch?v=v3rxpX2cgtM)

Installed HPLIP 3.11.3a which was from here: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I connected the officejet per ethernet cable. It has a function to show you its actual ethernet-address : Print Report->ok Network Config -> ok

After starting the hp device manager (e.g. from terminal with hp-toolbox ), choose setup device-> Network/Ethernet
-> Show advanced options --> Manual Discovery   and enter there the ip of the officejet e.g. 192.168.1.7

Printer tested... works fine
Scanner tested... works

Fax sended tested...works fine

drivername: hp-officejet_4500_g510g-m.ppd

Good luck

---

### Post by 5ER on 2011-10-21
Does borderless printing work in Linux?

---

### Post by agillator on 2012-02-24
Take a look at [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845) #9. Although that is specifically about wireless, the principle is the same. In my experience there is something wrong with Ubuntu's installation of HPLIP. I believe you need to totally remove it, get HP's complete version, and install that one. Then you should be able to find and set up your printer, either wired or wireless. If you can't with the 4500, that will be the first HP printer that I have heard of that won't work.

---

### Post by nothingspecial on 2012-02-27
You are replying to a spam post that bumped an old thread to the top.

The spam has been removed.

Closed.

---

