---
title: "Apple Bluetooth keyboard"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by bated_breath on 2006-10-18
Hi All,

I am fairly new to ubuntu and i am trying to connect and apple bluetooth keyboard to my ibm z60m laptop.  I have searched these forums and the web and  have tried the following:

hcitool scan

(this returns a list of bluetooth devices one of which is the keyboard i am trying to pair with)

sudo hcitool cc 00:0A:95:46:50:39

I have located the default bluetooth pin (1234) from etc/bluetooth/pin.  So I then enter this pin on the bluetooth keyboard and hit the return key.  As soon as i hit the return key i get the following error message:

Can't create connection: Input/output error


Any help much appreciated ...

---

### Post by bated_breath on 2006-10-18
Is there a gui for pairing bluetooth devices?

---

### Post by bated_breath on 2006-10-19
found this excellent howto - problem solved!

[http://www.ubuntuforums.org/showthread.php?t=224673&highlight=apple+bluetooth](http://www.ubuntuforums.org/showthread.php?t=224673&highlight=apple+bluetooth)

---

