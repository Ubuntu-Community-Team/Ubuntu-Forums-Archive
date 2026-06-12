---
title: "wireless not working with 11.10"
date: 2011-10-22
forum: Hardware
---

### Post by darkstar2001 on 2011-10-22
it worked fine when 10.10 was installed. 11.04 and 11.10 both show wireless unavailable....it will not turn on. 
 
Lenovo b 575 AMD Vision cpu/video combo. 
 
Any ideas????

---

### Post by darkstar2001 on 2011-11-03
So, no one has had this problem?? I can't get ubuntu to recognise a usb n wireless adapter when I plug it in. It just says that "wireless has been turned off in software."
 
Help please!!!

---

### Post by hydroxph on 2011-11-03
Has your wireless card worked with any of the older versions of ubuntu?

---

### Post by TBABill on 2011-11-03
You need to provide hardware information in order to better get to the root of the problem. Can you open a terminal and provide the outputs of ```
lspci
``` and ```
lsmod
``` From there it may be easier to get to the answer by knowing what the device is and if the right driver is active for it.
 
There have been regressions in 11.04 and 11.10, particularly with Broadcom devices. Specifically, the BCM4311, 4306 and 4318 have had many posts for assistance. I'm sure there are others as well.

---

### Post by gurusanthosh1989 on 2011-11-03
[FONT=Comic Sans MS]Hey guys..

Recently before 2 weeks i installed ubuntu 11.10..
the main problem is with wireless connection.. 
i am using DELL 4010 laptop..
Wireless card is BCM4313(14e4:4727)..

i think there is a problem with loading drivers..

i googled and did something but not cleared..
i want to know what to be blacklisted in /etc/modprobe.d/blacklist.conf and which driver is perfect for my lap??..

i need some help from you guys plzzzzzzzzzzz

Regards
Santhosh[/FONT]

---

### Post by TBABill on 2011-11-03
guru, could you open a new thread with your problem listed? You won't likely get much help in the middle of someone else's thread and better exposure will get you back up and running faster.
 
My understanding is you should be using the open source brcm80211 driver so the modules blacklisted should probably be the b43, b43legacy, ssb and wl. If you have tried to install the b43 or STA driver (which uses the wl module), that may be why it's not working because either of those installed would blacklist the brcm80211 I think.

---

### Post by darkstar2001 on 2011-11-05
> **TBABill said:**
> You need to provide hardware information in order to better get to the root of the problem. Can you open a terminal and provide the outputs of ```
lspci
``` and ```
lsmod
``` From there it may be easier to get to the answer by knowing what the device is and if the right driver is active for it.
 
There have been regressions in 11.04 and 11.10, particularly with Broadcom devices. Specifically, the BCM4311, 4306 and 4318 have had many posts for assistance. I'm sure there are others as well.
 
I will get the info.  Like I said, it all worked fine with 10.10.  Just need to find the missing piece.

---

### Post by darkstar2001 on 2011-11-05
Here in the listing for lspci and lsmod....

[ATTACH]206385[/ATTACH]
[ATTACH]206386[/ATTACH]

---

### Post by darkstar2001 on 2011-11-05
Sorry bout the duplicate info in the files...

---

