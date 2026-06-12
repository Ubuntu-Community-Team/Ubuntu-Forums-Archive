---
title: "Installing WinXP after Ubuntu"
date: 2008-10-19
forum: General Help
---

### Post by wenuswilson on 2008-10-19
Greetings. I own a Thinkpad T61 with a SATA drive, I've gone to the BIOS and changed to Compatibility mode. I'm trying to install a copy of Windows XP Professional and am having some difficulties. 
The setup sees my hard drive. I have a total of four partitions on a 100 Gig HDD. 1st - "New (Raw)", where I want the Windows to go. 2nd - Ubuntu 8.10, 3rd - swap, 4th - ext3, media and general backup files.

When I select the first partition I get this message and cannot proceed any further:
> To install Windows XP on the partition you selected, Setup must write some startup files to the following disk:

	95394 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP-compatible partition.

To continue installing Windows XP, return to the partition selection screen and create a Windows XP-compatible partition on the disk above. If there is no free space on the disk, delete an existing partition, and then create a new one.

To reutrn to the partition selection screen, press ENTER.

---

### Post by darrelljon on 2008-10-19
I think your first partition needs to be NTFS (or FAT32). Beware, Windows XP is greedy and the installation might eat your other partitions.

---

### Post by wenuswilson on 2008-10-19
That's what I'm worried about. Every time I try to install, I have to reset my grub because it likes to eat that too. I have tried using an NTFS partition by setting it up in gparted. I have not tried a fat32/16 yet. I have errands to run now, but I will keep you and other viewers informed once I try that out.

---

### Post by wenuswilson on 2008-10-19
Just tried the Fat32. No change in the message.

---

### Post by alzie on 2008-10-19
There is a tutorial for adding XP to a computer with an existing linux OS in place:  [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I hope this is what you are looking for.

---

### Post by wenuswilson on 2008-10-19
Ok-- so I figured out my problem, my entire 100Gb HDD was under sda1 when I should have reduced that itself to allow for a sda2. So that was a nice revelation to have. Now it's a new problem all together... WinXP copies files nicely and restart, upon restart I get "Invalid Partition Table". I tried fdisk but that was an invalid command. Suggestions? I'm very close to just saying f%$@ it and formatting the whole system and starting from scratch. BUT I DON"T WANT IT TO COME TO THAT.

---

### Post by CloudFX on 2008-10-19
> **wenuswilson said:**
> That's what I'm worried about. Every time I try to install, I have to reset my grub because it likes to eat that too. I have tried using an NTFS partition by setting it up in gparted. I have not tried a fat32/16 yet. I have errands to run now, but I will keep you and other viewers informed once I try that out.

About this, it is something that will always occur.  Windows will replace GRUB with its own boot application, MBR, which will only boot into Windows.

For reference, this Wiki page will help you out with getting GRUB back.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by wenuswilson on 2008-10-21
At this point I don't care it WinXP eats my grub, I've gefuckt my Ubuntu OS up so bad that I need to clean it out anyway.
WinXP Pro SP2 makes it to the initial restart to begin doing its think and then decides to tell me "Invalid Partition Table". I'm guessing just to reformat the entire system and start back at square one.

---

