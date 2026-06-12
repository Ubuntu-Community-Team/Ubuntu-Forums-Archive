---
title: "X window system doesn't load"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by Shinta on 2005-09-13
My video card is a Aopen Geforce 6800LE, when installing multiple distributions i don't encounter noticable problems (except with Fedora Core 4, that didn't install at all) but when I finally try to boot this happens:

I see the login screen, I'm able to fill in my user name and the password and then i press enter, then I see a black cross appearing and a (depends on the distro) soft blue or green color. The cross , which seems to be the mouse cursor changes into a pointer as expected but then nothing happens anymore.
I have this even background color with a cursor (which is movable without problems) and nothing else.

When I reboot i notice that the login screen too is rather fragile, when u vlick around a little bit to choose the graphical interface (KDE, Gnome, ..) the system often crashes.

Thx in advance

---

### Post by mlomker on 2005-09-13
Try changing to the VESA video driver as a test.  Select 'rescue' from the grub menu and login.

cd /etc/X11
nano xorg.conf

Look for **Section "Device"** and change the Driver= line to read vesa from whatever it says now.

---

### Post by Shinta on 2005-09-14
I don't seem to find the xorg.conf file, i do have found de xorg.cf file, i presume that that's the same but the file looks like a source code and it counts more than 1500 lines. 
Do I have to search through all those lines to find the word device or is there a search function in the nano editor to find the word "Device".

Any other suggestion can be useful.

---

### Post by mlomker on 2005-09-15
If you do not have a /etc/X11/xorg.conf file then you've somehow removed your desktop altogether.  You'll want to **apt-get install --reinstall ubuntu-desktop**(or kubuntu-desktop) in an attempt to reinstall everything.

---

