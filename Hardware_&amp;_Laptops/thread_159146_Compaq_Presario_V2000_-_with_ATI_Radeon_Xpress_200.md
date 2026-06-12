---
title: "Compaq Presario V2000 - with ATI Radeon Xpress 200M"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by TriZz on 2006-04-12
New to Linux here - so please bear with me if I mess up the jargon:

Before I start, let me tell you that I'm having a blast figuring this stuff out.  First, I couldn't get the GUI to work - so I had to change the xorg.conf file to "vesa" as opposed to "ati" and that got it working...then, figuring out how to get my wireless card to work.  I love it!!  Getting so frustrated, then making it work - it's a rush.

However, I'm lost about getting this ATI 200M driver to work/install properly.

I've tried the universal multiverse fix, but when I run the command the following command in the terminal:

> sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper

I get the following output:

> Package gcc3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package gcc-3.4 has no installation candidate

Any help to get this driver installed (in newbie terms) would be wonderful.

Thank you all for your future support.

Thank you.

---

### Post by Sidk on 2006-04-12
Go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide") and follow the instructions where it says 

 Method 2: Generating/Installing Ubuntu packages for the newer 8.24.8 drivers in Breezy Badger.....  Installing the new driver

cd into the download directory and just cut and paste the lines in a terminal... It's that easy.

---

### Post by Sidk on 2006-04-12
Wow, I just noticed that updated the drivers today.

---

### Post by TriZz on 2006-04-13
[QUOTE=Sidk]Go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide") and follow the instructions where it says 

 Method 2: Generating/Installing Ubuntu packages for the newer 8.24.8 drivers in Breezy Badger.....  Installing the new driver

cd into the download directory and just cut and paste the lines in a terminal... It's that easy.[/QUOTE]

Thank you sir!!  I couldn't find an easy to follow tutorial anywhere - works like a charm!!

---

