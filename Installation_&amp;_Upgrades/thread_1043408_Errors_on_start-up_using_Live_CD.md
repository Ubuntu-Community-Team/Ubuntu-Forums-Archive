---
title: "Errors on start-up using Live CD"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2009-01-18
I'm trying to see if Ubuntu will work on my old pc.  I'd like to give the pc to my dad for him to surf the internet and use email.  The pc has the following components:

- ASUS P4T i850 Chipset 400Mhz FSB Motherboard
- INTEL Pentium 4 - P4 1.40GHz Processor 400MHz system Bus
- 515 MB of RAMBUS 800 MHZ ram (4 sticks of 128 MB each)
- 32 MB Matrox dual VGA video card
- IBM IC35L040AVER07 Deskstar 60GXP 40GB Hard Drive
- 3COM 3C905CX-TXNM Fast Etherlink XLPCI 10/100NetworkCard
- Dell 2001FP 20`, 1600*1200 resolution monitor

I originally tried Ubuntu 8.04 (32 bit) but it did not boot up.  I then tried Ubuntu 8.10 and it seemed to partially work.  I got it to boot to the desktop but with the following three error messages:

- Error The panel encountered a problem while loading the following OAFIID:Genome_ShowDesktopApplet`  Do you want to delete the applet from your configuration.

- Error The panel encountered a problem while loading the following OAFIID:Genome_WindowListApplet`  Do you want to delete the applet from your configuration.

- Error The panel encountered a problem while loading the following OAFIID:Genome_WorkspaceSwitchterApplet`  Do you want to delete the applet from your configuration.


I`m also having a problem with loading Firefox.  I freezes and then shuts down.

BTW.  the question mark key does not appear to be working for some reason in this message.  I`m using a Vista pc to type this message.  This is unrelated to my Ubuntu installation problem.

Are the three errors significant or should I go ahead and delete them (question mark).  I want to make sure I can install Ubuntu on the hard drive without any problems.

How do I stabilize Firefox or get another browser installed (question mark).

---

### Post by Partyboi2 on 2009-01-18
You may need to reinstall the gnome-applets package
```
sudo apt-get --reinstall install gnome-applets
```
These errors are not going to bring your system to a stand still and may even disappear after you have installed. (did for me)
Once you have installed You can go to add/remove and do a search for web browsers and install another one if you want to install another browser.

---

### Post by boof1988 on 2009-01-30
Have you got it to work yet?

---

