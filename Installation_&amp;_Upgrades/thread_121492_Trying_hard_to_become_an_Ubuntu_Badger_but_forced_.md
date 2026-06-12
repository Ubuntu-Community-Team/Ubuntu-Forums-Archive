---
title: "Trying hard to become an Ubuntu Badger but forced to stay a Farty XP Badger"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by Farty Badger on 2006-01-25
Any help very much appreciated:

I have decided to throw Bill and his cronies out and am trying to install Breeezy on a Dell Inspiron 2500.

The installation starts correctly but then I get the message Invalid Compressed Format (err=1) Kernel Panic: No init found. Try passing init= open to kernel

I have checked the m5sum, I have tried the Live CD everything is fine

If I choose "expert" at the start of the boot process I don't get this problem, but then have no idea what to choose for all the options

Please help!! I'll buy you a beer if I solve this.

:confused:

---

### Post by bulldogzerofive on 2006-01-25
[QUOTE=Farty Badger]

Please help!! I'll buy you a beer if I solve this.

[/QUOTE]

Do I get the beer even if my advice is worthless?


Anyway, at what point in the install do you get this message?

---

### Post by Farty Badger on 2006-01-25
1. I get the first graphic and press enter

2. there are a couple of messages with lines of dots that extend

3. Then a big list of messgaes with numbers in square brackets on the left, messages on the right

The error occurs during this list

For useless advice I'm sure I can find some useless beer

---

### Post by dueY on 2006-01-25
You problem sounds similar to one I had with a Dell system.  Do you by any chance have some sort of software RAID enabled?  Check your BIOS.

---

### Post by Farty Badger on 2006-01-25
No RAID, just a single HD single partition as it came out of the box - about 10Gb free space if that matters. Any  help really [SIZE="7"]Really[/SIZE] appreciated

---

### Post by TransitMan on 2006-01-26
That 10gb you have free, is it a separate partition or is it one the same partition an WinXP?
If the later, you problem lies there. You need to have a separate partition to install Ubuntu on, or wipe the entire drive and lose everything on your XP.
And my guess is you don't have a separate partition, because I got the same message when trying to install another Linux OS.
Also, and if by chance that 10gb is a partition, it must be formatted for use by Ubuntu. Use the partitioning software that comes with Ubuntu to help you. Then the install should go like clock-work.

---

### Post by avantgardaclue on 2006-01-26
[QUOTE=Farty Badger]No RAID, just a single HD single partition as it came out of the box - about 10Gb free space if that matters. Any  help really [SIZE="7"]Really[/SIZE] appreciated[/QUOTE]

Had the same probs as you with my Dell, oh what the hell. Eventually saw the light, bought a second disk (maxtor) off ebay for dirt cheap money, 5 minutes to install, then even my granny could install ubuntu.=;

---

### Post by Farty Badger on 2006-01-30
Thanks for the tips on partitions - I'll bite the bullet and wipe the drive this week.....

---

