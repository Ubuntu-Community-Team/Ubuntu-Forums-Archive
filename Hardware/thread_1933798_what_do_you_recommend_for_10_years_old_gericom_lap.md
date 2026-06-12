---
title: "what do you recommend for 10 years old gericom laptop"
date: 2012-03-01
forum: Hardware
---

### Post by urban120 on 2012-03-01
hello
my father has an 10 year old gericom laptop that he still uses he currently has windows xp on but it runs slowly so i am wondering if it would better run with ubuntu or any other version linux
computer spec:
2.8 single core cpu
1gb ram
some (very) old ati graphic

im looking for best posible linux that i can put om it
computer is mostly used for office work

---

### Post by Linuxisfast on 2012-03-01
Puppy Linux, DSL or Tiny.

---

### Post by Rodney9 on 2012-03-01
[COLOR="Blue"]Lubuntu[/COLOR]

Installing Lubuntu
[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

A Pentium II or Celeron system with 128MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by madvinegar on 2012-03-01
Zorin OS ([www.zorin-os.com](www.zorin-os.com))
Based on ubuntu 11.04 but much faster and with look options (including win7 look, winXP look etc) so your father will be having a familiar environment.

I have installed it in any old pc I got (that used to run winXP) and it literally transformed them.

---

### Post by Mark Phelps on 2012-03-01
If a laptop with those specs is running so slowly under Windows XP as to be all but useless, only the most MINIMAL Linux distro is going to perform any better.  

Those specs can comfortable run XP quite well.  So, the slowness could be the result of filesystem fragmentation (easy to fix) or a failing drive (increasing sector failure will really SLOW down a hard drive).

If the drive is failing, NO OS is going to work well on it.

Also, I'm concerned about the comment "office work".  If you mean using MS Office, that doesn't run natively in Linux and requires the installation of Wine and considerable tweaking to get it to work.

---

### Post by urban120 on 2012-03-01
computer is not very slow with xp just a little
and with office work i meant word, excell etc. (linux version i use w7 so i dont know the name)
im still wondering if it would run latest ubuntu

---

### Post by Mark Phelps on 2012-03-01
> **urban120 said:**
> computer is not very slow with xp just a little
OK ... so, Ubuntu 11.x versions might be a little faster than XP, but I doubt you will see any real difference.

> ...and with office work i meant word, excell etc. (linux version i use w7 so i dont know the name)
You mean Microsoft Office -- and if you are using the latest version, or a version that came preinstalled in Win7, you're talking about Office 2010 -- which will require the installation of Wine, and according to the WineHQ website, does not work well in Linux.  So, if daily use of MS Office 2010 is a feature needed, migrating to Linux is a really BAD idea.  Other folks may tell you that using AbiWord and/or LibreOffice will work FINE, but folks trying to use those to work with Office XML documents have found them to be problematic.

> im still wondering if it would run latest ubuntu
The only REAL way you can find out is to download and burn an ISO of 11.10 to a CD, boot from that, select Try Ubuntu -- and see how well it works.  It will be a little slow because it's loading SW from the CD, but at least you will be able to tell how well it detects the hardware and installs the proper drivers.

Good Luck

---

### Post by urban120 on 2012-03-01
what abaut openoffice is it good

---

### Post by lykwydchykyn on 2012-03-01
> **urban120 said:**
> what abaut openoffice is it good

That's a can of worms to open.

OpenOffice is what LibreOffice was forked from.  At this point, it's essentially an old verion of LibreOffice with some features missing.

Why not install LibreOffice, firefox, and other cross-platform open-source applications on Windows XP and see if the users of the laptop find them acceptable?

---

### Post by madvinegar on 2012-03-01
Just to keep in mind, Zorin OS comes with libre office preinstalled.
Personally I have seen huge difference from when the PCs had XP...

---

### Post by jerrrys on 2012-03-01
I have ran Xubuntu and Puppy on a single core P4@1.7Ghz with very good results.

---

### Post by urban120 on 2012-03-02
ok i decided that i will try zorin os and latest ubuntu
thank you all for your help i will post results when i try them on my fathers computer

---

### Post by ahning on 2012-03-02
If you want to use less resources than regular ubuntu try xubuntu with window managers from fluxbox or openbox as they both use fewer resources. 

I use a nettop with openbox mainly with xubuntu, Debian and Microsoft Windows Vista (triple boot.) I also used fwvm on my Debian OS. Fluxbox has everything set up more than openbox for first installation; but you could still run both your Microsoft OS and Xubuntu or another OS. What is so neat about openbox is that you can do keybinding and mouse binding such that you can make your own shortcuts with the keys or mouse clicks to bring up menus or what ever you want.

---

### Post by mastablasta on 2012-03-02
some older ATI mobile cards might not have good 3D support. default Unity interface in Ubuntu uses 3D, to solve this issue a version called Unity2d is available which looks the same and doesnt' use 3D hardware acceleration.

1GB 2.8Mhz computer should run windowsXP quite well. especially if it's only for office work.

---

