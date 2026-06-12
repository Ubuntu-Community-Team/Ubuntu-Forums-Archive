---
title: "White screen after update"
date: 2009-10-17
forum: Hardware
---

### Post by naschas on 2009-10-17
Hi everyone,

Hoping you can help me out. Update manager updated the intel-xorg driver on the latest update on my 9.04 system, HP laptop. After rebooting, the screen is just white with only the mouse visible. The system is running and all the sounds are working and if I click in the general area of the shut down the system shuts down or suspends.

Any ideas? My guess would be to roll back the driver somehow...

---

### Post by edin9 on 2009-10-17
> **naschas said:**
> Hi everyone,

Hoping you can help me out. Update manager updated the intel-xorg driver on the latest update on my 9.04 system, HP laptop. After rebooting, the screen is just white with only the mouse visible. The system is running and all the sounds are working and if I click in the general area of the shut down the system shuts down or suspends.

Any ideas? My guess would be to roll back the driver somehow...

 Does your PC have ATi graphics?

---

### Post by naschas on 2009-10-18
Hi edin9,

No, its using the Intel graphics chip which I understand is not ATi.

Thanks.

---

### Post by greg batmarx on 2009-10-18
same problem with me...
it seems that this upgrade broke something...
can someone please help?

---

### Post by greg batmarx on 2009-10-18
As for now,I run kde after a long time using konqueror and trying to find an answer for this problem...
The problem affects only gnome and the intel gpu obviously...

---

### Post by naschas on 2009-10-18
Well i got back to my desktop by hitting ctrl+alt+f2 then in the terminal typing "pa aux" then look for the PID for compiz, kill it by using "kill <PID>", hit ctrl+alt+f7.

I then went reinstalled the older intel driver and removed the new one.

---

### Post by greg batmarx on 2009-10-18
how did you reinstall the old driver and removed the new one?
can you post details?
thanks in advance!

---

### Post by naschas on 2009-10-18
just search for intel in synaptic and remove the currently installed driver and install the older version that is available i think its version 2.4.1.

---

### Post by greg batmarx on 2009-10-19
Finally i solved the problem upgrading to karmic koala beta.
Not only gnome is back with a vengeance but moreover i enjoy a much more speedier and functional operating system!:P

---

