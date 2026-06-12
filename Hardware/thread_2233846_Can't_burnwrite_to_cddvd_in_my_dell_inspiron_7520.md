---
title: "Can't burn/write to cd/dvd in my dell inspiron 7520"
date: 2014-07-11
forum: Hardware
---

### Post by se3 on 2014-07-11
System: Dell Inspiron 15r se(turbo) 7520 in dual boot configuration with Windows 8.1 and Ubuntu 14.04.
Optical Drive: tsstcorp dvd+-rw sn-208bb

I cannot burn/write to cd/dvd , neither to blank nor to partially filled cd/dvd. i have tried cd/dvd by various brands and used k3b, brasero . I can read both cds and dvds just fine. i am attaching dropbox link to their log files for a cd.
k3b shows unable to fixate disc.

[https://db.tt/JfTnoIlb](https://db.tt/JfTnoIlb)
[https://db.tt/HoL0Rt3u](https://db.tt/HoL0Rt3u)
[https://db.tt/K37Sy4JQ](https://db.tt/K37Sy4JQ)


Guys please help me solve this problem, tell me what can i do, is their some patch? or where am i going wrong?

Note: I used to have similar problem in windows 8.1 as well , but after the last update it has sorted out and i can write partially filled cds as well, which makes me think it may be due to device's incompatible drivers (or kernel modules, whatever you guys call them)

---

### Post by scdbackup on 2014-07-11
Regrettably the preview shows my fixed font formatted text as a single dumpling. I post it nevertheless: ---------------------------------------------------------------- The decisive problem which prevents burning is reported by these SCSI error messages:        CDB:  2A 00 00 00 32 27 00 00 1F 00       status: 0x2 (CHECK CONDITION)       Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 64 00 00 00       Sense Key: 0x5 Illegal Request, Segment 0       Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0  The attempt failed to write 31 blocks to block address 0x3227 = 12839 decimal. The error message would match an attempt to write to a closed medium.  Regrettably wodim does not clearly tell the medium state here. But this message indicates that there is already a data track on the medium:      Starting new track at sector: 12839  All three logs seem to stem from attempts to write the same CD-R medium. What do you get with a new CD-R, or an erased CD-RW ?  ----------------------------------------------------------------  In general it is possible with many media types to add more data, if the previous write run kept the medium appendable. So the failure now probably is caused by the way how the previous burn run on the medium was set up.  The burn program is supposed to offer you some option to toggle between closing and keeping appendable. According to [http://askubuntu.com/questions/28044/why-is-it-not-possible-to-burn-a-multisession-dvd-using-brasero](http://askubuntu.com/questions/28044/why-is-it-not-possible-to-burn-a-multisession-dvd-using-brasero) it would be for Brasero: "Leave disc open to add other files later" in the "Properties" sub menu of the "Image Burning Setup".  ----------------------------------------------------------------  Have a nice day :)  Thomas

---

### Post by scdbackup on 2014-07-11
Trying to attach my reply to a new post.

---

### Post by se3 on 2014-07-12
Thank you for replying, i tried to burn an iso image to a blank cd  and it burned just fine, maybe i am just not able to append to partially filled cds,i  will add more after a few tests, but i am not able to burn to dvd, i suspect there is problem with my optical drive's dvd laser, see following for dvd [https://db.tt/sqwlKHA1](https://db.tt/sqwlKHA1) [https://db.tt/FOrZFWrC](https://db.tt/FOrZFWrC) [https://db.tt/F82dZtH7](https://db.tt/F82dZtH7) .

---

### Post by scdbackup on 2014-07-12
Well, the successful run with k3b used program growisofs with options  -use-the-force-luke=dao -dvd-compat which are supposed to close the DVD. So this medium will not work for a further session. --- As said, you will have to tell the burn program not to close the medium.

---

