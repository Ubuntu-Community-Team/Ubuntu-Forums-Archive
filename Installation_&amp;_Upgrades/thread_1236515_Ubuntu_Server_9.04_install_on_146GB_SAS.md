---
title: "Ubuntu Server 9.04 install on 146GB SAS"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by nbeeby on 2009-08-10
I am trying to install Ubuntu 9.04 Server onto a 146GB SAS drive within a Dell server.
 
This drive already has MS Windows Server 2008 Standard SP2 64bit installed in a partition (60GB). I would like to dual boot with Ubuntu. The disk is in Drive slot 0.
 
When I run the Ubuntu install I gat to the disk partition screen and I have no options of disk's or partitions - just a blank line. The remaning part of the drive 146GB drive is 'unallocated' but Ubuntu refuses to see it. Normally it would give me option to delete or resize existing partitions etc.
 
At first I thought Ubuntu couldn't see the disk at all so I added a 2nd, 74GB disk to the system (in Drive slot 1) which also has an NFTS partition, using 40GB of the drive. The Ubuntu install see's this drive as 'sdb'. Therefore the installer must be seeing the 146GB disk as 'sda' but not allowing me to use it.
 
Any thoughts or suggestions would be greatly appreciated.
 
Many Thanks,
 
Nick

---

### Post by phillw on 2009-08-10
The tutorials below cover most combinations.

[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Hope they are of help.

Regards,

Phill.

---

### Post by nbeeby on 2009-08-10
Thanks for the link, I've had a look through the tutorials but they only seem to cover the Ubuntu workstation install, i.e. with the nice GUI & i'm attempting an Ubuntu Server install. Also they don't cover problems during install - the install isn't allowing me to use my 146GB disk despite the fact I used the Shrink option within W2K8 Server to create some available space on the drive....

---

### Post by nbeeby on 2009-08-11
Does anyone have any further thoughts?
 
Thanks,
Nick

---

### Post by nbeeby on 2009-08-12
Any further thoughts from anyone?

---

