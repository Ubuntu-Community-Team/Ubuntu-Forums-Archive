---
title: "Reclaiming Windows"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Citizen Bleys on 2009-03-20
**Phase 1**

I'm dual-booting 8.04 and XPee on my laptop (which is technically a Dell if it matters, but Dell didn't install Ubuntu on it, I did...it's ridiculous that the exact same laptop costs more if they install a free OS on it instead of Doze).  The only Doze thing I ever do on it anymore is play World of Warcraft, which somehow manages to run *better* under wine than it does under real Windows, so it's time to ditch my Doze partition.

Current partition scheme:
/dev/sda1 - XPee - 100 GB
/dev/sda2 - /boot 128 MB
/dev/sda3 - swap - 2048 MB (The same as the amount of RAM in my laptop, which I believe is consistent with recommended practice these days)
/dev/sda4 - / - 50 GB

So yes, 2/3 of my hard drive never gets used.

My plan so far is to delete my Windows partition and create a new /boot partition, another 2048 MB swap partition, and format the remainder of my ex-Windows partition as a new /, and then do a simple cp of everything in my current Ubuntu /boot partition to the new one, then do the same for my current ubuntu / partition, and then of course update the device names in (new) /boot/grub/menu.lst and then reboot and hope to wind up in a perfect copy of my existing Ubuntu install, save on the 100GB part of the disk and not the 50GB part of the disk.

Reasons:  1) I don't want to re-download all of my updates and configure Ubuntu from scratch when I already have a working install.  All I want to do is *copy* said working install
2) My WoW install is over 16 GB, and as a smoker, I do not have piles and piles of cash just laying around to purchase large removable hard drives at the drop of a hat.  I got it working under Linux by copying from my Windows partition, and I doubt I could do a clean install under Linux, even if I didn't mind spending 19 hours doing updates, which I most certainly do.

**Your mission**, if you choose to accept it, is to tell me all of the ways in which I'm an idiot and my plan can only end in tears.  I want to know everything that can possibly go wrong, up to and including my neighborhood being invaded by baby-eating robot Nazis while I'm trying to reformat.  If you're feeling especially generous, you can even offer solutions to the no-doubt extensive list of problems that I will encounter should I attempt to go ahead with my current plan.  I promise not to call the cops.

**Phase 2**

This is the easy part.

At this point, assume Phase 1 or something like it was successful and I now have 2 exact copies of my Linux install, and the Herald Angels are singing my praise in the Kingdom of God.  This, of course, is useless  (The 2 exact copies of the same Linux install, I mean.  The angel bit would be pretty cool if I do say so myself).  I now want to merge them.  Of course, deleting my old /boot, swap, and / partitions is no problem--is there a Linux app I can use to non-destructively grow my new / partition to fill the newly unpartitioned space?

This part I don't really care about, since I can just use the 50GB to play around with Gentoo if I can't have the whole hard drive dedicated to my already-working Ubuntu install.  (I do insist on the majority of my disk being dedicated to Ubuntu, though; since the advent of modular xorg, my greatest success with Gentoo was a system in which I could only use xfce--which I hate--and even then only if I logged in as root 100% of the time, a brilliant plan of action if ever I heard one)

---

### Post by aheckler on 2009-03-21
What you're describing sounds too complex and risky to be worth it for me. If I were in your shoes, I'd just wait until Jaunty comes out next month, do a clean install, and tackle your WoW problem at the same time. If you have an external drive, it would be easy, so you might consider investing in one (they're cheaper than you think!). Plus, you could use it for backups (a good habit to get into) after this whole thing is solved.

Oh, and with 2GB RAM on your system, I'd say you only need 1GB for swap.

---

### Post by Mark Phelps on 2009-03-21
Unless I'm missing something, my guess is that what you want to do is (1) remove your Windows install and (2) expand your Linux install to fill the drive.  Is that right?

In that case, you should be able to do the following:
1) Download and burn a current GParted Live CD (go to Distrowatch to get one)
2) Boot from the GParted Live CD
3) Remove the Windows partition
4) One-by-one, move the remaining partitions to the left on the drive.  Warning -- this can take HOURS to do.
5) When you get to the last partition, expand it to take up the available space on the left.  This can also take HOURS to do.
6) Reboot using an Ubuntu Live CD
7) At this point, your old menu.lst file has obsolete UUIDs and /dev IDs (which you already have guessed), so use blkid to get the new ones.  Update your menu.lst with the current UUIDs and/dev IDs.
8) Reboot into Ubuntu -- should be good to go.

---

### Post by Citizen Bleys on 2009-03-22
Actually, I don't know what a UUID is, but last time I had a GRUB problem (really a udev problem, since the partitions on that computer had different /dev IDs when booted into a LiveCD environment than they did trying to boot the hard disk), all I had to do was change /dev/sdd1 to /dev/sdb1 in 2 places and GRUB was instafixed.

That issue, however, did not involve actually moving and resizing partitions, so perhaps I'd better do some googling on UUIDs--Now that I know what they're called, thanks :)--and make sure I know what needs to be done before I get started.

The hours could be a problem, too, it's for a laptop I have at work and house rules limit laptop use to the hours between 2AM and 6AM.  Nevertheless, the GPartED solution sounds a lot simpler and easier than the nightmare I had planned to unleash upon myself.

---

### Post by Mark Phelps on 2009-03-22
UUIDs are what GRUB uses to identify bootable partitions.  IF you look into a menu.lst file, you'll find an entry like:

```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f7a1777c-44bd-4132-a2a3-e4eeaa2bbeb6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f7a1777c-44bd-4132-a2a3-e4eeaa2bbeb6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
blkid
```

See the uuid in the second line?  To find that, use the "blkid" command, which in my case, yields:

```

bill@bill-ibex:~$ blkid
/dev/sda1: UUID="f7a1777c-44bd-4132-a2a3-e4eeaa2bbeb6" TYPE="ext3" 
/dev/sda2: UUID="a060ef20-2dad-41eb-a33d-220f146b0b45" TYPE="swap" 

```

My Linux root partition is the first one on sda1, so menu.lst uses the UUID of sda1 in its stanza.

To find out what devices are assigned to your partitions, use "fdisk -lu" (that's a lowercase L, not a one).

---

### Post by Citizen Bleys on 2009-04-01
Took me a while to get around to it, but I took your advice; GPartED LiveCD worked beautifully--I actually didn't have to change my menu.lst at all except to comment out the menu entry for XPee.  After reboot, my /boot partition was still, for some reason, /dev/sda2, swap was /dev/sda3, and / was /dev/sda4--/dev/sda1 does not exist and Ubuntu booted seamlessly without any need for a LiveCD or Super GRUB disk.

Thanks a bunch, this issue is now formally resolved.

---

