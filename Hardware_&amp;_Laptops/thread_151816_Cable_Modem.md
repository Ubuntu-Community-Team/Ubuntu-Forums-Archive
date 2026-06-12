---
title: "Cable Modem"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by muu on 2006-03-28
I have a USB cable modem that slackware detects just fine.

When I ran the Ubuntu setup, it detected, but upon reboot into the installed system, no dice.  The exact same thing happens with debian.

So, whats goin on with the Ubuntu hotplug system, and how can I get this working?

Thanks!  //muu

---

### Post by rmjokers on 2006-03-29
The first thing to do in a situation like this is figure out what driver/module is missing.  Do you have an idea which module is needed in order to operate this hardware?  If you have your old configuration, take a look at output from lspci, lsusp, and lsmod and compare it with the new systems.  I am guessing that it might be as simple as running /sbin/modprobe with the appropriate module to get it working.  If you dont have that information available, a search on google might help you track it down.  Good luck!

---

### Post by muu on 2006-03-29
Yes, in fact, when I built a 2.4 kernel, there was only one kernel option under USB support and it was CDC ethernet support or something like that.

I believe in the 2.6 kernels there are 2 options that need to be installed and from what I can guess they are usbnet and cdc-acm.

I am new to installing modules but on Ubuntu 5.10 modprobe does not work, so I downloaded module-init-utils which is supposed to work on 2.6 kernels.  So right now I am switching from an old slackware partition on which I can see the internet and a new Ubuntu to try things on.

Any specific help would be appreciated, along with how to get these things automatically loaded.  TIA.

---

### Post by rmjokers on 2006-03-29
The only thing you should have to do to load those modules is:

sudo /sbin/modprobe usbnet
sudo /sbin/modprobe cdc-acm

If you dont have the modprobe binary, I'll have to check which package it is in...dont know off hand.  If those are the right modules, they should already be on your system for the current kernel under /lib/modules/

---

### Post by muu on 2006-03-29
OK, right, so I run:

sudo /sbin/modprobe usbnet

Kernel requires old modprobe, but couldnt run /sbin/modprobe.modutils: no such file or directory

I have downloaded module_init_utils*deb, which I think is the right package for Ubuntu 5.10, but now the thing is, I do not know how to load it because apt-get and the other installer want an internet connection.

Is there an easy command line kind of way to install this deb package?

Thanks!

---

### Post by muu on 2006-03-29
OK, I'll answer my own question

> sudo dpkg -i pkgname.deb

---

