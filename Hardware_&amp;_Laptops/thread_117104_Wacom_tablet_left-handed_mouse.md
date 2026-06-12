---
title: "Wacom tablet: left-handed mouse"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by cornelis1 on 2006-01-14
I have recently bought a Wacom Volito tablet and succesfully, thanks to this forum, managed to get it working under Breezy. (Including pressure sensitivity) The only thing I like to accomplish now, is to make the mouse that came with the tablet (and which is not my default mouse) work as a left-handed mouse, leaving my default mouse working as a right-handed mouse. Can this be done?

---

### Post by cornelis1 on 2006-01-21
Found out how to do it!

After some searching on the web I found this site very helpfull:

[http://www.faqs.org/docs/Linux-HOWTO/Wacom-Tablet-HOWTO](http://www.faqs.org/docs/Linux-HOWTO/Wacom-Tablet-HOWTO)

To achieve my goal I had to install a program called “xinput” (it is in “Universe”) and run:

[B]sudo xinput set-button-map cursor 3 2 1
[/B]
Now I had a left-handed mouse with my Wacom tablet, while my other mouse was still right-handed.

The mouse-button changes, made by xinput, however are not permanent so they have to be set every time X starts up.  To do this automatically I put:

** /usr/X11R6/bin/xinput set-button-map cursor 3 2 1 **

in the list of programs to start up every time I log into gnome (sysytem > preferences > sessions > start programs).

---

### Post by 18nikko on 2006-01-21
Hi,
Your post is a big relief. I just bought a wacom tablet for my son and he is a lefty. It is good to know it works with ubuntu. What software does yours play well with?

Nicholas

---

### Post by cornelis1 on 2006-01-23
I mainly use it with the Gimp, works really well with pressure sensitivity. Both pen and mouse work fine as pointer divices in gnome.

---

