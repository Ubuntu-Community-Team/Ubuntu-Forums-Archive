---
title: "[SOLVED] install xp without full format, keeping kubuntu"
date: 2008-11-15
forum: General Help
---

### Post by LordIshamael on 2008-11-15
hey i currently have kubuntu 8.10 on my laptop
i want to play some xp games like tes 3 but vbox doesnt have support for direct3d, and from what i found isnt likely to anytime soon
i was wondering if it was possible to set up a dual boot of windows and kubuntu without having to uninstall and then reinstall kubuntu & all my apps as otherwise its just not worth the trouble

i found this site which details how to do it but as the operation seems a bit risky i just wanted a second opinion on whether its a good idea to do it or not

Edit:
sorry forgot to post the site
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by taurus on 2008-11-16
Basically, you want to boot your machine from the LiveCD.  Then, use gparted from the CD to resize your harddrive, making space at the front of the harddrive for windows.  You can format that space to ntfs with gparted.  Then, reboot and switch the Ubuntu LiveCD with your windows and install XP on that new ntfs partition.  After installing XP, you now need to reinstall GRUB to MBR so you can boot Ubuntu and XP.

Or at least that's what I would do.  And of course, _back up_ your important files on your Ubuntu first before you start resizing anything just in case.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by empthollow on 2008-11-16
That looks like a great tutorial.  Whenever you start to mess with changing partitions there is some risk of losing data.  However, it looks like all you need to do is shrink the ubuntu partition and this is a very low risk operation.  You should be able to install windows without too much trouble as long as you read carefully and understand what you are doing in each step.

---

### Post by LordIshamael on 2008-11-16
yeah thats basically what the walkthrough says
thanks a lot!now i know its safe
much appreciated!

---

### Post by taurus on 2008-11-16
When you resize your harddrive, the UUID for your / would probably change so you need to change it in /etc/fstab and /boot/grub/menu.lst or Ubuntu would crap out when you try to boot from it.

---

### Post by LordIshamael on 2008-11-16
ill keep that in mind...thanks

---

### Post by LordIshamael on 2008-11-16
> **taurus said:**
> When you resize your harddrive, the UUID for your / would probably change so you need to change it in /etc/fstab and /boot/grub/menu.lst or Ubuntu would crap out when you try to boot from it.

i have to go into them and replace the old with the new right? so how do i know the new UUID?

---

### Post by taurus on 2008-11-16
After you resize your harddrive, you can look it up with

```
sudo blkid
```

---

### Post by TeXtonyx on 2008-11-16
After you resize your *buntu partition, I don't think it is a good
idea to partition that space, leave it unallocated. The live cd
installer for instance has an option 'install to largest free space
(guided)' which will choose the unallocated space not the unused
space within an already assigned partition. I think that the Windows
installer also lets you choose unallocated space, just keep in mind
how large in GB the unallocated space is which is usually the same
as how much you previously resized your partition down to; the
difference is size before and after shrinking. Your valuable partition
is formatted, so when you have to pick which partition to install to
and they are all previously formatted, there is a chance to make a
mistake. But, if install to an unallocated space, then you never
risk overwriting some partition containing data of value. You can be 
pretty sure of which formatted partition to install to, but why take 
any chance at all when it isn't needed. Installs know how to format.

---

### Post by LordIshamael on 2008-11-16
i ran into a problem in the first step itself
the /home partition(my biggest at 130gb) is not getting resized

i booted into my pclos livecd(as thats the most recent one i have)
and tried to resize the partition, but the first time i do it after booting up, the control center hangs
i restart the control center, but then it says e2resize not possible
and i cannot access the partition after that, through konqueror or konsole
i checked and there is definitely enough space to resize(oddly, thoguh, kubuntu tells me that 70 of 130 gb is free, but it counts 94 gb of space on the same partition(/home), which i can track down, so the second number is correct)
but theres definitely 25gb of space available either way, which is how muhc i want to give xp
i even tried resizing to free up 10gb, but it didnt work
i have an old kubuntu gutsy cd too, but the display doesnt work properly on that, and a fedora 8 livecd which doesnt have an option to resize disks
so pclos is my only hope unless i can borrow a cd, which will take time
any ideas why this is happening and how to work around it?

i can easily and freely boot into kubuntu btw, so the attempted resizes havent affected anything at all

---

### Post by empthollow on 2008-11-19
whenever i resize, i use ubuntu live and gparted - just so you know where i'm comming from.  the partitions will not resize if the the hard drive is mounted.  on some versions of ubuntu live, starting gparted causes the hard drive to mount and i have to unmount and apply changes.

---

### Post by LordIshamael on 2008-11-20
in pclos, the control center partition manager has an option to unmount, and the option to resize partitions doesnt become available until its unmounted
thanks anyway
im downloading gparted live now, lets see how that works

---

### Post by LordIshamael on 2008-11-22
someone is out to get me.

gparted worked beautifully (it could do with a lot more work on the interface imo - though its just in an early version so i guess theyve got bigger priorities)
it didnt even have the option as far as i saw to format to fat32 or ntfs, but i wanted to leave it unallocated anyway
but then i boot up with the xp install, and it says it cannot detect any hard drives!
obv i cant do anything and have to restart
any ideas?help please?

btw the UUID didnt change for any of my partitions, thanks for the tip anyway

---

### Post by LordIshamael on 2008-11-23
im going to retry w/ vista in a couple of days, or shd i try with a friend's xp?

---

### Post by LordIshamael on 2008-11-27
vista worked perfectly!
recognised everything straight off, installed, and is working fine (after a couple of driver upgrades)

thanks to everyone who helped out here!


i still dont know what the problem was with xp, though, but anyway, i dont need it anymore

---

### Post by t0n on 2008-12-05
i still got the same problem with XP when it says it cannot found any HDD.
want to install XP, not Vista :)
any ideas what to do?

---

