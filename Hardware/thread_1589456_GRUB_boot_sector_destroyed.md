---
title: "GRUB boot sector destroyed"
date: 2010-10-06
forum: Hardware
---

### Post by Shompol on 2010-10-06
I installed Ubuntu as a dual boot with existing Windows 7, the next day  the boot sector is gone, most likely corrupted by a windows trojan or a  rogue app.
Needless to say, the blame is pinned on me.

How can I restore boot sector with GRUB?

---

### Post by drs305 on 2010-10-06
From a LiveCD:
Substitute your Ubuntu partition for **XY**. Substitute your Ubuntu *drive **only*** for sd**X**

```
sudo mount /dev/sdXY /mnt  # Example  sudo mount /dev/sda5
sudo grub-install --root-directory=/mnt /dev/sd**X**

```

---

### Post by oldfred on 2010-10-06
You just may have win7 software that does not comply with standards.
Grub2 team is looking for unique issues to see if they can work around the problem.

If you have 2 drives an advantage of booting grub on the other drive.
Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Shompol on 2010-10-07
Thank you. I was not sure which partition to reinstall grub, used main Linux partition, and it worked. 
[FONT=monospace]
The computer is from Dell, and I see that the first partition is called DellUtility 41 MB FAT, so they are the prime suspect for boot corruption.

Luckily, I convinced the owner that she does not need Windows, so will just disable that boot option for now.
[/FONT]

---

