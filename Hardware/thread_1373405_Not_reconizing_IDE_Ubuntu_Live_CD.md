---
title: "Not reconizing IDE Ubuntu Live CD"
date: 2010-01-05
forum: Hardware
---

### Post by rickiibeta on 2010-01-05
Hi guys, let me start by expressing appreciation to those of you who are more knowledgeable than myself. As an introduction i would like to point out that i have, indeed, google'd this for about the last two hours... i hope you guys can help.

i am trying to recover some files for a friend off of a drive that will not boot.  
 
by will not boot i mean that it will not allow my compy to pass to even the bios screen if it is the master, and if it is set up as a slave along side my 300g velociraptor sata (awesome btw), it won't pass the windows 7 boot screen...  
  
when i run the fdisk -l on the ubuntu live cd (9.04) it returns to the prompt... that is to say:[INDENT]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 

[/INDENT]i am pretty sure that this means that the drive is not recognized, however it is recognized at the bios... i am very confused. help please.  
  
[e]: i ran fdisk -l with the VR attached and returned:
[INDENT] To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03042e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36482   293032960    7  HPFS/NTFS
ubuntu@ubuntu:~$[/INDENT]

[e]: i downloaded and ran testdisk off of the ubuntu rescue remix and it only displayed the cd/dvd drive...

---

### Post by rickiibeta on 2010-01-05
Guys, i really need help with this...  
  
the drive is showing up in Bios, but NOT in testdisk... that concerns me.

what would cause an ide drive to do this?

[e]:here is a screenshot of the testdisk screen. i am positive BIOS reconizes it, and says the size.  [http://imgur.com/T8IU7](http://imgur.com/T8IU7)

---

