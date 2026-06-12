---
title: "Installation &quot;Loopy Tunes&quot;"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Forumuser on 2005-04-12
I am trying to install Kubuntu onto a Toshiba 2100CDT, but after booting up from the CD and after I hit "enter" for a default install, the computer begins to access the CD (I'm assuming to continue the install) -- but -- it then returns to the Toshiba setup screen, then back to the install screen from the CD, then the setup screen, etc. in an endless loop.

Anyone have any ideas or work-arounds?

---

### Post by direwolf on 2005-06-02
[QUOTE=Forumuser]I am trying to install Kubuntu onto a Toshiba 2100CDT, but after booting up from the CD and after I hit "enter" for a default install, the computer begins to access the CD (I'm assuming to continue the install) -- but -- it then returns to the Toshiba setup screen, then back to the install screen from the CD, then the setup screen, etc. in an endless loop.

Anyone have any ideas or work-arounds?[/QUOTE]

I have a 2100cdt and just did an install - 10mins ago - of Ubuntu Hoary Hedgehog 5.04 on my 2100cdt (same specs as yours). It all went fine except that I'm stuck (for now) on a 640x480 resolution. 

one way to get KDE desktop is on an existing Ubuntu install....
Install x86 Ubuntu 5.04 ... 
boot it up (or reboot once its fully installed) 
insert Kubuntu 5.04 CD
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
Session or Session Type choose KDE, then login.

and/or... your cd may be corrupted somehow? Just a guess, but try burning the installation cd again and re-trying.

---

