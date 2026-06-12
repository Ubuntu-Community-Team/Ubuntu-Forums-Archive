---
title: "4 Partitions, No Disk Space on Ubuntu"
date: 2008-07-30
forum: General Help
---

### Post by bsriram7 on 2008-07-30
Hi, I've moved to Ubuntu about a few months back. And when I first installed it I was just doing so to try it out. 

Problem is, I'm running out of space on my Ubuntu partition. How do I remove the partitions I don't need and combine them into my existing Ubuntu partition? 

And also, Windows is only taking up about 30/80GB on the main partition and I cannot further shrink the size of the partition in Windows. Is it possible to do it with GParted?  Please help. I want to have more space on Ubuntu, and I still want to keep Vista as well. I have attached a screenshot of my partitions below and I underlined the ones I don't need.

[IMG]http://ramipage.googlepages.com/GParted.png[/IMG]

sda1 - Windows Vista (Can this partition be further shrunk?).
_**sda2**_ - The partition all my stuff is on. (Not required anymore)
_**sda3**_ - I don't know why there is unallocated space. 
**_sda4_** - swap (Can I remove this? I heard if you have 2GB RAM or more, you don't require swap partition. Is that true?)
sda5 - Ubuntu Hardy. (I know 3GB is not exactly running out of space, but I recently installed Ultamatix and I wanna try the games).


If I remove sda2 (the drive I don't need) will the Linux partition change to sda4? If so, will that cause problems if I don't edit /boot/grub/menu.lst or does Ubuntu auto-update it?

Any help would be greatly appreciated. And also, my apologies if this has already been posted.

---

### Post by Ocxic on 2008-07-30
unfortunately there is no way for you to get more space without re-installing. Your partition being at the end of the drive is unable to be enlarged.

---

### Post by Seks on 2008-07-31
Yes, you should use gparted for this, make a gparted live cd or use an ubuntu live cd to do this. Otherwise you can't.


It lets you delete, shrink and more. But don't delete the swap, and defrag first. Swap will keep your machine from crashing if you run out of ram. I have 2gigs, and it still puts some stuff there.

Boot into any windows partition and defrag all the ntfs partitions as much as you can before shrinking (deleting doesn't matter). And shut down windows cleanly to prevent dirtying up the disk again. Even with the defrag and clean shutdown, you might need to resize a piece at a time, or it will throw back an error if you try to shrink it all at once.

---

### Post by Seks on 2008-07-31
> **Ocxic said:**
> unfortunately there is no way for you to get more space without re-installing. Your partition being at the end of the drive is unable to be enlarged.

Not true, mines at the end of the drive and I've reassigned sizes multiple times. You just gotta move it over =P

---

### Post by bsriram7 on 2008-07-31
Isn't my 'Home' directory the reason why my hard disk is running out of space? If so, can't I just delete the ntfs partition that I don't need and move my home directory to that partition? Is that complicated to do?

---

### Post by plucky on 2008-07-31
> **bsriram7 said:**
> Isn't my 'Home' directory the reason why my hard disk is running out of space? If so, can't I just delete the ntfs partition that I don't need and move my home directory to that partition? Is that complicated to do?

See the Psychocats tutorial for [seperate home partition](http://www.psychocats.net/ubuntu/separatehome)

It is a good idea to separate the home partition.

Good Luck

---

### Post by coffeecat on 2008-07-31
I have two ideas for you, and the first doesn't require any resizing, moving or deleting of partitions.

1. Leave your 'stuff' on sda2 and simply set up symlinks from your home folder in Ubuntu to whatever you want to access in sda2. Symlinks are the Linux equivalent of shortcuts in Windows and the icons are like folders with bent arrows on them. So if you go into your home folder and double-click on a symlink folder, you open a folder in sda2, but it's as though you are still in /home. This is what I do to access the same data from Windows and Ubuntu (and other Linux distros on the same multi-booting machine) - all my personal data on a shared NTFS partition, no separate /home partitions for any on the Linux installations and it all works well. Read/write in NTFS is reliable in Linux now and if the Ubuntu installer didn't set up fstab to mount your NTFS partitions at boot up, that's easily remedied.

And if you want help setting up symlinks, just post back.

2. But if you want to change your partition setup, the first thing to say is that you have four primary partitions. This gives you little room for manoeuvre. Explanation: you are limited to four primary (or extended) partitions only. Workaround - instead of a primary partition, you can set up what is called an extended partition. You don't use an extended partition directly - it is merely a 'container' for a number of logical partitions. Primary/extended partitions are numbered sda1 - sda4. Logical, sda5 upwards.

So - if you want to delete sda2 and use the space, do so with Gparted. Then, if you wish, you could shrink your Vista C: partition from within Vista. I've never done this myself, but I believe that Vista (unlike XP) has this ability, and it would be better to do it this way than with Gparted. You'll now have contiguous unallocated space from the end of sda1 to the beginning of sda3, including that unallocated 5.67 MiB. With Gparted, create an **extended** partition using the whole of that space - it will be sda2. Then create one or as many logical partitions within the extended partition as you want. Use it/them as a separate /home in the way a previous poster linked to, or as a symlinked data partition the way I described above - whichever you want. And you don't have to use the whole of the extended partition at once. You could leave some for later use - perhaps another partition for another distro when you decide to triple-boot? :wink: Don't forget that Linux, unlike Windows, can boot from a logical partition. 8)

Don't worry about your partitions being out of order, as it were. It's a bit untidy, but the partition table sorts that out for you.

---

### Post by Vadi on 2008-07-31
Just a note - do not use ultamatix.

Because a) it's nothing special. All games are available from applications - add/remove, or getdeb.net, and b) it can break your computer, badly ([link]("http://www.geekosophical.net/?p=186")).

What the application claims to do is nothing special since all that done is already, and it is very, very sloppily coded.

---

### Post by coffeecat on 2008-07-31
> **Vadi said:**
> Just a note - do not use ultamatix.

Because a) it's nothing special. All games are available from applications - add/remove, or getdeb.net, and b) it can break your computer, badly ([link]("http://www.geekosophical.net/?p=186")).

What the application claims to do is nothing special since all that done is already, and it is very, very sloppily coded.

Sounds like good advice - thank you - but I'm curious. What has this to do with the subject of the thread? Or am I missing something? :-k

---

