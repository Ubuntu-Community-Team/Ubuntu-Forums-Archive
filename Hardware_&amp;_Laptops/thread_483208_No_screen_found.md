---
title: "No screen found"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-06-24
For some reason, after the last upgrade from adept, I can't use my ubuntu :(

I get an blue screen with an error with the X server output that sais this:

bla bla bla
Parse error on line 53 of Section Input Device in file /etc/X11/xorg.conf
"..." in not a valid keyword in this section
(EE) Problem parsing the config file
(EE) Error Parsing the config file

Fatal Error:
No screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GMODE Failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

How can I install oro restore a new xorg.conf?

Help!

---

### Post by Neuralgia on 2007-06-24
no one? :(

---

### Post by Neuralgia on 2007-06-25
please, I'm stuck with windows :cry:

---

### Post by Neuralgia on 2007-06-26
please, can someone help me? I can't acces my files on my ubuntu... I'm getting frustrated

---

### Post by Neuralgia on 2007-06-29
ok, how can i edit my xorg.conf without the graphical interface? Please help!!!

---

### Post by releehw on 2007-07-01
Hi:

I'd backup xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

Then try :

sudo pico /etc/X11/xorg.conf

I think pico should be easy to use even if you've never used it before.

Assuming you find the syntax error (or whatever troubles X) on line 53, correct and save your xorg.conf file, you may need to:

sudo killall gdm
sudo gdm

to test.

---

### Post by Neuralgia on 2007-07-01
i ended up using

> sudo dpkg-reconfigure xserver-xorg

thanks

---

