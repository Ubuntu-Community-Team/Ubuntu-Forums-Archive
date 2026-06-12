---
title: "New atom platform compatibility"
date: 2009-12-31
forum: Hardware
---

### Post by Wizang on 2009-12-31
So intel is releasing their new atom platform in the next few days and I was planning on purchasing a mini-itx board for a little home server. I was advised by someone that linux support out of the box might not exist since its a brand new chipset. What do you guys think? The new chipset is the Intel NM10 Express. The first two boards with be the D410PT and the D510MO.

---

### Post by oappi on 2010-01-20
at least now my D510MO won't boot on any of the 5 linux distros i have tested with it... or atleast i dont get picture =( but hey i can make my dvd drive give dvd out =). Thats something.

---

### Post by hambleturtle on 2010-03-21
My D510MO worked out of the box with puppy linux 4.3.1, but not with standard ubuntu 9.10. Even booting from the cd with the options "live text" my machine hung on the line 
"Booting Processor 1 APIC 0x1 ip0x6000".

The solution was to upgrade my bios from version 0115 (MOPNV10J.86A.0115.2009.1006.2145) to the latest available version 0175 (MOPNV10J.86A.0175.2010.0308.0620) - I downloaded the iso installer from intel and put it on a usb key with LiveUSB Creator. After an intial whinge about a cmos checksum error the machine now seems to run fine - at least I got into X perfectly happily.

---

