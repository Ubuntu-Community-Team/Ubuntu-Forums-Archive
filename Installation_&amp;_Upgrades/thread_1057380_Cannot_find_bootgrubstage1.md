---
title: "Cannot find /boot/grub/stage1"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by NervousAboutAngels on 2009-02-01
My particular issues began when I tried to boot up linux in my dual-booting (Win XP/Ubuntu Hardy) Acer AspireOne.  I got: EIP: [<e0131d8b>] -local-bh-enable, followed by kernel panic- not syncing: Attempted to kill init! message.  XP still worked then, and my response was to re-install ubuntu, rather than track down the issue, because all my important data is saved in the XP partition anyway.  I started this process with the following partitions:
 /dev/sda1 fat32 4.88 GiB
/dev/sda2  ntfs 90.86 GiB
/dev/sda3  ext3 48.89 GiB
/dev/sda4  extended 4.42 GiB
/dev/sda5 linux-swap 2.22 GiB
After re-installing, (I had tried to make sda3-5 unallocated, then install on top of them) But I instead gained
/dev/sda6 ext3 2.04 GiB
/dev/sda7 linux-swap 164.70 MiB
This might have been all well and good, had I then been able to boot into, well, anything.
Now I had Error 15 coming up with an attempt to boot.
I have since tried find /boot/grub/stage1 but it gets error 15 as well. 
I used root (hd0,5)
setup (hd0)
and met with no /boot/grub/stage1 again.
I attempted instructions involving mounting several directories, but ran out of memory to do it in.
I used lilo to install mbr, which succeeded, but when I tried to boot again, I got the No Partition Active error message and it could go no further.  I feel like at least some of my troubles might very well be solved if I could get /boot/grub/stage1 in place.
Any suggestions are very welcome.  I am left with only the install/live session still working.
Thank you for your help.

---

### Post by dmizer on 2009-02-01
I split this out into it's own thread and moved it to "Installation & Upgrades". You're more likely to get help if you have your own thread, and it's in the correct section.

Thank you.

---

