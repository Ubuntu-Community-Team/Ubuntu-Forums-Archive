---
title: "Windows bootable DVD does not load on a PC with Ubuntu"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by srinivaskaila on 2009-03-20
Hi,

I have seen this topic before but unfortunately it wasn't solved and there in archive. So, I am posting it again.

I have a Windows bootable DVD which I does not boot in my machine alone. I have Ubuntu installed already.

I have seen few people talking about this kind of issue but none could give me a solution.

Changing the boot sequence did not help.

Any ideas, please?

-Sri

---

### Post by dandnsmith on 2009-03-20
I suspect that the problem is in the combination of your hardware, and the way the DVD has been written, nothing to do with any software installed on the PC (as it all happens before any of that is invoked).

You need to know more about the hardware capabilities (a BIOS upgrade might possibly help).

Are you talking about a DVD to install Windows? - I'm not sure why you mention Windows if not

---

### Post by kestrel1 on 2009-03-20
I have come across this issue in the past. I think you may find that it is because the Windows dvd cannot see any usable partitions when you have a Ubuntu install taking the entire drive. You need some free space on the drive preferably at the start of the drive. Use the Ubuntu Live CD to do this with Gparted.

---

### Post by srinivaskaila on 2009-03-20
I was using Windows XP before I came to Ubuntu.

I have total 4 partitions. I had to format the first partition while I installed Ubuntu. However, 3 more partitions are still in NTFS file format.

I seriously doubt if it is hardware / BIOS issue, because I was able to boot with this DVD many time before have installed Ubuntu recently.

---

### Post by kestrel1 on 2009-03-21
I wonder if it is because the first partition is not recognised. Shouldn't really make any odds, but you know the oddities of Windows.:)

---

### Post by srinivaskaila on 2009-03-21
You might be right. And there was somebody talking about Windows installer trying to act smart and bail out when finds an Linux or other OS.

Anyways, I have to have Windows by my profession. I really wish to come out of it but I can't do that now.

Do you think of any solution to get out of this issue?
May writing some entry to GRUB and force the DVD/CD to boot first..?

I am actually very new to Ubuntu. Please help me.

---

### Post by kestrel1 on 2009-03-22
To be honest I think your best bet will be to save your data & wipe the partition that has Ubuntu on it. Install Windows, then re-install Ubuntu on another partition.

---

### Post by spandon on 2009-03-22
.

---

### Post by dandnsmith on 2009-03-22
I don't think it's just the Windows DVD not being able to see the first partition as usable - I've machines with XP installed on the 3rd partition and the 7th partition, with the other partitions a mix of other types (mostly linux or swap).

It all goes back to what is on the DVD - there shouldn't be any problem with booting it, but could well be if then trying to install Windows (for a variety of reasons)

---

