---
title: "Ubuntu not booting on Multi-boot with Vista and Windows 7"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by nakshathram on 2009-02-02
Hi,
  I have multi-boot with Vista, 7 and ubuntu 8.10 (all 64-bit) in my machine, but can't get ubuntu to boot.

Here's how my hard drive is partitioned.

1. Vista - Primary
2. Windows 7 - Primary
3. Extended partition
[INDENT]Linux swap[/INDENT]
[INDENT]Ext3 - Ubuntu[/INDENT]
[INDENT]NTFS drive for sharing data between windows and ubuntu[/INDENT]
4. Recovery drive - Primary (I don't want to remove this for obvious reasons).

My laptop came with Vista pre-installed.
Here's what I did after that.
[LIST=1]
[*]Installed Windows 7 - This installed the bootloader from Windows 7 to MBR which listed both Windows 7 and Vista.
[*]Installed Ubuntu - I want to use windows boot loader, so installed grub on the partition where I installed ubuntu, not on MBR
[*]Booted to Windows 7 and installed EasyBCD. Added an entry for Ubuntu by choosing grub as the boot loader. EasyBCD showed the path it would look for grub as /NST/nst_grub.mbr under root drive (ie, the Vista partition).
[*]Restarted the machine with Ubuntu live CD, copied the menu.lst file from Ubuntu installed partition to Vista partition under the directory C:\NST.
[*]Restarted to Vista and rename menu.lst to nst_grub.mbr.
[*]Restarted and chose Ubuntu from boot loader. Screen just shows a blinking cursor on the top left of the screen and nothing happens.
[/LIST]

I am able to boot to both Vista and 7 without any issues. I do not want to install grub to MBR, just don't want to mess up my MBR since I am a newbie to Ubuntu. (Using recovery on HP laptops I heard is a pain.)

Can someone help me out with this so that I can boot to Ubuntu too?

Thanks,
Naks

---

### Post by nakshathram on 2009-02-03
This is resolved.

Couple of mistakes I was making.
[LIST=1]
[*]I was using Windows 7 boot loader. I changed it to Vista's.
[*]I renamed menu.lst to nst_grub.mbr. Stupid thing to do!
[/LIST]

This is what needs to be done to get all three working.

Pre-condition.
- Already has Vista installed.

To do.
- Partition the hard drive to as many as you want. Have one for Windows 7, one for linux swap, one ext3. linux swap and ext3 could be logical partitions under extended. No issues.

- Install Windows 7. This will over-write your MBR. Don't worry, we will go back to Vista's to avoid issues when Windows 7 beta expires.

- Install Ubuntu. Choose manual partition method while installation and on the review screen, click advanced. Install boot loader to the partition where Ubuntu is installed, not to MBR (if you want to keep windows boot loader).

- Re-boot. You will see only Windows Vista and 7 listed.

- Boot to Vista. Download and install EasyBCD.

- Add an entry for Linux (give name as Ubuntu or anything you would like to identify Ubuntu as) using EasyBCD and choose the partition where you have Ubuntu installed (Linux native).

- Write the MBR (under manage MBR tab).

- All set. Re-boot. You will see windows boot loader, with Ubuntu listed.

- Choose Ubuntu. You will see grub loader. Choose the Ubuntu version to boot to. And there you are.

- You will be able to boot to windows also without issues.

No need to use any boot DVDs or live CDs.

Hope this helps the ones who have been wrestling with multiboot Vista, Windows 7 and Ubuntu Intrepid.

'Njoy.

---

