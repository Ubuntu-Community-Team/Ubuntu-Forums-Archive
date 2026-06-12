---
title: "dual boot? XP Master, Ubuntu Slave"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-13
I did a lot of reading on dual booting, but I'm still lost.  I have XP on my master hd.  I pulled the XP hd and installed Ubuntu(at the time I didn't have an open ide cable).  I have been switching out the drives whenever I wanted to change OS.  I now have an open ide cable and would like to leave xp as master and have Ubuntu on slave, but want to be able to boot from either one w/o going into bios.  Can this be done easily?

---

### Post by Robgould on 2006-02-13
Yes.  Install grub to your mbr....at boot time you get to choose which system you want to boot to.

---

### Post by executex on 2006-02-13
First defrag your harddrive. Becuase i didn't do that and it wouldnt let me partition off more than 2 GB from my WinXP partition. Even though it has 50 GB space left.

Anyway, not only did that cause me an authorization error but made other problems too.

Also, i have a problem where grub won't launch my windows program. It doesn't recognize it. It only sees it as an unknown type 0x7, even though i know its NTFS. It won't launch anything except linux.

So i would be ready for a lot of headaches if i were you :O. I guess just keep googling like me... as i've been doing the whole day and yesterday.

But if you install ubuntu on a fresh drive, it will work. I think the biggest problem is when you are forced to partition or mess with your windows partition.

---

### Post by Coelocanth on 2006-02-13
[QUOTE=executex]First defrag your harddrive. Becuase i didn't do that and it wouldnt let me partition off more than 2 GB from my WinXP partition. Even though it has 50 GB space left.

Anyway, not only did that cause me an authorization error but made other problems too.

Also, i have a problem where grub won't launch my windows program. It doesn't recognize it. It only sees it as an unknown type 0x7, even though i know its NTFS. It won't launch anything except linux.

So i would be ready for a lot of headaches if i were you :O. I guess just keep googling like me... as i've been doing the whole day and yesterday.

But if you install ubuntu on a fresh drive, it will work. I think the biggest problem is when you are forced to partition or mess with your windows partition.[/QUOTE]


That shouldn't be a concern (partitioning), since he's got both OSes on separate drives. Hopefully the install of grub to the mbr on the main drive will go smoothly for him.

---

### Post by lha on 2006-02-14
Easiest way to go is to make Ubuntu master and Windows slave. Then add

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1

in the very end of menu.lst. (It's in /boot/grub.) No need to fool around with bios, mbr, or fstab.

PS. You might need to replace "hd1"'s with "hd2"'s (or even "hd3"'s) in that section you need to add to menu.lst if you have mre than two hard drives. Try first hd1.

---

