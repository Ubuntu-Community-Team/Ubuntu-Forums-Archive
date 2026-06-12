---
title: "Disable NIC?"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2006-12-05
My Dell X1 laptop has a on board Ethernet NIC that constantly flashes amber. The green light obviously is not flashing since there is no RJ-45 present. I would like to know if I should disable the NIC since I only use Intel wireless card built in.

If I want to disable this, should I do this via the BIOS or can this be done some how in Ubuntu?

---

### Post by zgornel on 2006-12-06
Disable it in bios if it is possible. It's the cleanest way. Btw, what exactly is wrong with the card ?

---

### Post by CarlosinFL on 2006-12-06
> **zgornel said:**
> Btw, what exactly is wrong with the card ?

There is nothing wrong with the NIC card...I just use wireless in my home. Now if I can just understand how the hell to get WPA working on Ubuntu ](*,)

---

### Post by zgornel on 2006-12-06
> **Carlwill said:**
> There is nothing wrong with the NIC card...I just use wireless in my home. Now if I can just understand how the hell to get WPA working on Ubuntu ](*,)

You shouldn't have problems ... there are loads of good tutorials on WPA on the forum. If you want the NIC not to be seen by the os (no ethX device attached), untick it's box in System/Administration/Networking.

---

### Post by CarlosinFL on 2006-12-06
Yes, I unchecked the "check" in "enable this connection" box and saved the location as "home" and it still flashes amber over and over.

I guess I need to do in BIOS.

Any links or suggestions for WPA setup on 6.10?

---

### Post by zgornel on 2006-12-07
For WPA:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) (search for WPA)
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

