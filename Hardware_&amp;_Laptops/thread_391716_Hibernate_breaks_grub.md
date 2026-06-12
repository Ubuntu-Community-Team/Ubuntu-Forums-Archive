---
title: "Hibernate breaks grub"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by quini on 2007-03-23
Hi,

I've got a big problem here; I installed Edgy on my laptop (LG LW20), and hibernating (or suspending to disk) was "almost" fine with 2.6.17 kernel.

"Almost" means that I rarely found that grub was damaged after hibernating; symptoms are:
1. grub takes a bit longer to appear (3-5 seconds),
2. all the available options take about 10-30 seconds to show "file system inconsistency" (this may be approximated, as I'm no longer hibernating).

The solution was booting with an alternate CD -> rescue -> reinstall grub.

Lately I've found this problem more often, so I decided to give feisty a try, but this problem also happens with feisty  :( 

Any idea?  TIA!!  :) 

PD a bit more info about my system:
-shutting down works, but it doesn't power the laptop off (rebooting works, and so does shutdown when hibernating),
-I'm booting with "noapic nolapic resume=/dev/sda7" options; I changed /the new UUID in etc/fstab in edgy because of that resuming from hibernate problem (1), and now it shows "/dev/sda7 none swap sw 0 0"; I've also modified /etc/initramfs-tools/conf.d/resume and run update-initramfs -u

(1) [http://ubuntuforums.org/showthread.php?t=390630&highlight=uuid]("http://ubuntuforums.org/showthread.php?t=390630&highlight=uuid")

---

### Post by quini on 2007-03-26
I've forgotten to mention that this behaviour happened once using suspend (to ram).

As it has happened one more time today, I've wrote the error message it shows when trying to boot from any option in grub (xp included):

[I]Error 16: Inconsistent filesystem structure
Press any key to continue.[/I]

Do you know if lilo could solve this behaviour?  :confused: 

TIA  :)

---

### Post by quini on 2007-04-05
New information.  It seems it is not a suspend/hibernate problem, because it has happened again today issuing a reboot from the Kde logout options  :( 

I've now removed the "noapic nolapic" options in menu.lst to see if something changes, but I have no idea on what to look for  :( 

Help would be appreciated.  TIA  :popcorn:

---

