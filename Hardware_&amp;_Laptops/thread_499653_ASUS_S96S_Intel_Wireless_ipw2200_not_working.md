---
title: "ASUS S96S Intel Wireless ipw2200 not working"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by frobroj on 2007-07-12
Hi all!!! Curious if anyone has gotten the wireless on an ASUS S96S working properly. 
I know its an IPW2200 but I can't get the system to see it. I have looked on Intels site and the ASUS site to no avail. I expected to find linux drivers for the subsystem on the intel site but there wasn't any just vista...I did try to install the intel IPW2200 drivers but I cant get them to compile. I would think that if Ubuntu doesn't see the appropriate device that I won't have any luck with the drivers anyway. Am I wrong on this? 

lspci:  04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
lspci -vnn:
04:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4229] (rev 61)
        Subsystem: Intel Corporation Unknown device [8086:1100]
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at fbefe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>


Thanks in advance for any help and or insight into this issue...

jm

---

### Post by frobroj on 2007-07-19
Anyone? buehler? buehler? Can anyone confirm or deny my assumptions on the lspci?
Thanks!

---

### Post by justsee on 2007-08-04
It might be worth having a chat to Dale who runs [http://efficientpc.co.uk](http://efficientpc.co.uk) . The model he sells is the ASUS S96S, so I'd suspect he could help you. He seems like he knows his stuff based on this thread: [http://ubuntuforums.org/showthread.php?t=335499](http://ubuntuforums.org/showthread.php?t=335499) and he seems to want to help the community...

---

### Post by frobroj on 2007-08-04
Sweet. Thanks for the reply I will give Dale a try. Much appreciated!
jm

---

### Post by Syke on 2007-08-04
I'd be surprised if you got an S96S with a 2200. It's more likely a 4935. 

You could just switch to a 3945 card. They're pretty cheap and easy to swap out, and the drivers are great.

---

### Post by frobroj on 2007-08-07
Sweet! Looks like you are right on... I am a dope! I should have taken that back panel off sooner. It is a 4965AGN. I will see if I can find a 3945. Really all I care about is ABG. 
Thanks for the insight.
jm

---

### Post by frobroj on 2007-08-10
Well I just gave Gutsy Tribe4 Alternate a try and it worked. Looks like they have incorporated the latest drivers... WOOHHOOOO! 
jm

---

