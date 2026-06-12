---
title: "&quot;no drive to partition&quot; during install"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by porter on 2005-07-05
during the install i get an error stating that i do not have any hd to partition. 

??? now what ??? 

i have the latest 5.04 32bit ubuntu and the mb bios recognizes both hd's with the correct sizes. i do not have or plan on having any version of windows on this machine and of the other 3 or 4 distros that i have tried on my older machine, i liked ubuntu by far and i would like to find a way to resolve this. any help would be greatly appreciated. thanks.

pc specs:
2 sata maxtor 80 gb hd's 
shuttle st20g5 mb 
amd64 3700+ cpu
pc3200 1 gb ram
sony dvd drive, ide

---

### Post by sunscape on 2005-07-05
Sounds like your motherboard's sata is not supported. You need to check around to see if anyone has solved the problem.

---

### Post by porter on 2005-07-21
yep, looked around. there seems to some others with different mb's that have the same problem, but no one has posted a solution yet....

---

### Post by marcus23 on 2005-10-13
I have escentially the same computer, other than it is 2 200GB seagate SATA drives;

Try enabling raid in your bios (even if you don't intend to use raid) - for some reason the ULi SATA driver only seems to detect drives that are connected to it if RAID is enabled in the bios. 

Even if you were in a case where you only have 1 SATA drive connected to it you should enable RAID in order to get it to detect the HD.

---

### Post by porter on 2005-10-24
success! 
thanks for the reply & pm.
i just got 5.10 dl'd and was having issues after installing about sda1 not being found... this fixed that issue also.

thanks again.

---

### Post by subhankar on 2005-10-30
Hello!

I'm having the same problem with Hoary. So, just using Breezy solved the problem entirely or did you have to do any tricks? Is it that Breezy installs fine on the sata but can't find sda1 and enabling raid in BIOS fixed that problem? Please confirm! It'll be really helpful.

Thanks in advance,
Subhankar

---

### Post by porter on 2005-11-20
yes, enabled the raid in the bios, breezy found the hd without any problems.

(sorry it took so long to reply, i didn't realize that this was still being replyed to)

---

