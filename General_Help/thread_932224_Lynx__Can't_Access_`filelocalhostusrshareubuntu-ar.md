---
title: "Lynx  Can't Access `file://localhost/usr/share/ubuntu-artwork/home/index.html'"
date: 2008-09-28
forum: General Help
---

### Post by felixdzerzhinsky on 2008-09-28
I removed gnome and put LXDE on my eeepc4g. I get the following error with lynx.

> ~$ lynx

Can't Access `file://localhost/usr/share/ubuntu-artwork/home/index.html'
Alert!: Unable to access document.

lynx: Can't access startfile 

What do I need to do?

---

### Post by fsmithred on 2008-09-28
If you got there by typing 'g' and then typing in that address, drop the first part, and just type /usr/share/ubuntu-artwork/home/index.html

---

### Post by alexanderpas on 2008-10-17
This is a known bug.
[https://bugs.launchpad.net/ubuntu/+source/lynx/+bug/220080](https://bugs.launchpad.net/ubuntu/+source/lynx/+bug/220080)


> **felixdzerzhinsky said:**
> What do I need to do?
install the ubunu-docs package as a temporary solution.

---

### Post by meditatingfrog on 2009-09-30
I had this bug.  I typed:

sudo mkdir -p /usr/share/ubuntu-artwork/home
cd /usr/share/ubuntu-artwork/home
sudo nano index.html
cntrl-o.

then lynx starts with a blank index.html file

---

