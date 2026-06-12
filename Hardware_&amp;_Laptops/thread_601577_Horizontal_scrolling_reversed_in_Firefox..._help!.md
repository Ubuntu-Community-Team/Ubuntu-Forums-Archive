---
title: "Horizontal scrolling reversed in Firefox... help!"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by JPorter on 2007-11-03
I'm having a weird issue with the scrolling function of my Trackpoint on my Thinkpad T60.

I've configured xorg.conf so that everything works properly per the instructions on thinkwiki, scrolling works as expected in Gnome.

The issue is only in Firefox... the horizontal axis seems reversed for scrolling only in that application, i.e. I scroll to the right and the screen moves left.  This behavior does not exist in any other application.

Can anyone help?  Is there an axis reversal control in Firefox?  I was unable to find anything relevant in about:config.


Thanks in advance for any help you can provide!

---

### Post by JPorter on 2007-11-11
Anybody?  Bueller?

---

### Post by Whiffle on 2007-11-11
in about:config

change

mousewheel.horizscroll.withnokey.numlines

to 1

---

### Post by JPorter on 2007-11-11
Whiffle, you are a genius.

Thank you!!

---

