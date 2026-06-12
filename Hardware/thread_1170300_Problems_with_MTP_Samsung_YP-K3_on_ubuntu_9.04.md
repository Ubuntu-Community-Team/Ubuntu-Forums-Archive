---
title: "Problems with MTP Samsung YP-K3 on ubuntu 9.04"
date: 2009-05-26
forum: Hardware
---

### Post by Rintxo on 2009-05-26
Hello
 I'm using gnomad2 on Ubuntu 9.04, to be able to connect to my MTP device Samsung YP-K3. The device is detected, I can see it in the desktop.
  Unfortunately, I am unable to transfer audio tracks on it. So when I do a mtp-detect in the terminal, here are the errors I get. 

 The errors:


~$ mtp-detect
libmtp version: 0.3.3
 Listing raw device(s)
   Found 1 device(s):
   Samsung: YP-K3 (04e8:5081) @ bus 0, dev 3
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.




I have proved to do that in other ubuntu versions like, 8.10 or 8.04 and I have no problems. Furthermore, I have tried to do that in xubuntu 9.04 and all is OK.
Can anybody help me? Thanks.

---

### Post by hotweiss on 2009-05-26
You have to change the firmware in your MP3 player:

[http://forums.gentoo.org/viewtopic-t-556945.html](http://forums.gentoo.org/viewtopic-t-556945.html)

---

