---
title: "GRUB missing, Windows gives BSODs...and RAID?"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by George_ on 2009-10-04
Hi guys, it's been a while since I was here last...

I used to have Ubuntu 8.04 32-bit installed on my old computer (Athlon64 3200+, 1GB DDR-400 RAM) as a dual-boot with Windows XP 32-bit. I seem to remember that Ubuntu had a boot menu (GRUB, was it called?) allowing you to choose between Ubuntu and XP at startup. Oh, and it may be relevant; both operating systems were on separate physical hard drives.

When I got my new computer in March (Core i7 920, 6GB DDR3-1333) I initially used only XP 32-bit for several months. However, I decided on a whim to reinstall Ubuntu again (mainly because the F@H SMP client runs so much better on Linux than Windows). This time I ran into a few problems. I edited my existing partitions to give Ubuntu a 20GB partition, plus 1GB for a swap partition (that's what I used for my old computer, though I've seen people say that it should be at least the size of physical memory...is it too small?). Then I downloaded the Ubuntu 9.04 64-bit iso, burnt it to a CD, put the CD into the disk drive, rebooted, changed the boot sequence in BIOS to boot from CD as well, and waited. I selected the option to install Ubuntu onto my computer, and I went through the steps. I chose ext3 for the file system of the root, and used the 1GB partition for swap. Everything's all good. It installs, and then it says I have to reinstall before installation completes. Fine. I click Restart Now, take the CD out when it tells me to, and press enter. The computer reboots. Here's where I start seeing problems.

First off, GRUB isn't there anymore. Should it be? Without it, I have no idea of how to get back into the Ubuntu installation I put on the hard drive.

Secondly, Windows XP flickered a BSOD before restarting at the Windows loading screen. This occurs about 2 seconds in.

My Dad managed to get rid of the BSOD issue by resetting the CMOS, so I'm not quite sure what caused the problem. The CPU was OC'ed to 3.6GHz before, so I don't know if that could have been the problem. But I don't think it would.

Also, I have a RAID on Windows. I'm not entirely sure if it's a hardware or software RAID, but the BIOS recognizes the RAID and during POST I get a screen telling me the status of the two drives I have (Western Digital 640GB 7200s), that they're in good working order, and that it's a RAID 1. So, if it's a hardware RAID, wouldn't Ubuntu recognize it? And if it were a software RAID, what do I have to do to get Ubuntu to recognize it?

I know this is quite a lot of stuff, but any help at all would be good.

Thanks for your time.

George_

---

### Post by oboedad55 on 2009-10-04
> **George_ said:**
> Hi guys, it's been a while since I was here last...

I used to have Ubuntu 8.04 32-bit installed on my old computer (Athlon64 3200+, 1GB DDR-400 RAM) as a dual-boot with Windows XP 32-bit. I seem to remember that Ubuntu had a boot menu (GRUB, was it called?) allowing you to choose between Ubuntu and XP at startup. Oh, and it may be relevant; both operating systems were on separate physical hard drives.

When I got my new computer in March (Core i7 920, 6GB DDR3-1333) I initially used only XP 32-bit for several months. However, I decided on a whim to reinstall Ubuntu again (mainly because the F@H SMP client runs so much better on Linux than Windows). This time I ran into a few problems. I edited my existing partitions to give Ubuntu a 20GB partition, plus 1GB for a swap partition (that's what I used for my old computer, though I've seen people say that it should be at least the size of physical memory...is it too small?). Then I downloaded the Ubuntu 9.04 64-bit iso, burnt it to a CD, put the CD into the disk drive, rebooted, changed the boot sequence in BIOS to boot from CD as well, and waited. I selected the option to install Ubuntu onto my computer, and I went through the steps. I chose ext3 for the file system of the root, and used the 1GB partition for swap. Everything's all good. It installs, and then it says I have to reinstall before installation completes. Fine. I click Restart Now, take the CD out when it tells me to, and press enter. The computer reboots. Here's where I start seeing problems.

First off, GRUB isn't there anymore. Should it be? Without it, I have no idea of how to get back into the Ubuntu installation I put on the hard drive.

