---
title: "Internal Card Reader Alcor"
date: 2008-06-28
forum: Hardware
---

### Post by 6205 on 2008-06-28
I am trying to get to work under Hardy my internal USB card reader, but so far without a success. Command [COLOR="Blue"]lsusb[/COLOR] or [COLOR="Blue"]lsusb -v[/COLOR] in terminal is useless -> 

Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:00db Microsoft Corp.
Bus 003 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

In Windows XP is everything fine, it was recognized as Generic USB device but Ubuntu 8.04 don't see it  and only led diod on it is flashing rapidly. OpenSUSE 11.0 is different story. It's working perfectly like under WinXP and [COLOR="Blue"]lsusb[/COLOR] shows this ->

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 004 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As can you see, everything is different. Now can somebody tell me how to get the same results in Hardy pls? Maybe some easy how-to or link to ubuntu packages with drivers to that Alcor chipset will be helpfull, because i really don't want to stuck with openSUSE only because it has better hardware support...

Thanks.

---

### Post by 6205 on 2008-06-29
Nobody nothing?

:(

---

### Post by 6205 on 2008-07-03
Thanks for help :(

---

### Post by stchman on 2008-07-03
> **6205 said:**
> I am trying to get to work under Hardy my internal USB card reader, but so far without a success. Command [COLOR="Blue"]lsusb[/COLOR] or [COLOR="Blue"]lsusb -v[/COLOR] in terminal is useless -> 

Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:00db Microsoft Corp.
Bus 003 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

In Windows XP is everything fine, it was recognized as Generic USB device but Ubuntu 8.04 don't see it  and only led diod on it is flashing rapidly. openSUSE 11.0 is different story. It's working perfectly like under WinXP and [COLOR="Blue"]lsusb[/COLOR] shows this ->

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 004 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As can you see, everything is different. Now can somebody tell me how to get the same results in Hardy? Maybe some easy how-to or link to ubuntu packages with drivers to that Alcor chipset will be helpfull, because i really don't want to stuck with openSUSE only because it has better hardware support...

Thanks.

If you cannot get the card reader to work then you can get a USB SD/xD reader.  They are about $10 on ebay.  What kernel is openSUSE using?

---

### Post by 6205 on 2008-07-03
Sorry but i don't plan to buy a new reader. These things must simply work because it's generic USB device. OpenSUSE 11.0 has kernel 2.6.25.5-1.1 and i'm very suprised how advanced this system is in comparision with Ubuntu. More polished GNOME, feature complete, better repositories, better font rendering and great HW support. I have still little more sympathy for Ubuntu, but propably not for long...

Added OpenSUSE 11.0 [COLOR="Blue"]lsscsi[/COLOR] output ->

[0:0:0:0]    disk    ATA      SAMSUNG SP0812N  TK10  /dev/sda
[1:0:0:0]    cd/dvd  TEAC     DV-W516GDM       M4S2  -       
[2:0:0:0]    disk    Generic  USB SD Reader    1.00  /dev/sdb
[2:0:0:1]    disk    Generic  USB CF Reader    1.01  /dev/sdc
[2:0:0:2]    disk    Generic  USB SM Reader    1.02  /dev/sdd
[2:0:0:3]    disk    Generic  USB MS Reader    1.03  /dev/sde

---

### Post by stchman on 2008-07-03
> **6205 said:**
> I don't plan to buy a new reader. These things must simply work because it's generic USB device.
OpenSUSE 11.0 has kernel 2.6.25.5-1.1 and i'm very suprised how advanced this system is in comparision with Ubuntu. More polished GNOME, feature complete, better repositories, better font rendering, great HW support..bla bla...but i have still little more sympathy for Ubuntu, but not for long..

Added OpenSUSE 11.0 [COLOR="Blue"]lsscsi[/COLOR] output ->

[0:0:0:0]    disk    ATA      SAMSUNG SP0812N  TK10  /dev/sda
[1:0:0:0]    cd/dvd  TEAC     DV-W516GDM       M4S2  -       
[2:0:0:0]    disk    Generic  USB SD Reader    1.00  /dev/sdb
[2:0:0:1]    disk    Generic  USB CF Reader    1.01  /dev/sdc
[2:0:0:2]    disk    Generic  USB SM Reader    1.02  /dev/sdd
[2:0:0:3]    disk    Generic  USB MS Reader    1.03  /dev/sde

I have a bad feeling that Ubuntu's kernel is somehow crippled down in terms of hardware support, because OpenSUSE has no special restricted drivers or utilities installed...

Then you should use OpenSUSE instead of Ubuntu.  Choice is a great thing.  The kernel in Ubuntu Hardy is 2.6.24-19 so SUSE has a later kernel.

---

### Post by 6205 on 2008-07-04
I don't thing that this is related to kernel version. Generic USB devices should work in linux like yours or mine generic USB keys are working, so should this reader working too..

---

