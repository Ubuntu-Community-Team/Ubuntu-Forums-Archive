---
title: "Clean Print Heads on HP Deskjet 930C"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by jacksonyee on 2005-07-25
Greetings,

I'm trying to figure out how to clean my print heads in Linux for my HP Deskjet 930c.  I have found the package escputil for Epson printers, but have found nothing comparable for HP printers.  Is there such a utility in Linux?

---

### Post by JNik on 2006-03-21
I am looking for the same thing but no luck yet :(


I found [this]("http://hpinkjet.sourceforge.net/install.php"), but the instructions are not correct (there is no hp-setup in the package I downloaded from synaptic).


If that was working I read somewhere that all you have to do is something like this

# hplip_clean -dhp:/usb/Deskjet_930?serial=MY48Q1Y3N5046W

# hplip_clean -dhp:/usb/Deskjet_930?serial=MY48Q1Y3N5046W -v2

---

