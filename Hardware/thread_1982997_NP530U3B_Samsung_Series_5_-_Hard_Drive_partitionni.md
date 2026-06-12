---
title: "NP530U3B Samsung Series 5 - Hard Drive partitionning"
date: 2012-05-19
forum: Hardware
---

### Post by soutenues on 2012-05-19
Hi,


I just bought this laptop:
NP530U3B Samsung Series 5 
which is the French version( i'm from France..)
[http://www.samsung.com/fr/consumer/it/notebook/ultra-portable/NP530U3B-A02FR](http://www.samsung.com/fr/consumer/it/notebook/ultra-portable/NP530U3B-A02FR)

- It was  shipped with windows seven and i don't want it.
- Hard drive is an hybrid  ssd + mechanical model is : Hitachi HDD: Z5K500-500 / HTS545050A7E380 of 500GB : 16 GB is on SSD and the 
  remaining part is on mechanical.


I first of all decided to install both windows seven and Ubuntu 12.04
which were working, and later decided to wipe all disk content and install **only** ubuntu.

I boot with a usb key on ubuntu iso (made with unetbootin) without a problem, i saw (as far as i remember)
2 hard drives (1 of 16GB) as far as i remember.. /dev/sda with two partitions
and another disk with the remaning parts of 480GB approx..

I remove the partitions with fdisk and reboot on my usb key to reinstall from scratch..
now..i have this message ( grub rescue > ) and laptop don't let me boot as before on the usb key !!

I remove the hard drive from the laptop and put it in an USB external hard drive case, and i'm ablt now to connect it to my workstation.

So my question is! 
- What is the partitioning required , as initially ?
- Do i ned to create a 16GB partition at the beginning of the hard drive (/dev/sda1 = 16GB mounted as  / ) 
and create 2 others partitions ( e.g 500MB /dev/sda2 for swap   and  480GB   /dev/sda2  ext4 for /home/ e.g   ?)


ANy help appreciated, because i don't know now what is the partitionning scheme to apply .. :(


Thanks in advance for your help !!


NB: 
here below some informations :


On my workstation (1TB Hard drive /dev/sda) i remove the HD from my laptop and connect it though usb;
i did:
# tail -f  /var/log/syslog
(...)
May 19 20:10:33 Pandora kernel: [ 4780.924784] usb 1-1.1: new high-speed USB device number 7 using ehci_hcd
May 19 20:10:33 Pandora kernel: [ 4781.018769] usb-storage 1-1.1:1.0: Quirks match for vid 152d pid 2329: 8020
May 19 20:10:33 Pandora kernel: [ 4781.018874] scsi8 : usb-storage 1-1.1:1.0
May 19 20:10:33 Pandora mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1"
May 19 20:10:33 Pandora mtp-probe: bus: 1, device: 7 was not an MTP device
May 19 20:10:34 Pandora kernel: [ 4782.016527] scsi 8:0:0:0: Direct-Access     Hitachi  HTS545050A7E380       PQ: 0 ANSI: 2 CCS
May 19 20:10:34 Pandora kernel: [ 4782.017794] sd 8:0:0:0: Attached scsi generic sg2 type 0
May 19 20:10:34 Pandora kernel: [ 4782.019446] sd 8:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May 19 20:10:34 Pandora kernel: [ 4782.020357] sd 8:0:0:0: [sdb] Write Protect is off
May 19 20:10:34 Pandora kernel: [ 4782.020362] sd 8:0:0:0: [sdb] Mode Sense: 28 00 00 00
May 19 20:10:34 Pandora kernel: [ 4782.021246] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.021251] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.023611] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.023616] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.066594]  sdb:
May 19 20:10:34 Pandora kernel: [ 4782.069260] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.069265] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.069268] sd 8:0:0:0: [sdb] Attached SCSI disk





