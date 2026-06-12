---
title: "Partitions table... disapeared?"
date: 2008-08-24
forum: Hardware
---

### Post by vigon on 2008-08-24
Hi! First, I apologise for my very poor english but i'll try to explain my problem as clearly as possible.

I have installed different linux distributions on my external hdd for use on a eeePC (and, actually by pure curiosity). The last I have installed is Mandriva 2008. Ubuntu and Xubuntu were already installed.

But now, when I try to see my partitions with gparted, my disk seems to be... empty! But the different distributions 	
manifestly boot correctly... I have a FAT32 partition too for my documents on the same disk. When I try to edit the partitions by booting my computer with a live CD, the same problem appears. Moreover, I can see my disks on my desktop! (regardless of the version booted)

I PERHAPS have an idea of the origin of my problem: maybe I have too much "primary partitions" on my disk. But my knowledges in this domain are unsuffiscient to understand the problem correctly.

So... how can I find my partitions back and edit them? By fixing the MBR? (under windows with a fixmbr...? It doesn't seems to be an elegant solution...)

Thanks for help!
Vig

---

### Post by caljohnsmith on 2008-08-24
Welcome to the forums, vigon. :)
> **vigon said:**
> 
I PERHAPS have an idea of the origin of my problem: maybe I have too much "primary partitions" on my disk. But my knowledges in this domain are unsuffiscient to understand the problem correctly.
I don't think that could be the problem, because no respectable partition editor will let you create more than four primary partitions on your HDD; in other words, the fact that you can use that HDD OK means you don't have too many primary partitions, because it's impossible to have more than four primary partitions on a usable HDD.
> **vigon said:**
> 
So... how can I find my partitions back and edit them? By fixing the MBR? (under windows with a fixmbr...? It doesn't seems to be an elegant solution...)

I wouldn't recommend using "fixmbr", because that will erase Grub in the MBR and replace it with the Windows boot loader. What do you get from the following command:
```
sudo fdisk -lu
```
That should show all your HDDs and partitions. Also, in gparted, are you sure you're selecting the correct HDD? When you first start gparted, it usually defaults to reading your first HDD, or your internal one. In the upper right corner, there is "/dev/sda" type button to click on and change HDDs. 

If you are using that HDD fine, then I really doubt there is anything wrong with its partition table at this point, so please don't rebuild your partition table just yet. :)

---

### Post by vigon on 2008-08-24
I'm absolutely sure that I check the correct disk. (on an eeePC, there's only one hdd with a capacity of 4GB, my external HDD have 160GB and the disks are clearly displayed in gparted)

Thanks for the fdisk command. I have tried to use fdisk before but didn't succed :).


This is what the command return: (I have added some comments)

