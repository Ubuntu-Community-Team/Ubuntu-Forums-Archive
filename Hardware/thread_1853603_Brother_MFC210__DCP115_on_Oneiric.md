---
title: "Brother MFC210 / DCP115 on Oneiric"
date: 2011-10-02
forum: Hardware
---

### Post by rafaellaguna on 2011-10-02
Does anybody installed the drivers for the Brother DCP115 or MFC210 on Ubuntu Oneiric? This is what I've made:

[LIST]
[*]installed the brscan2 driver
[*]added user to group scanner
[*]added this to /lib/udev/rules.d/40-libsane.rules:

[INDENT][/INDENT]# Brother scanners
[INDENT][/INDENT]ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
[*]restarted the OS (of course)
[/LIST]
Result: No scanner found

Does anyone has the same problem? I'm thinking the removal of HAL may cause this, but I'm not sure (those lines are for Ubuntu 11.04, it may change in Oneiric).

Thanks in advance.

---

### Post by Redblade20XX on 2011-10-03
Hmmm....did you make sure you fulfilled the pre-reqs before installation?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#101)

-Red

---

### Post by rafaellaguna on 2011-10-03
Yes, and installed csh, checked groups and port permissions, etc. Somethings wrong with Oneiric and Brother, I've installed again this printer on Natty and it works perfectly.

---

### Post by rafaellaguna on 2011-10-17
Ok, let's go with the magic.

- First you must install the brscan2 driver from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan2"):

- Second you must edit /lib/udev/rules.d/40-libsane.rules and add this as the last scanner (after HP ones, f.ex.)

[INDENT]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/INDENT]

- Third execute all this in a terminal

[INDENT]sudo cp /usr/lib64/libbrscandec2.so.1.0.0 /usr/lib64/libbrcolm2.so.1.0.1 /usr/lib64/libbrcolm2.so /usr/lib64/libbrscandec2.so.1 /usr/lib64/libbrscandec2.so /usr/lib64/libbrcolm2.so.1 /usr/lib

sudo cp /usr/lib64/sane/libsane-brother2.so.1.0.7 /usr/lib64/sane/libsane-brother2.so.1 /usr/lib64/sane/libsane-brother2.so /usr/lib/sane

sudo echo 'SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"' >> /lib/udev/rules.d/50-udev-default.rules[/INDENT]

This will relocate the libraries to the right place and enable every user to scan.

Too tricky, dear Ubuntu and Brother people. Things like this make Ubuntu harder to use for newbies (and for me).

Oops, I'm THAT people of Ubuntu!

---

### Post by roger_1960 on 2011-10-17
Hi

I think you only need the terminal commands if you have multiple users.  Otherwise just the first and second items in the above are required.

---

### Post by rafaellaguna on 2011-10-17
Ubuntu has something like "one user and a half". The initial user has a superuser password (fake root) without being a root, so really the system is multiuser enabled.

And the third one is requiered as the libraries cannot be find by the sane parser, unless you're on Natty or earlier. This is a significative change of "libusb" devices.

---