Secondly, Windows XP flickered a BSOD before restarting at the Windows loading screen. This occurs about 2 seconds in.

My Dad managed to get rid of the BSOD issue by resetting the CMOS, so I'm not quite sure what caused the problem. The CPU was OC'ed to 3.6GHz before, so I don't know if that could have been the problem. But I don't think it would.

Also, I have a RAID on Windows. I'm not entirely sure if it's a hardware or software RAID, but the BIOS recognizes the RAID and during POST I get a screen telling me the status of the two drives I have (Western Digital 640GB 7200s), that they're in good working order, and that it's a RAID 1. So, if it's a hardware RAID, wouldn't Ubuntu recognize it? And if it were a software RAID, what do I have to do to get Ubuntu to recognize it?

I know this is quite a lot of stuff, but any help at all would be good.

Thanks for your time.

George_

Grug should be there. How did you install, specifically how did you handle the partitioning aspect? Did you let the install pick the empty space, did you manually partition? You know, that sort of thing.

---

### Post by George_ on 2009-10-04
I clicked manually manage, then clicked on the partition, selected ext3 for the root filesystem, selected / for the mount point, and selected swap for the swap partition. That's all, I think. I'd already changed the partitions in Windows, so that I had the 21GB of unformatted space on my hard drive for the install.

---

### Post by oboedad55 on 2009-10-04
> **George_ said:**
> I clicked manually manage, then clicked on the partition, selected ext3 for the root filesystem, selected / for the mount point, and selected swap for the swap partition. That's all, I think. I'd already changed the partitions in Windows, so that I had the 21GB of unformatted space on my hard drive for the install.

Hmmm... And the install completed normally. Do a search for installing grub in these forums. It's been addressed a million times. You'll boot from the LiveCD and reinstall grub that way. I wish I had more help for you, but you can't hurt anything by installing grub again. You didn't by any chance decide no to install a boot loader?

---

### Post by dcclabough on 2009-10-04
theres also the super grub boot disk... or as i refer to it when i want to keep my mystical super nerd image in tact around technophobes- "the magical boot disk"
[http://www.supergrubdisk.org]("http://www.supergrubdisk.org")

---

### Post by George_ on 2009-10-04
Here's what I did:

Boot off live CD
Terminal
sudo grub
find /boot/grub/stage1
[it gives me (hd0,4)]
root (hd0,4)
setup (hd0)
quit
Reboot

And grub fails to show up.

> Hmmm... And the install completed normally. Do a search for installing grub in these forums. It's been addressed a million times. You'll boot from the LiveCD and reinstall grub that way. I wish I had more help for you, but you can't hurt anything by installing grub again. You didn't by any chance decide no to install a boot loader?
Was I supposed to install a /boot/ mount on a separate partition? Because I remember reading somewhere that GRUB not being there was because there was something wrong with /boot/, or that there wasn't one in the first place.

> theres also the super grub boot disk... or as i refer to it when i want to keep my mystical super nerd image in tact around technophobes- "the magical boot disk"
[http://www.supergrubdisk.org](http://www.supergrubdisk.org)
Erm...what does this do, exactly?

---

### Post by oboedad55 on 2009-10-04
> **George_ said:**
> Here's what I did:

Boot off live CD
Terminal
sudo grub
find /boot/grub/stage1
[it gives me (hd0,4)]
root (hd0,4)
setup (hd0)
quit
Reboot

And grub fails to show up.


Was I supposed to install a /boot/ mount on a separate partition? Because I remember reading somewhere that GRUB not being there was because there was something wrong with /boot/, or that there wasn't one in the first place.

Did you not install grub on the mbr of the first drive? That's what it's starting to look like.

---

### Post by dcclabough on 2009-10-04
> Erm...what does this do, exactly?

check it out... you just boot the cd, and follow the on screen instructions to solve your grub/mbr issues... its kind of a booting cure-all

---

### Post by oboedad55 on 2009-10-04
> **dcclabough said:**
> check it out... you just boot the cd, and follow the on screen instructions to solve your grub/mbr issues... its kind of a booting cure-all

I second the motion. Just go to the web site and download the program then make a bootable CD from it. Take a look at the site, it's self-explanatory.

---

