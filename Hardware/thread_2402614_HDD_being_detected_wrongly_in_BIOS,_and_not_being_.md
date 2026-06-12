---
title: "HDD being detected wrongly in BIOS, and not being mounted"
date: 2018-10-02
forum: Hardware
---

### Post by sheruvs on 2018-10-02
Hi All,

This is my first post, and I have a unique and major issue. First a little background..

My original setup:
Intel® Core&#8482; i7-2600 CPU @ 3.40GHz × 8 
16 GB RAM
Internal HDD 1 - SSD ATA 512 GB - boot disk - C400-MTFDDAK512M
Internal HDD 2 - ATA 1 TB - Model Seagate ST1000DM003 
Ubuntu 16.04 LTS - 64b (Dual boot with Win 7)

During booting, Internal HDD 2 was giving some Drive Ready errors, so in order to backup data, I added an internal 4 TB disk Seagate - ST4000DM005 to the above setup. 

System did not fully boot even after 2-3 mins, so powered down and disconnected only the 4 TB disk and rebooted again.

Discovered that the 1 TB disk is not getting mounted in Ubuntu. Gparted throws up warning "Fsyncing/closing /dev/sdb: Input/Output error" and is not able to recognise the 1 TB drive.

Rebooted into BIOS and observed that the 1 TB drive is being detected as a 4 TB drive!! 

Tried changing the SATA data and power cable, and even tried connecting the 1TB disk on a different system, but no luck - same symptoms as above.

Then, booted again into Ubuntu and ran the following:

> uvs@uvs-ESPRIMO-P500:~$ sudo lshw -C disk
 *-disk                  
             description: ATA Disk
             product: C400-MTFDDAK512M
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 040H
             serial: 0000000012460365C33B
             size: 476GiB (512GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7e73438b
 *-disk
             description: ATA Disk
             product: ST1000DM003
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: CC46
             serial: S1D9YKS7
             size: 3950MiB (4142MB)
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512

Fortunately, I have another 1 TB working HDD of exactly the same make and model. So,I (disconnect the problematic disk) connected the working HDD to the system and ran same command as above:

> uvs@uvs-ESPRIMO-P500:~$ sudo lshw -C disk
[sudo] password for uvs: 
    *-disk                  
             description: ATA Disk
             product: C400-MTFDDAK512M
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 040H
             serial: 0000000012460365C33B
             size: 476GiB (512GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7e73438b
  *-disk
             description: ATA Disk
             product: ST1000DM003-1CH1
            vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
     version: CC46
     serial: S1D9YSEQ
     size: 931GiB (1TB)
     capabilities: partitioned partitioned:dos
     configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=c2092d18
uvs@uvs-ESPRIMO-P500:~$ 

Note the difference in sizes for the same models and interestingly, the problematic disk shows sector size as 512 (whereas it should be 4096) and also it does not have any 'signature'. What is the significance of the disk signature (I read that Windows  writes a unique ID into the MBR - is this of any significance in  Ubuntu?)

Another thing I have tried is that I swapped the controller cards between the two.
Observations: Both disks are being recognized in BIOS as 4 TB, and both the disks including the 'good' 1 TB HDD cannot be recognized by the OS and can't be mounted.

I put back the controllers to their original disks, and the 'good' disk is recognized in BIOS as 1 TB and can be mounted as earlier and is just fine.

So concluded that the controller of the 1 TB disk originally in the PC has gone for a toss, and somehow, this is due to the addition of the 4 TB disk that has messed up the original 1 TB disk.

I would like to know if there is any way to get the problematic disk working so as to retrieve data. Read of the tesdisk utility, but it requires the disk capacity to be correctly detected before attempting recovery. 

Any help would be greatly appreciated. 

TIA

---

### Post by sheruvs on 2018-10-03
Any update, anyone? It's dark in here. :(

---

### Post by Autodave on 2018-10-03
I would connect the HD to another computer and see what it says. If another computer reads it correctly, then I would say that you have a bad motherboard or at least a bad connector on the motherboard. If you get the same wrong info from the second machine, then I would think the the HD (controller) has failed.

---

### Post by sheruvs on 2018-10-03
Thank you for your reply.
I tried what you suggested, but in the other computer also, the BIOS detects it wrongly as 4 TB
Also changed the HD controllers, but with the different controller - also the same issue. So I suspect that something would have got written into the HDD which is causing the wrong detection. As I have shown the o/p of the list hardware command, the sector size is incorrect. 
I'm curious to know if by some means, I can directly access the HDD to correct / rewrite this sector info, if that could help.

---

### Post by deadflowr on 2018-10-03
Look at what hdparm shows.
If not installed
sudo apt install hdparm[/code]
look at the info with
```
sudo hdparm -I /dev/sdb
```
(Or whichever device you want to look at)

hdparm has a lot of options and features, you may review them in
```
man hdparm 
or 
hdparm -h 
```
I'm not sure how helpful it will be, though.
But it's something to look into, I would think.

---

### Post by oldfred on 2018-10-03
What do you mean when you say you swapped controller cards?
Drive card for a drive is unique a drive. It now often has internal settings for alignment & configuration.

---

### Post by Yellow Pasque on 2018-10-03
> **oldfred said:**
> What do you mean when you say you swapped controller cards?

I'm glad I'm not the only one who was puzzled by that.

---

### Post by sheruvs on 2018-10-06
As the make and model of the two drives were the  same, I interchanged the HD controller cards.
Did this after confirming that the firmware of the two controllers was the same version, I hoped that the failed drive would become accessible.

---

### Post by Autodave on 2018-10-06
If the drives are identical, that can be done: have done it before.  If the good controller card still gives the wrong info on the "bad" drive, then the drive has failed in some way: could be a sticking arm.  Since you changed the controller with no difference to the HD itself, you now know that the drive itself is failing / damaged.

---

### Post by oldfred on 2018-10-06
Even identical drives now are so precise that they have tuning parameters loaded into the configuration. 
I do not think an average user without sophisticated repair equipment can change parts on a drive.

---

