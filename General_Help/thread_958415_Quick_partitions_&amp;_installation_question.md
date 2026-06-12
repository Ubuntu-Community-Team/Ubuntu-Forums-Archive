---
title: "Quick partitions &amp; installation question"
date: 2008-10-25
forum: General Help
---

### Post by Emarian on 2008-10-25
I was thinking about trying to setup a quadboot. I've heard that Ubuntu works fine with being installed on a logical partition, so it's possible, right?

Here's what I want to do:

(hd0,0) - Mac OSX - Primary Partition
(hd0,1) - Vista - Primary Partition
(hd0,2) - XP - Primary Partition
(hd0,3) - Ubuntu - Logical Partition
(hd0,4) - Ubuntu's Swap - Logical Partition

I'd install them like this:

1. Wipe HD completely clean
2. Install Mac
3. Create partition and install Vista
***That way neither OS picks up the other with their bootloader
4. Create partition and install XP
***XP won't detect Vista/Mac
5. Create both partitions and install Ubuntu and it's swap space.
6. Chainload all other 3 OSes with GRUB


Will it work? Thanks for your help.

---

### Post by cantormath on 2008-10-25
I remember there being an issue with windows requiring that it be  on the first partition.  This is correctable with some grub magic but I dont know about doing it with two copies of windows.  

My guess is it will work.

---

### Post by Emarian on 2008-10-25
Thank you. I appreciate it.

---

