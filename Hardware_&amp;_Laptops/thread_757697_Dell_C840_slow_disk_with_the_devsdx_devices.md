---
title: "Dell C840 slow disk with the /dev/sdx devices"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by md4 on 2008-04-17
I have a Dell C840 and installed Ubuntu Hardy on it.
The hard disk "feels" slow, I checked with "sudo hdparm -Tt /dev/sda"

The response looks like
/dev/sda:
 Timing cached reads:    58 MB in  2.02 seconds =  28.76 MB/sec
 Timing buffered disk reads:   50 MB in  3.07 seconds =  16.28 MB/sec

This is slow.

I assume it is slow because it is not using the IDE interface.

I booted the laptop using a Knoppix 5.1 CD, it uses the IDE interface, so the device names look like /dev/hdx

I run the above command again, and now the speed is about 3 times more.

Question: is there a way to force Ubuntu Hardy 8.04 to use the IDE interface instead of the PATA

Would be great, if I could speed up the system

Thanks for any help.

---

### Post by md4 on 2008-04-20
Hi 
Please help me with this issue, I have two of these system for my kids and I would like them to use ubuntu.

find attached the out of lspci -vvvnnn

Many thanks for any help and suggestions.

---

