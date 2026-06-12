---
title: "(K)Ubuntu installer doesnt recognize ANY partitions or space (hardware RAID 0)"
date: 2010-02-16
forum: Hardware
---

### Post by MCVenom on 2010-02-16
Not really solved, but no longer an issue, after discovering that it was a Fake RAID, my dad just disabled it. For those who would like to install on a Fake RAID, there's plenty of information here: [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

(**Extraneous info**) So my father was experiencing A LOT of problems after upgrading from Vista to Win 7 and had been attempting to fix them to the best of his ability (he's no computer lightweight, he knew Assembly Language at one point in his life ;) ). So naturally my inner Linux fanboy suggests he try Kubuntu 9.10, which he takes interest in and decides to dual boot with Win 7. (**/Extraneous info**)

Long story short, when we reached the partitioning step of the installer, none of his partitions were there. None. Zip. The partition table was blank. (GParted recognized them, though.) I tested this step with a Kubuntu 9.10 x64 LiveCD, Kubuntu x64 Alternate CD, Kubuntu 9.10 x32 LiveCD, and a Linux Mint 8 (GNOME, Ubuntu 9.10 based) LiveCD; all of these failed to recognize his partitions in the installer. It did however, recognize a USB key he inserted. ](*,)

His hard drives are all SATA hard drives with a software (fake) RAID 0 configuration, and we started with about 600 GB unallocated space and later formatted this down to about 50 GB unallocated space. His BIOS does not have an option for a Legacy or Compatible SATA mode. I know one of the drives is a Seagate Baracuda hard drive, if that helps.

Thanks in advance for any help and I'll provide any more information if needed, I'm just posting what little I know about his setup now. I'd love to be able to impress him the awesomeness that is Ubuntu if we can get past this issue! :grin:

---

### Post by quixote on 2010-02-17
Hey, thanks for the info.  And anyone who knows assembly language has got no business messing about with anything as bloated as Windows! :biggrin:

---

### Post by MCVenom on 2010-02-17
> **quixote said:**
> Hey, thanks for the info.  And anyone who knows assembly language has got no business messing about with anything as bloated as Windows! :biggrin:
He knew at one point, at least. I discovered his old programming books (there were tons ^^; ) when we were cleaning out an old storage garage of his. I also discovered a Sega Genesis and an old Sega Game Gear, to put that 'at one point' in perspective :lolflag:

And no problem, no use in this topic just taking up space :p

---

### Post by KickNazer on 2010-02-19
I am having the exact same issue. GPARTED sees my partitions as I used it to srink my Winodws XP SP3 NTFS partition getting ready to install Ubuntu 9.10. I left the new space unallocated, and GPARTED sees that fine too and Ubuntu Live mounts the windows partition fine as well. However, when I get to the installer, the screen that should show up to prepare a dual-boot (the one labeled "prepare disk space") does not come up. Instead, it does to the one labeled "prepare partitions" and shows none. Please help? My harddrive and DVD drive are SATA. 

Thanks!

---

### Post by MCVenom on 2010-02-19
> **KickNazer said:**
> I am having the exact same issue. GPARTED sees my partitions as I used it to srink my Winodws XP SP3 NTFS partition getting ready to install Ubuntu 9.10. I left the new space unallocated, and GPARTED sees that fine too and Ubuntu Live mounts the windows partition fine as well. However, when I get to the installer, the screen that should show up to prepare a dual-boot (the one labeled "prepare disk space") does not come up. Instead, it does to the one labeled "prepare partitions" and shows none. Please help? My harddrive and DVD drive are SATA. 

Thanks!
Check your BIOS setting and see if you have an option for SATA mode; if its set to RAID then you should change it.

---

### Post by mxc1090 on 2010-02-25
Try this:

In the installer, open up a terminal window and type: sudo apt-get remove dmraid

[http://ubuntuforums.org/showthread.php?t=1311512](http://ubuntuforums.org/showthread.php?t=1311512)

---

