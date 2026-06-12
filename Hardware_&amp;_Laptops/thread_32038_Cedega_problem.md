---
title: "Cedega problem"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by computerguy867 on 2005-05-05
Hello all, 

I have just installed cedega and then Knights of the Old Republic II.  After the install, 
when I go to run the executable to start the game, the screen flashes to black and displays "Video Mode not Supported".  Is this an x configuration thing or a cedega thing?  Any help is greatly apprechiated!

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=computerguy867]Is this an x configuration thing or a cedega thing? [/QUOTE]

X

Your monitor must be incorrectly configured....

---

### Post by computerguy867 on 2005-05-05
Thanks for the reply.  I checked my xorg.conf file, and my monitor settings are 

Section "Monitor"
        Identifier      "F227B"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160

Now, im not sure about the last two options but when I run

dpkg-reconfigure xserver-xorg

and choose the simple monitor setup thats what it gives me.  Is it possible that those options have something to do with it?  I have a Daewoo 17 inch LCD by the way.

---

