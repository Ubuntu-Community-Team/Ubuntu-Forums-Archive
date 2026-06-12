---
title: "RAID1 with windows AND Linux"
date: 2008-10-17
forum: General Help
---

### Post by Jeanpaul145 on 2008-10-17
Hi guys and girls, 

First, some background info:
I have recently bought loose parts to make my own custom-built pc, with a  mainboard (A Gigabyte GA-X48T-DQ6) which has an X48 northbridge and an ICH9R Southbridge. It also has another RAID controller, which Gigabyte calls "GIGABYTE SATA 2" (which means I can't find out which RAID controller is actually being used atm).

I've also bought 2 1TB hdd's (2 Samsung Spinpoint F1's to be exact).
Now, I'd like to put these 2 drives in RAID1 mode (100% redundancy).

Now, what I'd like to know is this: is there a RAID1 solution which is both dependably readable **and** dependably  writable from both Linux (My OS of choice is, of course, Ubuntu :popcorn: ) **and** windows XP/windows Vista (I do the game-thing every now and again)? And what is the best solution? Software RAID, the ICH9R RAID mode, or the other RAID chipset on the mainboard?

Any difficulties I should look out for?

Thanks in advance.

---

### Post by Jeanpaul145 on 2008-10-20
Does nobody have any experience with this particular situation?

---

### Post by ilovesocks on 2008-10-27
I'm interested in this, as well. I have an Asus P5E-VM HDMI, which uses the Intel ICH9R southbridge as a RAID controller. I'm not worried about dual-booting, but I've already got Xubuntu installed on a HDD and I want to put that HDD into RAID 1 with a new identical one. According to the mobo manual, you can create a RAID 1 array with an existing and a new drive, but can Ubuntu handle that? The community documentation seems to be a bit outdated.

---

### Post by fjgaude on 2008-10-27
The raid array created with the BIOS can only be used in Ubuntu by using a program called **dmraid**. It's not really the way to go though. Those of us who use software raid use a program called **mdadm**. Google these things and light will show.

---

### Post by ilovesocks on 2008-10-27
Okay, thanks! Found a nice how-to: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by Jeanpaul145 on 2008-10-29
Thanks, it was a great help!:)

Now I've only got to figure out the second part, making it usable in Windows...

---

