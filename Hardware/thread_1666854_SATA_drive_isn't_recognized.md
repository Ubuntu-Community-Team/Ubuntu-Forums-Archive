---
title: "SATA drive isn't recognized"
date: 2011-01-14
forum: Hardware
---

### Post by kasmar on 2011-01-14
HI,
I used to work a bit with ubuntu, but you can consider that I am new in this area. 
 
I istalled ubuntu (latest one) on IDE drive, because ubuntu doesn't see my SATA drive. I see that SATA drive is seen by BIOS and it's also seen by installer of Win7 or WinXP. 
What is the problem?
I have ASUS P7H57D Evo. I had no problems to see the drive when I had WinXP installed. I had no problem to see the drive on my old motherboard.
Mariusy

---

### Post by cascade9 on 2011-01-14
This, again. (sorry, no reflection on you kasmar, just this problem appears to becoming very common). 

ASUS P7H57D Evo, let me guess, you've hooked up the SATA drive to the 'SATAIII ports (tow of them, grey). They are from a marvel controller, and the marvel controllers have some issues with linux. Change the HDD to the blue ports (from the Intel controller)  and you should see the HDD fine with linux.

---

### Post by kasmar on 2011-01-14
Thanks!
I have read this somewere, but it seemed strange for me (due to the fact that this SATA drive was detected by BIOS...).
I will check it and put outcome here.

---

### Post by kasmar on 2011-01-14
Now it works! Great!
But for iinfo:
I had connected ny SATA cable to white socket. Now I changed to blue, which is one of 6 of Intel sockets.Neveerthees, I stil have ome problems with installing win7 and ubuntu as well, but we wwill see....
Thanks a lot!

---

