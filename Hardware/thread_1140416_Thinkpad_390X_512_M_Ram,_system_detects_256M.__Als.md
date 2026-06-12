---
title: "Thinkpad 390X 512 M Ram, system detects 256M.  Also, trouble mounting QUE! cd burner"
date: 2009-04-27
forum: Hardware
---

### Post by storckm on 2009-04-27
I'm new to Linux, running Xubuntu 8.10 on a Thinkpad 390X 2626-MOU.  On the whole, I've been very pleased, but I've had two problems.  First, I bought some RAM on e-bay, 256 M (the max) for each bay, and the lshw-gtk lists each chip as only 128 M.  I tried a puppy linux distro too, and it says the same thing.  I've contacted the seller, as the fault may be unrelated to the operating system.

Another problem: I bought an external USB cd-burner, plugged it in, and can't mount it.  the lshw says that there's a QUE! USB drive attached, and the dmesg commands says that something is there, but doesn't assign it a device name, or whatever you call it, e.g., scd0.  None of the cd-burning programs can read it, so I'm rather at a loss.

Thanks

---

### Post by storckm on 2009-06-03
I did download--and managed to do it without a battery--a BIOS update that was supposed to fix exactly the problem I was trying to solve, with no results.  So I think that the RAM problem was because I needed to have low density RAM (although it's certainly weird that it was read as 128M). 
   It looks like other people have had problems with the same QPS QUE! drive.  I hate to just say that linux doesn't support it and leave it at that, though.
   So if you have any ideas, I'd love some help.
Thanks.

---

