---
title: "how do I set up a dual or even a tri booting system"
date: 2010-05-18
forum: Hardware
---

### Post by pr0t3g3 on 2010-05-18
I'd like to set up a pc where I can boot up 2 or even 3 different operating systems on my laptop or even on a new laptop as a future project.  Those operating systems may include but might not be limited to:  

1. a linux based os
2. windows xp
2. vista/windows7 (or newer version)

what I'd like to do is set it up so that I can select which system to enter via startup
any ideas or suggestions how I might do that?  Hardware tips?  software setup? what kind of laptop and parts should I purchase and where?

---

### Post by oldfred on 2010-05-18
You need to plan partitons ahead of time. Window wants/needs to have at least one primary partition and then the second install will boot thru the first install in a primary. If you ever delete the first the second may not be bootable unless it is in a primary and then still requires repairs. the windows boot loader only works that way.

But if you want to boot with grub:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Your linux installs and data partitions can all be on logical partitions inside the extended partition. If you are using windows a fair amount you may want a shared NTFS data partition so you easily use data in all installs. I have photos, firefox and thunderbird profiles in the shared so I have all the same data in both windows & linux.

If you keep /home separate you can use as little as 10-20GB for root. If planning several linux installs you may want to move data to /data partition to share that. Some say you can share /home but want you to log in with different user names to avoid setting conflicts which to me defeats most of the advantage of a shared /home.

---

### Post by pr0t3g3 on 2010-05-18
> **oldfred said:**
> You need to plan partitons ahead of time. Window wants/needs to have at least one primary partition and then the second install will boot thru the first install in a primary. If you ever delete the first the second may not be bootable unless it is in a primary and then still requires repairs. the windows boot loader only works that way.

But if you want to boot with grub:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Your linux installs and data partitions can all be on logical partitions inside the extended partition. If you are using windows a fair amount you may want a shared NTFS data partition so you easily use data in all installs. I have photos, firefox and thunderbird profiles in the shared so I have all the same data in both windows & linux.

If you keep /home separate you can use as little as 10-20GB for root. If planning several linux installs you may want to move data to /data partition to share that. Some say you can share /home but want you to log in with different user names to avoid setting conflicts which to me defeats most of the advantage of a shared /home.


I see.  Would it be possible to save an os (not the installation program) to flashdrive or another such removable drive and have the option of booting different operating systems from there as long as my pc can support saving and running files/programs from that os?

---

### Post by oldfred on 2010-05-18
I have a 4Gb flash set up with multiple ISO that are all bootable to use for installs or as repairs. I have another where I used the USB startup creator. I have a new large USB where I plan a full install.

A full install to flash is not really different than to any other drive. Just be sure to install grub2 to the flash drive not the internal drive.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by pr0t3g3 on 2010-05-18
I still have more questions and blank spots; however I'm going to redirect my focus to programming languages for now ^_^ thanks you've been a great help to me

---

