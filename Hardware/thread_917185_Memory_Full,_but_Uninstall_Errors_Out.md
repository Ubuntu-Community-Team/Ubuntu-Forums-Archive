---
title: "Memory Full, but Uninstall Errors Out"
date: 2008-09-11
forum: Hardware
---

### Post by Erdr1ck on 2008-09-11
I just installed Ubuntu on my shiny new Asus EEE PC (model 901), and quickly ran out of space on the main (4 gb) drive.  I try to unistall stuff and I get an error message saving I need to do "dpkg --configure -a" from the command line, but when I try to do that, I get an error message saying I don't have enough space.  Is there an easy way out of this pickle?

Also:  Given that I'm just using the machine to take notes, surf the web, and prototype some programs, any fat juicy programs I can uninstall to clean things up?  I intend to move to a stripped down Xubuntu install once I'm more comfortable with Linux, but until then I need to make my Ubuntu/Gnome setup a little more light weight.

---

### Post by DoctorMO on 2008-09-14
you could get rid of the deb cache in /var/cache/apt/archives/

> sudo rm /var/cache/apt/archives/*.deb

---