Disque /dev/sda: 4001 Mo, 4001292288 octets (//More than probably my internal flash HDD - containing my winXP)
4 heads, 63 sectors/track, 31012 cylinders, total 7815024 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x29202920

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1              63       64511       32224+  ef  EFI (FAT-12/16/32)
/dev/sda2   *       64512     7812755     3874122    7  HPFS/NTFS

Disque /dev/sdb: 160.0 Go, 160041885696 octets (//More than probably my external HDD. Partitions seem to be ok! Great... but why gparted doesn't see them, regardless of the computer or distribution I use???)
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x5b6ac646

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1              63    45833444    22916691    5  Extended
/dev/sdb2        45833445   312576704   133371630    b  W95 FAT32
/dev/sdb3   *    13221495    24868619     5823562+  83  Linux
/dev/sdb5             126    10490444     5245159+  83  Linux
/dev/sdb6        10490508    12578894     1044193+  82  Linux swap / Solaris
/dev/sdb7        12578958    13221494      321268+  82  Linux swap / Solaris
/dev/sdb8        24868683    41238854     8185086   83  Linux
/dev/sdb9        41238918    42427664      594373+  82  Linux swap / Solaris
/dev/sdb10       42427728    45833444     1702858+  83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

Disque /dev/sdc: 2032 Mo, 2032664576 octets (//What damned is it? I don't have any 2GB disk, except my USB drive but it wasn't connected when I typed the command in the terminal...?)
41 heads, 40 sectors/track, 2420 cylinders, total 3970048 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x02808e9a

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1   *         249     3970047     1984899+   b  W95 FAT32


-----

I'm really lost. Why my disk isn't recognized by gparted regardless of the computer I use (I've tried to connect it on my desktop pc, running under Ubuntu but... exactly the same problem).

What's this disk sdc...?

The more I thought, the less I understand... I need an external brain ^^ (I hope it will be recognized by my body)

Thanks for your answer, caljohnsmith :).

---

### Post by vigon on 2008-08-24
Ok... the 2GB is a SD disk :)... ha ha sorry.

But it doesn't solve the problem.

---

### Post by caljohnsmith on 2008-08-24
Your fdisk output shows your external HDD just fine, with all its partitions. So it looks like the problem is with gparted, not with you losing your partitions. How are you running gparted? Try running it from a Live CD with:
```
gksudo gparted
```

---

### Post by vigon on 2008-08-24
Exactly the same... BUT a message appeared in the terminal! 

"On ne peut avoir de partitions qui se chevauchent"

(means something like "Overlaping partitions are not allowed")

God damned...

---

### Post by caljohnsmith on 2008-08-24
How did you originally set up all those partitions? Did you use gparted or something else? 

One thing I noticed from you fdisk output is that your logical partitions do not stop and start exactly at the partition boundaries. In other words, you've got little gaps of unused space on your HDD. That's not a good sign, but I wouldn't think that in itself would prevent gparted from showing your partition structure.

---

### Post by vigon on 2008-08-24
I've initially manually managed my partitions. But for my last installation (Mandriva as said above) I let it automatically configure the partition table by selecting "use the free space" (I had previously created a gap on the disk to let enough space for the Mandriva installation).

So, it seems to be a real problem if a well understand...
The date on this disk aren't critical. I used it as a "test". Perhaps I could format the disk or delete the partitions with fdisk... But the scientific I am doesn't like to get rid of a problem without understand ^^.

---

### Post by caljohnsmith on 2008-08-24
> **vigon said:**
> 
So, it seems to be a real problem if a well understand...
The date on this disk aren't critical. I used it as a "test". Perhaps I could format the disk or delete the partitions with fdisk... But the scientific I am doesn't like to get rid of a problem without understand ^^.
Well, if you can afford to experiment on that HDD, I would definitely give "testdisk" a try and let it rebuild your HDD's partition table. That might be enough to fix whatever is causing gparted to balk. I believe testdisk has an option to first backup your HDD's partition table before modifying it, so you shouldn't have anything to lose. Or you can back up your partition table yourself with:
```
sudo dd if=/dev/sda of=MBR.backup bs=512 count=1
```
That actually copies the entire master boot record (MBR) which contains the partition table. See this [testdisk tutorial]("http://www.users.bigpond.net.au/hermanzone/p21.html") if you need help getting started using testdisk.

---

### Post by vigon on 2008-08-24
Ok! I will try this...

Thanks.

---

### Post by vigon on 2008-08-24
Ok so... this is what I read now:


ubuntu@ubuntu:~$ testdisk /list /dev/sdc
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sdc - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512

Disk /dev/sdc - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 E extended                 0   1  1  2852 254 63   45833382
 2 P FAT32                 2853   0  1 19456 254 63  266743260
 3 * Linux                  823   0  1  1547 254 63   11647125
Space conflict between the following two partitions
 1 E extended                 0   1  1  2852 254 63   45833382
 3 * Linux                  823   0  1  1547 254 63   11647125


What can I do?

---

### Post by caljohnsmith on 2008-08-24
> **vigon said:**
> 
Space conflict between the following two partitions
 1 E extended                 0   1  1  2852 254 63   45833382
 3 * Linux                  823   0  1  1547 254 63   11647125

Well that above error definitely looks like your problem; fortunately I've never had much need to use testdisk, so I'm not sure of the exact steps in testdisk you would use to resolve it. Did you see that tutorial I linked to in my last post? I think that will help you figure out testdisk. Also, when you use testdisk for anything other than just listing your partitions, be sure to run it as root:
```
sudo testdisk
```

---

