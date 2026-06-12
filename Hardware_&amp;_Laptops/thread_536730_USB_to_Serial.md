---
title: "USB to Serial"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by will71110 on 2007-08-28
How can I test to see if my USB to Serial adapter is acctually working.  Also what can I use to console into a device using this? (Like a Cisco device.)

BTW my USB to Serial adapter does not say who it is made by nor has a part number :mad:

EDIT: I did a lsusb.  I have a Prolific PL2303 USB to Serial

---

### Post by davidsrsb on 2007-08-28
The PL2303 works with Ubuntu

To test it use a terminal program and link TXD (pin3) to RXD (pin2) with a piece of wire

---

### Post by will71110 on 2007-08-28
What do I use software wise?  Like in windows there is hyperterminal. Is there one built in or do I have to search for one?

---

### Post by orotrev on 2007-08-30
Did you find "minicom"? I have used it a few times to connect to Cisco devices and servers.

---

### Post by will71110 on 2007-08-30
I'm going to use putty.  I use it on windows all the time.  Didn't realize you can use it though serial on Linux :)

---