root@Pandora:~# fdisk -l 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953525168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00023d65

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT   <--- this is my workstation OS (not my laptop hd !!)
/dev/sda2          206848   307202047   153497600    7  HPFS/NTFS/exFAT
/dev/sda3       307204094  1953523711   823159809    5  Étendue
/dev/sda5       307204096   308178943      487424   82  partition d'échange Linux / Solaris
/dev/sda6       308180992  1953523711   822671360   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes                               <--- this is my laptop hd !!  No more  16GB partition... : (

255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x887c6b0a

Périphérique Amorce  Début        Fin      Blocs     Id  Système
root@Pandora:~#

---

### Post by soutenues on 2012-05-20
HI,

If someone using the same laptop or same hard drive could post his partition table, it'll be useful.

Thanks !

---

### Post by ahallubuntu on 2012-05-20
Partition your hard drive as if it were a simple 500GB hard drive.

The SSD is an "ExpressCache" which is a cache of  part of your hard drive, to speed up access to the most frequently accessed data and programs.  You can't access it as a separate partition.  The firmware will automatically decide how to use it to improve disk performance.

So you can have two partitions: one for "/" and one for swap.  (/home would be part of "/").  Some people prefer to have a separate /home partition.  So you could make a 20GB partition for Ubuntu, a 4GB swap partition (if you wish to use Hibernation), and use the rest for /home .

---

### Post by soutenues on 2012-05-20
Hi !

First of all thanks for taking time to answer ! Ithik i'm not the only one having problems ;)

Some points:
- I clearly saw a 16GB partitions before removing all.. but  now i'm not sure of anything..
- thanks for the nice recommendations ! on partitionning.
- now the laptop won't let me boot from usb so i sent the laptop for a RMA.
- when i'll receive a new one i'll do some other things ( create a ghost image of the disk for later reuse if so..) , then look again at the partition types and inform you in this thread, then apply your recommendations with partitionning scheme.

Next step: me to notify you of information.

Many thanks

---

### Post by ahallubuntu on 2012-05-20
There may well have been a 16GB partition - for Windows recovery.  Almost all new laptops have such partitions now.  I think it is a coincidence that you saw a 16GB partition and that your SSD cache is also 16GB.

Yes, it is a wise idea to make an image backup of your Windows hard drive before completely wiping it out.  That way, you can always restore it to factory condition if you ever need to sell it without Ubuntu on it.

If you had not sent it back already, I would have suggested making a new USB boot drive with whatever computer you are using right now and start over.  It sounds to me like something happened to the USB drive - maybe Grub was overwritten?  Or maybe the Samsung was trying to boot from the hard drive instead of the USB drive, and the hard drive was not set up correctly?  Oh, well, I guess it no longer matters if you have already sent it back.

---

### Post by fraba65 on 2012-05-21
I think I have to correct some issues related to the SSD.  I have this laptop up and running with original windows 7 on the regular 500GB hard disk drive and in parallel installed 12.04LTS on the 16GB SSD. At first I removed the usage of the express cache from windows 7 so that I was able to install 12.04 without major impact to my original windows partitions.
You are right with your statement that you definately saw the 16GB SSD in UBUNTU installation screen because it´s really there. 
I installed 12.04 also via unetbootin image on USB stick and for me it worked only in one USB port. I don´t remember which one but it was one of the 2 regular ports on the right side and not the USB3.0 one.
In BIOS you should disable "fastboot" and you should see the stick in bios menue where you can change the boot order. It took me 2 or three reboots with connected stick so that the stick was visible in the bios. 
After this it worked perfect but don´t forget to install grub on  "sda" and not on "sdb" (the SSD!!!) because the system can only boot from the regular hard disk.
Result of this installation is booting UBUNTU from grub takes about 12 seconds. :)



Here is the output from fdisk -l


[COLOR=Blue]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xcb9885ab

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143593471    71693312    7  HPFS/NTFS/exFAT
/dev/sda3       931295232   976769023    22736896   27  Hidden NTFS WinRE
/dev/sda4       143593472   931295231   393850880   27  Hidden NTFS WinRE

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 Köpfe, 63 Sektoren/Spur, 1946 Zylinder, zusammen 31277232 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7c62

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1            2048    22259711    11128832   83  Linux
/dev/sdb2        22259712    31262719     4501504   82  Linux Swap / Solaris[/COLOR]

---

### Post by soutenues on 2012-05-26
Thanks taking time to answer !!

Here my fdisk -l result now that i received my NEW laptop, and installed 12.04 on the whole disk with full-encryption (just a boot and a ciphered container) :

root@laptop:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets
taille d'E/S (minimale / optimale) : 4096 octets / 4096 octets
Identifiant de disque : 0x00082b0c

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Étendue
La partition 2 ne débute pas sur une frontière de cylindre physique.
/dev/sda5          501760   976771071   488134656   83  Linux

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 têtes, 63 secteurs/piste, 1946 cylindres, total 31277232 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x74f02dea

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1            2048    22259711    11128832   73  Inconnu
/dev/sdb2        22259712    31262719     4501504   84  OS/2 masquée disque C:

Disk /dev/mapper/sda5_crypt: 499.8 GB, 499847790592 bytes
255 têtes, 63 secteurs/piste, 60769 cylindres, total 976265216 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets
taille d'E/S (minimale / optimale) : 4096 octets / 4096 octets
Identifiant de disque : 0x00000000

