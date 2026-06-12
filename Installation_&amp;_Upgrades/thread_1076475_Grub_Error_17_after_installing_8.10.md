---
title: "Grub Error 17 after installing 8.10"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by flim on 2009-02-21
Hi there,

I've had my machine upgraded - now has 4x1TB drives on raid 0 and no hd connected to internal controller.
Ubuntu boots fine from cd, and install works without problem. However, on boot, Grub stops with Error 17.

It's a new install, there's no other OS present (and won't). Ubuntu has been installed to sda, with sda1=swap, sda2=ext3 /. Grub is written to sda and configured to boot from sda2 (although that is via UUID) - doesn't look as if grub could find that info though, seems to stop before reading it (menu doesn't come up).

I've of course done some research before posting, but couldn't find anything useful yet. There's nothing in bios or raid setup (hardware raid, controller is DC-3410) I could change (bios only allows to change internal controller anyway, and only the CD drive is connected to that one).

Disks are working fine once Ubuntu has been booted from CD.

Any ideas anyone? I've got no clue where to look for more infos right now :|

---

### Post by dstew on 2009-02-21
Error 17 means that grub stage 1.5 on the MBR of the boot disk cannot recognize the parititon type. This makes me suspect that you are trying to load grub stage2 (which shows the menu etc.) from a partition that is part of the RAID. Grub stage1.5 is a very simple program (just a few kilobytes) and it cannot mount striped RAID, such as RAID 0.

You can fool grub into loading stage 2 if you put it on a mirrored RAID partition, like RAID 1. Or, you can create a partition that is not part of any RAID, that has the grub stage 2 and the linux kernel. The kernel is a big program, and it can mount the RAID.

I am talking about soft RAID here. There is a way to boot grub from a FakeRaid, but it is a little tricky. See the [FakeRaid HowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). I read there that now you can install 8.10 to a FakeRaid using the Alternate Install CD (but not the Live CD).

---

