---
title: "Installation Problems (RAID config)"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by Brok3n_Sword on 2006-01-24
Hello all, hopefully someone would be kind enough to help me out!  :)  Right now I have 2 74 GB Raptors that are set up in RAID 0, and windows is installed there.  I also have two additional SATA drives.  I'm trying to install ubuntu on a partition of one of the drives, and everything goes fine until I reboot.  GRUB gives me an error (22) and now I can't get to ubuntu or windows.  Is there something special you have to do to get GRUB on the MBR of a RAID config?  Thanks again.

---

### Post by lha on 2006-01-24
[QUOTE=Brok3n_Sword]Hello all, hopefully someone would be kind enough to help me out!  :)  Right now I have 2 74 GB Raptors that are set up in RAID 0, and windows is installed there.  I also have two additional SATA drives.  I'm trying to install ubuntu on a partition of one of the drives, and everything goes fine until I reboot.  GRUB gives me an error (22) and now I can't get to ubuntu or windows.  Is there something special you have to do to get GRUB on the MBR of a RAID config?  Thanks again.[/QUOTE]

Are trying to boot from raid0? Grub cannot do that.

---

### Post by Brok3n_Sword on 2006-01-24
Yes, I was trying to boot from the raid0 (as this is where windows is installed, and I guess the MBR?)  So are there no options for me if I want to boot windows from a raid0 and linux from a seperate drive?

---

### Post by lha on 2006-01-24
[QUOTE=Brok3n_Sword]Yes, I was trying to boot from the raid0 (as this is where windows is installed, and I guess the MBR?)  So are there no options for me if I want to boot windows from a raid0 and linux from a seperate drive?[/QUOTE]

(Every hard drive has a master boot record. AFAIK Ubuntu installs grub to mbr of primary master as default.)

There are options for you, but you need to fix your Windows into bootable state first.

What kind of installation are you planning? Raid for Ubuntu, too? (It can use software raid.) Which drive(s) are you planning to use for Ubuntu?

Can you set bios to boot from the drive where you want to install Ubuntu?

I assume that you could chainload Windows' boot loader from grub even from raid0. (It's hard to believe that mbr would be raided too and even bios can boot your Windows so why grub couldn't.) Even if this isn't possible, you can use ntldr (Windows boot loader) to start Grub.

I know I gave you more questions than answers, hopefully my next post is more informative for you. :)

---

### Post by Brok3n_Sword on 2006-01-24
Thanks for continuing to help!

I'm working on getting Windows up right now.

I plan on installing ubuntu on a partition of the first drive on the SATA channel (A 250 GB WD), and leaving windows alone on the raid drives.

I can set BIOS to boot from the drive which would contain the partition ubuntu is on.

I think the problem with grub is that it doesn't see my raid config, just two seperate 74 gb drives; therefore, I think it must be mapping things wrong.  (I got this idea from here:  [https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29))

I hope I gave you enough information.

---

### Post by nihilocrat on 2006-01-24
[QUOTE=lha]Are trying to boot from raid0? Grub cannot do that.[/QUOTE]

Can it boot from a raid 1? I'm having a similar problem with a server I'm trying to install. It has two 18GB SCSI drives with a hardware RAID 1 and installation goes smoothly until I reboot... GRUB uncompresses the kernel but when it tries to load it says it can't find /dev/ida/c0d0p1. Would the simplest solution just be to switch to LILO?

---

### Post by nihilocrat on 2006-01-24
[QUOTE=lha]Are trying to boot from raid0? Grub cannot do that.[/QUOTE]

Can it boot from a raid 1? I'm having a similar problem with a server I'm trying to install. It has two 18GB SCSI drives with a hardware RAID 1 and installation goes smoothly until I reboot... GRUB uncompresses the kernel but when it tries to load it says it can't find /dev/ida/c0d0p1. Would the simplest solution just be to switch to LILO?

edit : oh, and I found out through dmesg that the RAID controller is a Compaq SMART2, which according to the internet, means I don't have to worry about using SCSI drivers to access the disk. So not having SCSI drivers probably isn't a problem.

edit 2 : well great, I completely reinstall my system and it won't even let me install LILO! It just sort of craps out and says "uhh... nope, it won't work". Perhaps I should just go back to Debian for my server?

---

### Post by lha on 2006-01-25
> **Brok3n_Sword]Thanks for continuing to help!

I'm working on getting Windows up right now.

I plan on installing ubuntu on a partition of the first drive on the SATA channel (A 250 GB WD), and leaving windows alone on the raid drives.

I can set BIOS to boot from the drive which would contain the partition ubuntu is on.[/QUOTE]

Ok, this sounds good. When you get Ubuntu installed and Windows repaired, we'll get on setting dual boot. ATM, your goal is to get both system working and "dual"-boot by selecting boot device from bios.

First I thought you were trying to use grub to load Ubuntu (kernel and initrd.gz, to be precise) from raid0. This isn't possible, as I previously mentioned. I do not know if it is possible to get grub working in the way you tried first, but I wouldn't recommend it even if it was possible.

[QUOTE=Brok3n_Sword]I think the problem with grub is that it doesn't see my raid config, just two seperate 74 gb drives said:**
> https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29[/url])

I hope I gave you enough information.

Are you using some kind of a hardware raid with those Windows disks or Windows' own software raid? Are raided drives sata or ide? As FakeRootHowTo tells, even hardware raid cards aren't really completely hardware always. This is why grub sees your Windows drives as two separate drives - they are separate drives and drivers are used to achieve raid functionality. I think you can't make grub see your raid0 drives as one, but there is no need for that. (Grub doesn't see my software raid1 drives as one but it can still boot from them.)

---

