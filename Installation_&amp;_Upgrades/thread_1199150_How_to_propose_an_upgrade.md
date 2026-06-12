---
title: "How to propose an upgrade"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by AceCraft on 2009-06-28
Hi!

Meaby I will start from begin. More or less 2 months ago I have inattentively removed (using fdisk) Microsoft Windows XP partition from my dual boot disk and as the effect I have lost all data from that partition. Just recently (with great help from people from this forum and some friends) I managed to more or less restore lost data. So my first thought after restoring Windows was how I can prevent this kind of situation from happening again (I saw a number of topics with problem). As I couldn't find any good solution on Linux forums (or meaby I sought wrong phrase?) I've wrote this small piece of code, that I've put in .bashrc both in root and all users homefolders:
```

# fdisk & cfdisk extra security for inattentive Windows removal
alias fdisk='echo -e "\n--------------------------------";
	echo -e "WARNING: modifying and windows partitions with this\n program might wipe out Microsoft Windows system.\n Use on your own risk.";
	echo -e "---------------------------------\n";
	sleep 1;
	fdisk'

alias cfdisk='echo -e "\n--------------------------------";
	echo -e "WARNING: modifying and windows partitions with this\n program might wipe out Microsoft Windows system.\n Use on your own risk.";
	echo -e "---------------------------------\n";
	sleep 1;
	cfdisk'

```
I hope it's quite self-explanatory. I have tester it on Bash 3.2.48(1)-release and it works with no problem:
```

root@michal-laptop:~# fdisk -l /dev/sda

--------------------------------
WARNING: modifying and windows partitions with this
 program might wipe out Microsoft Windows system.
 Use on your own risk.
---------------------------------


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b452b44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   7  HPFS/NTFS
/dev/sda2            2491        5229    22001017+   5  Extended
/dev/sda3            5230       30401   202194090    7  HPFS/NTFS
/dev/sda5            2491        2733     1951866   82  Linux swap / Solaris
/dev/sda6            2734        5229    20049088+  83  Linux

```

Warning text appears after 1s.
Meaby it's very simple modification, that isn't worth of putting in official release, but nontheless the problem with accidental removing of system exists (at least for unexperiaced admins) and it would be good idea to propose this kind of warning for fdisk and cfdisk. Now, I have no idea where should I put that proposal (tried on [http://www.linuxdevcenter.com/](http://www.linuxdevcenter.com/) but it's quite confusing for me). Can anyone help me?

Thank you in advice!

---