Le disque /dev/mapper/sda5_crypt ne contient pas une table de partitions valable

Disk /dev/mapper/laptop-root: 495.6 GB, 495615737856 bytes
255 têtes, 63 secteurs/piste, 60255 cylindres, total 967999488 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets
taille d'E/S (minimale / optimale) : 4096 octets / 4096 octets
Identifiant de disque : 0x00000000

Le disque /dev/mapper/laptop-root ne contient pas une table de partitions valable

Disque /dev/mapper/laptop-swap_1 : 4181 Mo, 4181721088 octets
255 têtes, 63 secteurs/piste, 508 cylindres, total 8167424 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets
taille d'E/S (minimale / optimale) : 4096 octets / 4096 octets
Identifiant de disque : 0x00000000

Le disque /dev/mapper/laptop-swap_1 ne contient pas une table de partitions valable


----------------------------------------------------------------------------------------------


Here now originally fdisk -l when there was only win7 on the NEW laptop i received.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xcb9885ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   931299327   465546240    7  HPFS/NTFS/exFAT
/dev/sda3       931299328   976773119    22736896   27  Hidden NTFS WinRE

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    22259711    11128832   73  Unknown
/dev/sdb2        22259712    31262719     4501504   84  OS/2 hidden C: drive

Disk /dev/sdc: 4005 MB, 4005560320 bytes
251 heads, 20 sectors/track, 1558 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b392f

   Device Boot      Start         End      Block         Id  System
/dev/sdc1   *           1     7823359     3911679+  83  Linux


I've now just a problem which is the suspend2ram, or 2 disk
that is working but not automatically when i close the screen...
I mean i have to do sudo pm-suspend e.g to do a suspend2ram.
I'll maybe open a new post if none exist...


Thanks again !
Post can be closed ..? ??..

---

### Post by gspidey on 2012-06-09
Hi to everyone,

Same laptop here. I thought the 16gb disk was a cache disk part of the 500gb included disk, but I removed that disk and the ssd 16 gb is still there.

So I had no problem formatting it and making extra space to my sata disk. There's no problem with it it's always nice to have an extra ssd storage. :)

Extra tip: if you're planning to change the included disk, find a 7mm one or you will be surprised.

---

### Post by delfio on 2012-06-13
> **fraba65 said:**
> At first I removed the usage of the express cache from windows 7 so that I was able to install 12.04 without major impact to my original windows partitions.

How can i remove the usage of the express cache from windows 7?

---

### Post by s7dhansh on 2012-07-20
> How can i remove the usage of the express cache from windows 7?

You can simply delete the 10 gb partition of your 16gb ssd to remove expresscache. 
For a dual boot I would suggest installing ubuntu on that 10gb. Its amazingly fast. And even without expresscache, you won't notice any speed difference in windows.

