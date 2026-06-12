---
title: "Is my hdd incompatble with ubuntu?"
date: 2008-09-14
forum: Hardware
---

### Post by SpinningAround on 2008-09-14
I tried to install ubuntu but it simply wont work, I had different problems with the same result, it can be that the partition don't start or that the installation stop or even that it can't create a partition. The reason that I think it's the harddrive is that I recently bought new harddrives and since then haven't I been able to install ubuntu, with my old PATA drivers' where there no problems with installing.

Hardrive: 
Spinpoint F1 HD502IJ 
[http://www.samsung.com/global/business/hdd/productmodel.do?type=61&subtype=63&model_cd=240](http://www.samsung.com/global/business/hdd/productmodel.do?type=61&subtype=63&model_cd=240)

Motherboard:
MSI K8N Neo4-F 
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=177&maincat_no=1&cat2_no=&cat3_no=](http://global.msi.com.tw/index.php?func=proddesc&prod_no=177&maincat_no=1&cat2_no=&cat3_no=)

---

### Post by fourthofjuly on 2008-09-14
it would really be a surprise that hard disks would not be compatible with linux...!!! 

linux is known to detect and install a very wide range of hardware...

could you post  the error message(s) please?

---

### Post by 1/0 on 2008-09-14
Have you read page 3-17 in the motherboard manual? If not check the s-ata setting in the BIOS menu. It sounds like its disabled.

---

### Post by SpinningAround on 2008-09-15
> **fourthofjuly said:**
> it would really be a surprise that hard disks would not be compatible with linux...!!! 

linux is known to detect and install a very wide range of hardware...

could you post  the error message(s) please?

That is what surprise me, when I try to install it these days does the installation load the partitioner (progress bar finish) then it lock-up completely and a hard reboot is required.

I updated my bios as I maybe thought it might have a role to play and it did have one little effect, I noticed that grub was installed but on the wrong harddrive due to this drive having first priority to boot. The only time I managed to install ubuntu was with the alternative cd, but it didn't boot anyway, the reason do I know now since grub was installed on the "wrong" harddrive. The reason I used the alternative cd was that the normal installation didn't work, I think I got a error back then saying "errno 30".

try to make it a little clearer with the harddrives.
2 new Spinpoint F1 HD502IJ 
1 old (ATA-100!) WD

I think that the boot priority was like this
1. PATA drive from Western Digital (slave)
2. HD502IJ
3. HD502IJ
Reason I think this is I also installed windows on the 2nd drive, that I where able to boot (standard windows boot). Before I updated bios after that did grub show up.

1. PATA drive <- Grub here (from a earlier install)
2. HD502IJ <- windows here
3. HD502IJ <- ubuntu suppose to be here

After I updated bios did I notice this so I changed it to
1. HD502IJ 
2. HD502IJ 
3. PATA drive 
I thought this would help with the ubuntu installation, but the problem is still there, I get a complete lock-up after the partitioner is loaded. My guess is that the computer lock up while ubuntu scan the drives.

**1/0**
I checked if SATA was enabled and it was, no easy solution sadly as it look :(

Is there some way to clean the drives, maybe deleting mbr (grub) from PATA drive would help?

---

### Post by fourthofjuly on 2008-09-15
so you've 3 hard drives on your system...

are you sure your drive jumper settings are alright?

maybe you can use only 2 drives at a time alternatively to check if any one of the 3 drives is the problem?

---

### Post by SpinningAround on 2008-09-15
> **fourthofjuly said:**
> so you've 3 hard drives on your system...

are you sure your drive jumper settings are alright?

maybe you can use only 2 drives at a time alternatively to check if any one of the 3 drives is the problem?

I tried that today, removed the PATA drive hoping that something would change, but the installation still maybe a complete lock-up when scanning the drives. Can it be that Win XP screw it up?

Thanks for helping me out :)

PS: I did a complete new installation of XP today after I removed the PATA disk, before I installed XP did I try to install ubuntu, that time did the program handle the partition and the disk fine, but it was still not able to write a ext3 partition to the 2nd disk.

---

