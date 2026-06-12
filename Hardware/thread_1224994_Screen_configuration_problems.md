---
title: "Screen configuration problems"
date: 2009-07-28
forum: Hardware
---

### Post by CaesarsAdvocate on 2009-07-28
Hello,

I followed the instructions in Ubuntu Beginners Guide to import screen configuration from manufacturer disk.
I used:

gksudo displayconfig-gtk

and imported the *.inf file for my monitor from disk (Samsung SyncMaster T220)

I then selected my model (Samsung -> etc.) in displayconfig-gtk.

After reboot, I could no longer set the screen to its full resolution (1680x1050). When I tried to redefine the model to Generic -> Plug and Play it would allow me to use only ridiculously low resolutions.

Since installation the configuration had been Generic -> Plug'n Play and it worked great, correct resolution and everything, until now.

How can I restore my previous configuration?

R.

---

### Post by CaesarsAdvocate on 2009-07-29
The solution is embarrassingly easy.

As suggested in the commented out text in /etc/X11/xorg.conf, I ran:

sudo dpkg-reconfigure -phigh xserver-xorg

logged out, logged back on, and order was restored.

Thanks,

CA.

---