In case you want to get expresscache back, follow [http://forum.notebookreview.com/samsung/638788-guide-expresscache-i-want-my-expresscache-back-edition.html](http://forum.notebookreview.com/samsung/638788-guide-expresscache-i-want-my-expresscache-back-edition.html)

The 4 gb partition on the ssd is for sleep/suspend. I won't touch it because I like the quick wake when I am in windows.

---

### Post by fraba65 on 2012-07-20
> **s7dhansh said:**
> 
The 4 gb partition on the ssd is for sleep/suspend. I won't touch it because I like the quick wake when I am in windows.

You only need the 4gp SSD-partition for hibernate modus. Regular standby/sleep works without this. I´ve used the 4gb partition for /swap because I never use the hibernate modus. Sleep/suspend is enough forme because I normally use my ultrabook several times a day.

Nevertheless I have also still problems with suspend when I close the lid. This does not work. I always have to press the power button and then choose suspend manually. Wake up from suspend works fine now...
The strange thing is that it also does not work when running Windows 7. It worked a while but after installing Ubuntu 12.04 and getting suspend in general working it didn´t work again when I close the lid. Opening the lid reawakes the ultrabook from suspend under Windows 7 so there is maybe no mechanical problem... :confused:
Anybody with the same problems?

---

### Post by montolla on 2013-01-24
> **soutenues said:**
> Hi,


I just bought this laptop:
NP530U3B Samsung Series 5 
which is the French version( i'm from France..)
[http://www.samsung.com/fr/consumer/it/notebook/ultra-portable/NP530U3B-A02FR](http://www.samsung.com/fr/consumer/it/notebook/ultra-portable/NP530U3B-A02FR)

- It was  shipped with windows seven and i don't want it.
- Hard drive is an hybrid  ssd + mechanical model is : Hitachi HDD: Z5K500-500 / HTS545050A7E380 of 500GB : 16 GB is on SSD and the 
  remaining part is on mechanical.


I first of all decided to install both windows seven and Ubuntu 12.04
which were working, and later decided to wipe all disk content and install **only** ubuntu.

I boot with a usb key on ubuntu iso (made with unetbootin) without a problem, i saw (as far as i remember)
2 hard drives (1 of 16GB) as far as i remember.. /dev/sda with two partitions
and another disk with the remaning parts of 480GB approx..

I remove the partitions with fdisk and reboot on my usb key to reinstall from scratch..
now..i have this message ( grub rescue > ) and laptop don't let me boot as before on the usb key !!

I remove the hard drive from the laptop and put it in an USB external hard drive case, and i'm ablt now to connect it to my workstation.

So my question is! 
- What is the partitioning required , as initially ?
- Do i ned to create a 16GB partition at the beginning of the hard drive (/dev/sda1 = 16GB mounted as  / ) 
and create 2 others partitions ( e.g 500MB /dev/sda2 for swap   and  480GB   /dev/sda2  ext4 for /home/ e.g   ?)


ANy help appreciated, because i don't know now what is the partitionning scheme to apply .. :(


Thanks in advance for your help !!


NB: 
here below some informations :


On my workstation (1TB Hard drive /dev/sda) i remove the HD from my laptop and connect it though usb;
i did:
# tail -f  /var/log/syslog
(...)
May 19 20:10:33 Pandora kernel: [ 4780.924784] usb 1-1.1: new high-speed USB device number 7 using ehci_hcd
May 19 20:10:33 Pandora kernel: [ 4781.018769] usb-storage 1-1.1:1.0: Quirks match for vid 152d pid 2329: 8020
May 19 20:10:33 Pandora kernel: [ 4781.018874] scsi8 : usb-storage 1-1.1:1.0
May 19 20:10:33 Pandora mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1"
May 19 20:10:33 Pandora mtp-probe: bus: 1, device: 7 was not an MTP device
May 19 20:10:34 Pandora kernel: [ 4782.016527] scsi 8:0:0:0: Direct-Access     Hitachi  HTS545050A7E380       PQ: 0 ANSI: 2 CCS
May 19 20:10:34 Pandora kernel: [ 4782.017794] sd 8:0:0:0: Attached scsi generic sg2 type 0
May 19 20:10:34 Pandora kernel: [ 4782.019446] sd 8:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May 19 20:10:34 Pandora kernel: [ 4782.020357] sd 8:0:0:0: [sdb] Write Protect is off
May 19 20:10:34 Pandora kernel: [ 4782.020362] sd 8:0:0:0: [sdb] Mode Sense: 28 00 00 00
May 19 20:10:34 Pandora kernel: [ 4782.021246] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.021251] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.023611] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.023616] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.066594]  sdb:
May 19 20:10:34 Pandora kernel: [ 4782.069260] sd 8:0:0:0: [sdb] No Caching mode page present
May 19 20:10:34 Pandora kernel: [ 4782.069265] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 19 20:10:34 Pandora kernel: [ 4782.069268] sd 8:0:0:0: [sdb] Attached SCSI disk





root@Pandora:~# fdisk -l 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953525168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00023d65

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT   <--- this is my workstation OS (not my laptop hd !!)
/dev/sda2          206848   307202047   153497600    7  HPFS/NTFS/exFAT
/dev/sda3       307204094  1953523711   823159809    5  Étendue
/dev/sda5       307204096   308178943      487424   82  partition d'échange Linux / Solaris
/dev/sda6       308180992  1953523711   822671360   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes                               <--- this is my laptop hd !!  No more  16GB partition... : (

255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x887c6b0a

Périphérique Amorce  Début        Fin      Blocs     Id  Système
root@Pandora:~#



Hello


First:
You need to go to the bios setup and find a option like "fast boot" or "less post boot information" and desable. Becouse the machine boot more fast but do not find other media to boot. On disable mode, the machine look for all hardware on the machine and then, boot from the usb stick.

Second:

You need to repart the hard drive:
on hd make a swap partition at the begining about 4 Gb.
On the rest of hd make a ext4 partition for home.
On ssd make a full ext4 partition for / (root folder).
Then on the partition wizard, select the hd for boot or grub install. Becouse the machine only boot from hd and not from ssd.

Next just eny linux distribution (ubuntu).

And the faster samsung series 5 machine ubuntu inside.

Finally, you can enable the option on the bios setup for more fast boot.

Thanks

---

