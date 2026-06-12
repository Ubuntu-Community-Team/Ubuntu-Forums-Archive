---
title: "Infrared on Toshiba Tecra 8000"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by Snower on 2005-06-18
Does anybody know how to make the Infrared port work in ubuntu on a toshiba tecra 8000?
thx

---

### Post by lisje on 2005-09-04
currently in ubuntu 5.04 ... infra red just works on a tecra 8000 ... I've just checked on mine and it works.

I gave the following commands:
1. sudo apt-get install irda-utils
2. modprobe irda
3. sudo irattach irda0 -s

"sudo irdadump" gives me:

11:03:46.180144 xid:cmd c7663f69 > ffffffff S=6 s=0 (14) 
11:03:46.270116 xid:cmd c7663f69 > ffffffff S=6 s=1 (14) 
11:03:46.360109 xid:cmd c7663f69 > ffffffff S=6 s=2 (14) 
11:03:46.450093 xid:cmd c7663f69 > ffffffff S=6 s=3 (14) 
11:03:46.528607 xid:rsp c7663f69 < 00009782 S=6 s=3 Nokia 6021 hint=b125 [ PnP Modem Fax Telephony IrCOMM IrOBEX ] (27) 

you prob. found it allready by now, or gave up. But I have a off topic question tho'. Did you ever get the sound to work on your tecra?

---

