---
title: "AMD64-microcode 12.04 clashes with linux-firmware"
date: 2014-01-05
forum: Hardware
---

### Post by dsluser on 2014-01-05
Hi All, 

I've recently installed 12.04 on a lenovo G505 with an AMD A4-5000. On booting I get an error message - Failed to load amd64-ucode/microcode_amd_fam16h - Cannot resolve 

I've tried installing the microcode using apt-get but I only see intel microcode (using 3.8.0-35-generic)

I've tried installing the deb from [http://archive.ubuntu.com/ubuntu/pool/multiverse/a/amd64-microcode/](http://archive.ubuntu.com/ubuntu/pool/multiverse/a/amd64-microcode/) but I get an error about a clash with linux-firmware already containing fam15h and a broken package warning. 

The only actual issue I've seen so far is graphical corruption on reboot (screen flickering and colours bleeding, like a dying graphics card)

Has anyone successfully gotten the correct microcode for fam16h installed in 12.04?

**EDIT** I'm also seeing occassional black screen flicker on the desktop.

---

### Post by Yellow Pasque on 2014-01-05
AFAICT, no such file (amd_fam16h) exists right now. The .deb you're trying to install doesn't have it, so that's a dead end.
If you're not experiencing issues, the error mesage is annoying, but harmless.

---

### Post by king.of.random on 2014-01-05
Out of interest have you tried using the latest Ubuntu 13.10?? I only ask as if this is a newly introduced laptop then you may have bug fixes that will correct this. The next long term support 14.04 is due out in April this year so if that's what you would prefer then it's not long to wait.

---

### Post by dsluser on 2014-01-05
Thanks for the replies, 

I've tried 13.10 but I get the black screen on boot. I've also tried Fedora 20(Gnome and KDE), Mint 16 (Cinnamon and KDE) and openSUSE 13.1. Ubuntu 12.04 is the only distro that's even remotely stable. I'll wait for 14.04 and cross my fingers. I'm seeing some slight graphical corruption in places but nothing I can't put up with, then again I have yet to run any intensive applications. I'll post back in a few days once I have my IDEs set up and can run a few builds

---

### Post by Yellow Pasque on 2014-01-06
For reference: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1252952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1252952)
Alarmist error message should disappear kernel 3.13: [https://github.com/torvalds/linux/commit/11f918d3e2d3861b6931e97b3aa778e4984935aa](https://github.com/torvalds/linux/commit/11f918d3e2d3861b6931e97b3aa778e4984935aa)

---

### Post by dsluser on 2014-01-06
Thanks for the information and help, it's much appreciated

---

