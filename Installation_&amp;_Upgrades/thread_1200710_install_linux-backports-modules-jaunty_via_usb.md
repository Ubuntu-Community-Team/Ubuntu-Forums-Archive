---
title: "install linux-backports-modules-jaunty via usb"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by mjm1049 on 2009-06-30
Hello,
 
Does any one know if the linux-backports-modules-jaunty update can be transferred to the computer via usb and then installed that way instead of using the apt-get command?
 
I'm extremely new to linux and the apt-get functionality and I need to update a computer to make wireless work without having a wired internet connection.
 
If it can be done this way can you point me to where I can get the files and how to access them via the terminal once I transfer them to the machine?
 
Your help is greatly appreciated.
 
Thanks,
mjm1049

---

### Post by krazymelvin on 2009-07-01
Download the following packages and install them in that order:

[LIST=1]
[*][http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-13-generic](http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-13-generic)
[*][http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-13-generic](http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-13-generic)
[*][http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty-generic](http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty-generic)
[*][http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty](http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty)
[/LIST]

There are dl links for both 32 and 64 bit.


Again the order is:
[LIST=1]
[*]linux-image-2.6.28-13-generic
[*]linux-backports-modules-2.6.28-13-generic
[*]linux-backports-modules-jaunty-generic
[*]linux-backports-modules-jaunty
[/LIST]

After installing all the packages just restart your pc and all should be well.

---

### Post by Kansasguy on 2009-08-14
Krazy,

I have a similar problem, new ASUS netbook that came with XP, now dual booted with Jaunty.  Kernel 2.6.28.11    No wireless or wired, (though it works on XP.  Would love to follow your instructions, but would have to be downloaded on another computer> USB>transferred.

Also, not sure how to "install"    TIA  ht

---

### Post by believekevin on 2009-08-27
thanks, folks! this was very helpful and wifi is now working on our new asus eee pc 1005ha.

quick note, there are newer packages in the repository now so we had to download and install:

linux-backports-modules-2.6.28-15-generic
[http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-15-generic](http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-15-generic)

linux-image-2.6.28-15-generic
[http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-15-generic](http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-15-generic)

we copied all of these files onto a flash drive and installed them in the following sequence by double-clicking in gnome:

   1. linux-image-2.6.28-15-generic
   2. linux-backports-modules-2.6.28-15-generic
   3. linux-backports-modules-jaunty-generic
   4. linux-backports-modules-jaunty


thanks again!

---

