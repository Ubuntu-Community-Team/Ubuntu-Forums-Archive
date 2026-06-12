---
title: "HELP! Gutsy does not recognize my external hard drive"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by nabiscOGrahams on 2008-03-20
I just bought a 250gig toshiba external hard drive and ubuntu does not recognize it.

How do I get it to work?

If it is not possible then how do I switch back to windows xp.. I have a "Operating System CD" and a "Driver and Application Recovery CD" but the computer will not boot from either of them. Yes I have gone into BIOS and changed the boot order, but no dice.

Help me out.. Thanks.

---

### Post by HanaD on 2008-03-20
Aloha!

what version of ubuntu are you using?

what does it say when you plug in your HDD?

also post the output of following 2 comands at the terminal.

1) sudo fdisk -l 
2) lsusb

---

### Post by nabiscOGrahams on 2008-03-21
i am using ubuntu 7.10

here is the output of commands

pat@pat-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7120    57191368+  83  Linux
/dev/sda2            7121        7296     1413720    5  Extended
/dev/sda5            7121        7296     1413688+  82  Linux swap / Solaris

-------------------------------------------------------------------------

pat@pat-laptop:~$ lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

...Im ready to switch back to Windows if i cant get this hard drive to work... How do I fix this problem... or how do i obtain a boot cd and switch back?

---

### Post by HanaD on 2008-03-22
hmm,
i am having the same problem with western digital,
Ubuntu does not recognise it, but neither does windows, for me i have decided to exchange the HDD.

try using different computer or different cable to connect your HDD to your PC its not ubuntus bug, i hope so.

Does windows recognise your HDD?

Regards,
Hana

---

### Post by hardyheronnewb on 2008-06-27
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9774    78509623+   7  HPFS/NTFS
/dev/sda2            9775       19078    74734380   83  Linux
/dev/sda3           19079       19452     3004155    5  Extended
/dev/sda5           19079       19452     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

Bus 005 Device 006: ID 413c:3200 Dell Computer Corp. 
Bus 005 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 004: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c509 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


Hello. above is my output from the commands mentioned. i dont see my external here. its an internal ide drive that i put into an enclosure. 
I would really appreciate some help with this. i am running hardy heron.
thank you

---

