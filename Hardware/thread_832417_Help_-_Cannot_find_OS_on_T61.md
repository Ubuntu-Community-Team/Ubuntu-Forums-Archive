---
title: "Help - Cannot find OS on T61"
date: 2008-06-17
forum: Hardware
---

### Post by wenuswilson on 2008-06-17
I seem to have made a boo boo. I tried to install WinXP on my Thinkpad T61.

To do so I changed my SATA in the BIOS from DHCI (?) to Compatibility (?).

Then I installed Windoze like normal (it didn't find it before).

windoze took over and didn't give me a GRUB.

I changed back from Compatibility (?) to DHCI (?).

It blue screened - so I removed the WinXP partition with the Ubuntu LiveCD Gparted.

Now my HDD doesn't recognize any OS on it.

My liveCD sees the partition with all my system files for Ubuntu but my harddrive doesn't see anything.

I realize this is probably a long shot to get any help but I'm hopin for the best.

wenus.

---

### Post by wenuswilson on 2008-06-18
Super important BUMP.

---

### Post by TubaTodd on 2008-06-19
I may be able to help. We have a bunch of T60 and T61's where I work. First, if you get boot with a live CD and backup all you data....DO IT NOW!!!

Secondly, change your BIOS configs to default, which should include DHCI. Next, wipe your machine and install Windows XP and have it take up the whole drive. After XP is loaded boot from the Ubuntu CD and resize your XP partition accordingly with Gparted. Now create partitions for your Ubuntu install and 1 for swap. Now install from the CD but choose MANUAL when it is at the drive partitioning section. Manually select the Ubuntu partition you created and give it a label of / and check "format" and proceed. Ubuntu does a GREAT job of configuring the boot loader (grub) to allow booting both OS'. Windows is a pig and will only detect itself. :) That's the only way I've ever gotten XP and Linux to behave.

I hope this helps.

---

### Post by EarloftheWest on 2008-06-20
On my T61, I installed XP first and then Ubuntu. I installed XP from the restore partition. Doing so installs the SATA drivers. (I installed XP from an OEMSP2 CD and it installed fine but wouldn't boot XP when all was said and done. The problem was that I didn't have the SATA driver installed in XP. It ran fine under compatibility mode. There is a technote on the Lenovo website on how to install the SATA driver after the fact. It's pretty easy.)

My Ubuntu install did all it was supposed to do with the BIOS set to SATA mode.

Keep working at it and it'll get squared away. My system runs like a champ for the most part.

---

### Post by wenuswilson on 2008-06-22
Thanks to the both of you.

Unfortunately, I was impatient and just backed up important files and reformatted the whole HDD and simply reinstalled Ubuntu.


**The moral, by the looks of it, is that XP has to come first or not at all.**


I looked through Lenovo's site and couldn't find what I needed (SATA-wise) but then again, I only had Ubuntu so anything I found wouldn't be compatible.

**I suppose another question I could ask, to anyone who reads would be the proper way/order to install--**
[INDENT]WinXP Pro (w/ SP2)[/INDENT]
[INDENT]OpenSUSE 10 (install disk only currently)[/INDENT]
[INDENT]Ubuntu Hardy Heron (LiveCD)[/INDENT]

But to posters above this, again, thanks.
nate.

---

