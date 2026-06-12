---
title: "Mutouch Y reversed in Hardy"
date: 2009-12-08
forum: Hardware
---

### Post by grackleman on 2009-12-08
I'm trying to get a Microtouch screen working with Mutouch in Hardy. The Y axis is reversed. I've tried "InvY" and "SwapY" but they do nothing. In open Suse switching the MaxY and MinY values worked but it doesn't in Hardy.
Any ideas
Thanks

---

### Post by grackleman on 2009-12-11
Problem solved
I uninstalled the version installed by Synaptic and download and installed version 1.2.0-3 and reversing MinY and MaxY solved the problem.

---

### Post by seuchato on 2009-12-13
> **grackleman said:**
> Problem solved
I uninstalled the version installed by Synaptic and download and installed version 1.2.0-3 and reversing MinY and MaxY solved the problem.
Can you kindly indicate wher you downloaded what driver?

The only one I foud is this:
[http://packages.debian.org/lenny/i386/xserver-xorg-input-mutouch/download](http://packages.debian.org/lenny/i386/xserver-xorg-input-mutouch/download)

if I install it like described here:

[https://help.ubuntu.com/community/UbuntuBackports#Installing%20a%20single%20package](https://help.ubuntu.com/community/UbuntuBackports#Installing%20a%20single%20package)

sudo dpkg -i [xserver-xorg-input-mutouch_1.2.0-3]("http://ftp.de.debian.org/debian/pool/main/x/xserver-xorg-input-mutouch/xserver-xorg-input-mutouch_1.2.0-3.dsc").deb
sudo apt-get -f update

then restar Xorg
sudo killall gdm
sudo gdm

and touch the screen, the system immediately freezes.

Would be extremely happy to get this solved.

greets
chris

---

### Post by grackleman on 2009-12-13
That's the site I went to and I think I used the first one under North America. 
Any should work as long as you can download and save this:
xserver-xorg-input-mutouch_1.2.0-3_i386.deb

I just double clicked on it and let the package installer install it. Reverse the values of "MinY" and "MaxY" in xorg.conf.

First I uninstalled the version that Synaptic had found.

I'm using Hardy 8.04.

---

