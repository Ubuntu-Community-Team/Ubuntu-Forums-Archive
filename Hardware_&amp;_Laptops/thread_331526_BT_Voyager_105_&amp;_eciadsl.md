---
title: "BT Voyager 105 &amp; eciadsl"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by MT1 on 2007-01-04
:confused: (utter newbie) I've been following instructions from Keir Thomas's *Beginning Ubuntu Linux*on how to get the BT Voyager 105 running with Ubuntu. I've got the Edgy release, though I don't think that would matter. I've downloaded the eciadsl_synch-bin file, the eciadsl-usermode file and the pppoe file (all on Windows); transferred the lot to my home folder on Ubuntu, unpacking when needed. All have the right extensions etc.: I have no reason to doubt that I've got the right files in the right places. However, when I run the modem configuration program, it responds that the eciadsl config file has a syntax error: an unexpected "(". I'm not a programmer, but I've searched through the file and found no opening bracket without a corresponding closing bracket - so I'm mystified. It was the latest versions of all the relevant files that I used, so there are no later versions with bug fixes to be had. Any help would be very, very welcome. 

Thanks in advance.

---

### Post by teaker1s on 2007-01-05
make sure you have 
**build-essential** installed before compiling. 
Also I'm not a fan of bt voyager 105 (globespanvirata)
as they are buggy, a thomson speedtouch 330 is much better.
Though there is an ARP issue currently with pppd package this will affect all brands of modem I suspect as I hit a brick wall with a modem that would connect but no further due to ARP problem.
if you can afford to by a router it's the way forward;)

---

