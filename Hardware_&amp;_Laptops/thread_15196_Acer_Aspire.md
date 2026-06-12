---
title: "Acer Aspire"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by recmar on 2005-02-12
I'm lookin for happy ubuntu-acer aspire users. Have some graphics problems. I've tied find help but with no answers.

---

### Post by inhetep on 2005-02-16
I am a sort of happy Acer Aspire 1355 LMi user. So far ubuntu is running well graphics  (ATI Mobile 9200) included.
What is your problem?

---

### Post by Jspired on 2005-02-16
I've also installed on an Acer.  What model/make are you running and what are your problems?

---

### Post by hardjowikromo on 2005-02-17
Acer Aspire 1352XC

Every hardware is working fine here  :)

O I am sooooo happy :D

---

### Post by faqpete on 2005-02-18
ACER 1522 WLMI
Everything is working fine (incl. IPN2220 Wireless LAN - thx. to ndiswrapper) except my nvidia graphics card (5700 go) ... @gdm the resolution is higher than my monitor resolution supports - looks like the login-screen is divided into two or three parts with 2 mouse-pointers ... but after login, I can use my resolution (1280x800) without any problems ;-)

I find it very interesting that when I'm using the "nv" - driver in the XF86Config-4 instead of "nvidia" I do not have any problems @gdm and I can use 1280x800 without any problems too - surly without 3d-acceleration ;-)

---

### Post by recmar on 2005-02-18
Hello fellas!
I'm running Aspire 1353LC with VIA/S3 KN/KM400 graphics on board and using GUI is just killing me. Screen drawing is going very slow, i get all kinds of artifacts while draging windows around and general mouse responce seems slugish. I thought that maybe i wasn't using the correct video driver but only vesa seems to work with my VIA. Where the problem can be?

---

### Post by inhetep on 2005-02-20
Did you look at the VIA arena driver website, might give you some clues. 
[http://www.viaarena.com/default.aspx?PageID=2](http://www.viaarena.com/default.aspx?PageID=2)
[http://www.xfree86.org/current/RELNOTES3.html#14](http://www.xfree86.org/current/RELNOTES3.html#14)

also have look at the following pages:
[http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html)
[http://www.it-west.de/service-aspire1353lc_en.html](http://www.it-west.de/service-aspire1353lc_en.html)
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)

It helped me setting Linux up on a Travelmate with a via graphic card.

BTW, do you use an external mouse or the touchpad?

---

### Post by recmar on 2005-02-21
I've tried to find something interesting on VIA and linux-on-laptops sites but with no success. Recently I've tried Knoppix (which is basically debian - as ubuntu is) and graphix worked just excellent (vesa driver). I was wondering is the problem can be with Gnome configuration? Knoppix uses KDE.
Talking about pointers - I use both: usb logitech mouse and touchpad.

---

### Post by inhetep on 2005-02-23
The problem should not be GNOME. Did you by any chance save the XF86config-4 file from your ubuntu installation (mostlikely not). If yes, u might want to compare this file with your Knoppix file. Maybe you you will see some differences.
With respect to your mouse problems,  I use the same combination and it works with out problems. Maybe you can modify the input device section in your XF86config file.
What version of ubuntu do you use (Hoary or Warty). I had some problems getting things running using Hoary (still testing stage).

---

### Post by cyu021 on 2005-03-12
how about aspire 1680 series ?
I am running ubuntu (hoary, 5.04, kernel-2.6.10-4) on a 1682, everything seems all right except for "battery status", "sound", and "wireless NIC"

---

