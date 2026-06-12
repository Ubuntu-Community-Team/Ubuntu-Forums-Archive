---
title: "Boot Floppy Grub Installation"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by nicom on 2006-02-12
Hello Ubuntu people,

I am new to Ubuntu. I have up till now been playing with the small versions of linux (dsl and puppy) on an old computer (p133). I am now looking at using Ubuntu on a real computer (2.4 GHz, 512 MB) although installing it in a partition at the back of a large hard disk with XP as the main OS.

I am being very cowardly about it and trying to boot Ubuntu from a floppy disk as the grub boot rather than modify the MBR. I have gone through the installation proceedure and created the grub boot floopy but the installation does no appear to proceed from there. Booting on the floppy will start up Ubuntu but only in text mode. X does not start.

I tried dpkg-reconfigure xserver-xfree86 put was told that Xserver is not installed.

Can anyone help?

---

### Post by heimo on 2006-02-12
Try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nicom on 2006-02-12
Thanks for the suggestion.

I gave it a try but the same thing. Something like "xserver-xorg not installed".

The fact that the installation did not proceed beyond the point of creating the grub boot makes me think there is some further installation required that did not happen because it required the floppy to reboot during the installation process.

---

### Post by heimo on 2006-02-12
Hmm.. Yeah. But you're able to boot it to command line (not just booting to some kind of rescue disk)? I'd probably run:
```
sudo dpkg --configure -a
```
to make sure all packages are configured, and then:
```
sudo apt-get install ubuntu-desktop
```
to get full Gnome desktop environment and whole lot of applications installed. (assuming your network connection was configured and works)

---

### Post by nicom on 2006-02-13
Thanks Heimo,

That did the trick. I am now up and running on Breezy.

By the way, was it necessary to apt-get the ubuntu-desktop from the internet. Could I not have got it from the CD?

---

### Post by heimo on 2006-02-13
Good to hear. :) No, actually it wasn't neccessary to use internet versions, install CD contains everything needed for default desktop, Gnome environment and other applications. But at least this way you got the latest versions (for Breezy - versions of some packages in install CD are old). I believe that install CD gets added to repositories (/etc/apt/sources.list) and is used by default if no more recent versions of packages are available. Also the usual install process upgrades all packages if internet connection is available during install.

Oh, and welcome to Ubuntu forums. :) Enjoy your Breezy Badger and be sure to check how to upgrade to Dapper Drake 6.04 late April. It'll be even better.

---

