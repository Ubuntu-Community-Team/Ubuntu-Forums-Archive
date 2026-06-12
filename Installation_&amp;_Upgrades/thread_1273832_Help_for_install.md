---
title: "Help for install"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by roajames on 2009-09-23
I can't install ubuntu onto my system. Have 2 other systems with XP and ubuntu, both working fine but this one is problematic. System has 3 SATA drives. Drive 1 : 80GB, Dive 2 : 320GB, Drive 3 : 750GB(unallocated for now cause initial ubuntu loading was unsuccessful)) have been trying to load unbuntu onto this Drive 3 - this would be partitioned in NTFS as : 100GB(for my docs), 250GB(for my music), 300GB(for software) and the balance around 100GB is where i want to load the unbuntu/bootloader. Have attempted many times but failed. Using the same install CD as i did for my other 2 systems. Just dont know what i am doing wrong, please help!!!!
](*,)
James

---

### Post by bmorency on 2009-09-23
You say it fails but what exactly is happening? Does it give you any errors? Where does it fail? During the install or when you try to boot the first time?

How about trying to have your ubuntu partition first and than the other partitions after? I thought I read somewhere before that your /boot partition/folder needs to be be before the 1024 cylinder on the hard drive. 650 gigs would definitely be past that spot on the hard drive. I'm not sure if that is still a limitation or not.


edit: I just found this. It talks about this cylinder limitation. The post is old but it could be the problem.
[http://www.linuxforums.org/forum/installation/48152-grub-mbr-boot-1024-cylinder-limit.html]("http://www.linuxforums.org/forum/installation/48152-grub-mbr-boot-1024-cylinder-limit.html")

---

### Post by roajames on 2009-09-23
bmorency thanks for the reply. install everthing works fine, inidicated sdc1 as where i want to install the bootloader(which is my 750GB 3rd partition of 100GB), I did not partition this, left it unallocated and ubuntu partitioner recognised it as free space, so i presume it will write the bootloader to this. after install and start up, just goes immediatelt into windows, no dual boot or grub - upon checking the drive in windows disk management, 2.5GB space was taken up in my 2nd disk as : 2.5GB unknown, 799mb unknown and nothing at all on my 3rd hard dive accept for the initial NTFS partitions. Any ideas or suggestions appreciated please

---

### Post by akakingess on 2009-09-23
I don't believe that windows will even see drives/partitions formatted with ext3 or ext4 which is what should be used for Ubuntu install, so that would explain why Windows is not seeing those partitions, but we still need to know exactly what is happening that it will not let you install Ubuntu, are you booting off of a Live CD, trying a WUBI install or what, please provide a few more details as to how you are attempting the install and then maybe we can assist.

---

### Post by gadolinio on 2009-09-24
Can you boot with the liveCD, open system--administration--gparted partition editor, and create an ext3 partition for ubuntu? does it let you install there?

---

### Post by bmorency on 2009-09-24
What happens if you make your first partition the 100gig partition with ubuntu on it and than make the other ones after it? maybe grub can't boot the 100 gig partition because it is so far on the drive.

---

### Post by roajames on 2009-09-25
will try doing that, or i may just uninstall the windows from the SATA 80GB and use this to install ubuntu using the entire disk

---

