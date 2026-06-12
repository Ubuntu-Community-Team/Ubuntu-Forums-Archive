---
title: "Suspend problems with HP NX7000"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by Jott42 on 2006-08-08
Hi all,

I have a HP NX7000 Notebook with Ubuntu 6.06 dapper with the default ati x-server. Nearly everything works fine but the suspend-to-ram does not work correctly: 

- The laptop suspends and resumes correctly the first time after boot. but then the keyboard hangs and the mouse pointer jumps.
- After a second suspend the computer does not wake up any more.

Is there any possiblity to get the suspend mode working? Is there any logfile helping to understand the origin of the problem?

Thanks for any ideas.
Konrad

---

### Post by RafRaf on 2006-08-08
Hi, I have a HP nc6000 and Suspend works most of the time. ;) 
Sometimes it does not resume and I need to restart. Anyway, have you checked out the wiki documentation at: [https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto) ?

---

### Post by kashms on 2006-08-08
I don't know if it is a similar issue but my keyboard on a Medion 5400 would be unresponsive after a suspend to ram. In my case it was the psmouse module that was the culprit. You could try unloading it before suspend and reloading after resume.

---

### Post by Jott42 on 2006-08-09
Thanks for the tips.

I have read Howto [https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto) but this does not help in my case. 

I tried to unload the "psmouse" module but this does not solve the problem. Are there any other modules dealing with the keyboard or is this an x11 problem?

I also tried the additional kernel options for suspend s3_mode and s3_bios but without any success.

Is there nobody who has suspend-to-ram working on a nx7000?

---

