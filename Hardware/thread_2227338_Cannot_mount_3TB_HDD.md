---
title: "Cannot mount 3TB HDD"
date: 2014-06-01
forum: Hardware
---

### Post by krijeck2 on 2014-06-01
Hello,

I have a working Ubuntu 13.04 installation. I had two external USB 3TB drives with media on it. As I had enough space in the case I decided to install the HDDs directly into the computer with sATA. The drives are recognized with 
```
[FONT=Monaco]sudo lsblk -o NAME,UUID,FSTYPE,SIZE,LABEL,MOUNTPOINT[/FONT] 
```
but I am not able to mount them and I am not able to see the UUID.
the output is like that:
```
[FONT=Monaco]NAME   UUID                                 FSTYPE   SIZE LABEL  MOUNTPOINT[/FONT]
[FONT=Monaco]sda                                                 55,9G        [/FONT]
[FONT=Monaco]&#9500;&#9472;sda1 C30B-2A02                            vfat      94M        /boot/efi[/FONT]
[FONT=Monaco]&#9500;&#9472;sda2 85ff9102-9cdb-42b1-bba1-34d0858cdebd ext4    51,9G        /[/FONT]
[FONT=Monaco]&#9492;&#9472;sda3 c3a0e58f-9463-4d31-a580-130f0607a326 swap     3,9G        [SWAP][/FONT]
[FONT=Monaco]sdb                                                  1,4T        [/FONT]
[FONT=Monaco]&#9492;&#9472;sdb1 5804CBB404CB9402                     ntfs     1,4T media  /media/media[/FONT]
[FONT=Monaco]sdc                                                  1,4T        [/FONT]
[FONT=Monaco]&#9492;&#9472;sdc1 F87C8F9C7C8F53F2                     ntfs     1,4T series /media/series[/FONT]
[FONT=Monaco]sdd                                                  2,7T        [/FONT]
[FONT=Monaco]&#9492;&#9472;sdd1                                             349,3G        [/FONT]
[FONT=Monaco]sde                                                  2,7T        [/FONT]
[FONT=Monaco]&#9492;&#9472;sde1                                             349,3G [/FONT]
```

The new drives are sdd and sde. The drives are recognized but no UUID and also the size seems to be incorrect. 
When I try to mount I get the following error message:


[FONT=arial]NTFS signature is missing.
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/FONT]



just tried the following:
```
[FONT=Monaco]$ sudo parted -l[/FONT]
```[COLOR=#F5F5F5][FONT=Monaco]
[/FONT][/COLOR]```

[FONT=Monaco]Modell: ATA KINGSTON SKC300S (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sda:  60,0GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: gpt[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Dateisystem     Name  Flags[/FONT]
[FONT=Monaco] 1      1049kB  99,6MB  98,6MB  fat32                 boot[/FONT]
[FONT=Monaco] 2      99,6MB  55,8GB  55,7GB  ext4[/FONT]
[FONT=Monaco] 3      55,8GB  60,0GB  4179MB  linux-swap(v1)[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD15EADS-00P (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdb:  1500GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      32,3kB  1500GB  1500GB  primary  ntfs[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD15EADS-00S (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdc:  1500GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      1049kB  1500GB  1500GB  primary  ntfs[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD30EZRX-00M (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdd:  3001GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/4096B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      131kB   375GB  375GB  primary[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD30EZRX-00M (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sde:  3001GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/4096B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      131kB   375GB  375GB  primary[/FONT]
```

What can I do? Any ideas?

I am connected with SSH from remote,
Thanks,
krijeck

---

### Post by newbie2244 on 2014-06-01
I am not an expert, but . . .Perhaps, your system's address space is not large enough to recognize the full capacity of 2 3TB drives, in addition to other mounted devices.

---

### Post by krijeck2 on 2014-06-01
> **newbie2244 said:**
> I am not an expert, but . . .Perhaps, your system's address space is not large enough to recognize the full capacity of 2 3TB drives, in addition to other mounted devices.

ok, does mean what? how can I find it out? 
Thanks ...


Actually the system is Ubuntu 13.04 and the hardware its running on is pretty new. Actually this was my shopping list:
Intel Core i5-3470S, 4x 2.90GHz, boxed
Kingston HyperX Plug n Play DIMM Kit 8GB PC3-12800U CL9 (DDR3-1600)
ASUS HD7770-DC-1GD5-V2, Radeon HD 7770 GHz Edition, 1GB GDDR5, 2x DVI, HDMI, 1x DisplayPort
ASUS P8Z77-M Pro, Z77 (dual PC3-12800U DDR3)
be quiet! Shadow Wings SW1 Mid-Speed 120mm
Scythe Big Shuriken 2 Rev. B
be quiet! Straight Power E9 400W ATX 2.3 (E9-400W/BN190)

Then I added the [FONT=Tahoma]Kingston SSDNow KC300 60GB MLC SATA600 for the Ubuntu and two 1.5TB WD HDDs for Data. With no issues. Now with the two 3TB HDDs I have said issues. 
[/FONT]What I alos recognized was the sector size 4096 instead of 512. Does this make an issue?

Additionally I forgot to mention that the drives are full of data I do not want to loose!

---

### Post by newbie2244 on 2014-06-01
For starters, is your system 32-bit or 64-bit implementation?  Is your OS 32-bit or 64-bit?  

More questions:
1.   How did you format your hdd's?
2.   Was the original OS Windows? 32-bit or 64-bit?

Sometimes, depending on how you format the hdd  --   MBR versus GPT, you may limit the amount of data space that you can use on your 3TB hdd's.  Please see, for example,  the following:

[http://www.servethehome.com/fix-746gb-3tb-hard-drive-issue/](http://www.servethehome.com/fix-746gb-3tb-hard-drive-issue/).

[http://wdc.custhelp.com/app/answers/detail/a_id/2754/~/hard-drives-greater-than-2-tb-do-not-work-on-existing-operating-systems](http://wdc.custhelp.com/app/answers/detail/a_id/2754/~/hard-drives-greater-than-2-tb-do-not-work-on-existing-operating-systems). Actually, I think the limit in this case is 2.2TB.

---

### Post by krijeck2 on 2014-06-01
Hello again,
The Ubuntu version i have is a 64 bit version ([FONT=arial, helvetica, clean, sans-serif][COLOR=#393939]Linux 3.8.0-35-generic auf x86_64).[/COLOR][/FONT]
[FONT=arial, helvetica, clean, sans-serif][COLOR=#393939]How I formatted the drivers? - I do not know actually - I think I formatted them on OSX with NTFS (I have Tuxera NTFS installed). So this answers the second question that the OS was OSX (I do not have any Windows) 

Is it possible to find out if this is MBR or GPT? and if yes is it possible to change without killing all the data? 
The drives where installed in external WD enclosures and connected via USB2 long time without any problems. 

The second link you posted seems to tell that there is no way for me to operate them internal. :(
will read them in detail now ... 


[/COLOR][/FONT]

---

### Post by oldfred on 2014-06-01
Post this:
sudo parted -l

And better with gpt to use gdisk, it is in repository:
sudo apt-get install gdisk
sudo gdisk -l /dev/sdd       

 sudo gdisk -l /dev/sde

    
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

And since you have an UEFI install with gpt, you probably should be consistent and use gpt on all drives. I have been using gpt on my 160GB drive since 10.10 and even on my new flash drives with full installs.

---

### Post by newbie2244 on 2014-06-01
Thanks OldFred, the info is great.

---

### Post by krijeck2 on 2014-06-01
Thanks ...

here the output of [COLOR=#000000]sudo parted -l :
[/COLOR]

```
[FONT=Monaco]Modell: ATA KINGSTON SKC300S (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sda:  60,0GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: gpt[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Dateisystem     Name  Flags[/FONT]
[FONT=Monaco] 1      1049kB  99,6MB  98,6MB  fat32                 boot[/FONT]
[FONT=Monaco] 2      99,6MB  55,8GB  55,7GB  ext4[/FONT]
[FONT=Monaco] 3      55,8GB  60,0GB  4179MB  linux-swap(v1)[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD15EADS-00P (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdb:  1500GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      32,3kB  1500GB  1500GB  primary  ntfs[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD15EADS-00S (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdc:  1500GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/512B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      1049kB  1500GB  1500GB  primary  ntfs[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD30EZRX-00M (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sdd:  3001GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/4096B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      131kB   375GB  375GB  primary[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Modell: ATA WDC WD30EZRX-00M (scsi)[/FONT]
[FONT=Monaco]Festplatte  /dev/sde:  3001GB[/FONT]
[FONT=Monaco]Sektorgröße (logisch/physisch): 512B/4096B[/FONT]
[FONT=Monaco]Partitionstabelle: msdos[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags[/FONT]
[FONT=Monaco] 1      131kB   375GB  375GB  primary[/FONT]
```

```
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]sudo gdisk -l /dev/sdd [/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]GPT fdisk (gdisk) version 0.8.5[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partition table scan:[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  MBR: MBR only[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  BSD: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  APM: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  GPT: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]***************************************************************[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Found invalid GPT and valid MBR; converting MBR to GPT format.[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]***************************************************************[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Disk /dev/sdd: 5860533168 sectors, 2.7 TiB[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Logical sector size: 512 bytes[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Disk identifier (GUID): 136B6AE4-D7D4-47AC-8CCB-57E8B716A9B6[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partition table holds up to 128 entries[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]First usable sector is 34, last usable sector is 5860533134[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partitions will be aligned on 256-sector boundaries[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Total free space is 5127967341 sectors (2.4 TiB)[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Number  Start (sector)    End (sector)  Size       Code  Name[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]   1             256       732566015   349.3 GiB   0700  Microsoft basic data[/COLOR][/FONT][/COLOR]

```

```
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]sudo gdisk -l /dev/sde[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]GPT fdisk (gdisk) version 0.8.5[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partition table scan:[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  MBR: MBR only[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  BSD: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  APM: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]  GPT: not present[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]***************************************************************[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Found invalid GPT and valid MBR; converting MBR to GPT format.[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]***************************************************************[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Disk /dev/sde: 5860533168 sectors, 2.7 TiB[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Logical sector size: 512 bytes[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Disk identifier (GUID): BF6D2B0A-4AF8-4CB0-80CF-85400A757FAF[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partition table holds up to 128 entries[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]First usable sector is 34, last usable sector is 5860533134[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Partitions will be aligned on 256-sector boundaries[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Total free space is 5127967341 sectors (2.4 TiB)[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]Number  Start (sector)    End (sector)  Size       Code  Name[/COLOR][/FONT][/COLOR]
[COLOR=#F5F5F5][FONT=Monaco][COLOR=#000000]   1             256       732566015   349.3 GiB   0700  Microsoft basic data[/COLOR][/FONT][/COLOR]

```

I am not sure if I understand everything correctly but you mean I could fix my issue without loosing data? 
Makes me a little bit afraid! :)
Do the output tell you anything more?

thanks ... krijeck

---

### Post by newbie2244 on 2014-06-01
Can you access all your data on the 3TB hdd's? Pls let us know.                      [http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by newbie2244 on 2014-06-01
Can you access all your data on the 3TB hdd's? Pls let us know.

---

### Post by oldfred on 2014-06-01
Backups are important. But conversion should work.

But you have a 3TB drive formatted as MBR which means it is a 2TB drive. It has to be gpt to be fully useable.
 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)


Did you review the link on conversion with gdisk in post #6.

---

### Post by krijeck2 on 2014-06-02
> **newbie2244 said:**
> Can you access all your data on the 3TB hdd's? Pls let us know.

hello,

no I cannot access the data on the drives when built into the PC. I was able to access them when they were in their external USB2 enclosure.

@oldfred: 
youre right backups are important - but unfortunately I do not have enough disks to backup all data of these two 3TB drives. Actually I thought (at least until yesterday) that I put them in and everything is fine as it was with the two other drives (1,5TB). ;) yes I was that blind ...  
Funnily looking at the output of [FONT=Monaco][COLOR=#000000]sudo gdisk -l /dev/sdd[/COLOR][/FONT]  it seems to be MBR. is that strange or do I missunderstand the things? When they were connected via USB I was definitely able to access all the 3TB visible on these drives. 

I did a review of the link posted in post #6 but it seems that I am too stupid to understand and it seems that this is not a command line one command issue but a little bit tricky (in sense of time) to do. not easy cheesy as I thought ... ;) ... sorry but I am not (as you can imagine) a Linux expert. :)

---

### Post by oldfred on 2014-06-02
There have been a few 3TB drives with vendor specific configurations. They use two partitions and somehow violate the standard MBR or use non-standard sectors, or other specific configurations.
 If it works in your caddy, I would see what that vendor has as its specification for how it does it. But I would backup data and partition to standard gpt.

---

### Post by krijeck2 on 2014-06-02
> **oldfred said:**
> There have been a few 3TB drives with vendor specific configurations. They use two partitions and somehow violate the standard MBR or use non-standard sectors, or other specific configurations.
 If it works in your caddy, I would see what that vendor has as its specification for how it does it. But I would backup data and partition to standard gpt.

OK, the drives are from Western Digital of their Elements Series of external 3.5 USB drives with 3TB. Actually due to the fact that I did not expect any problems I did not note the exact naming of the drives. Will check when I remove them again. I plan now to remove them again and backup the data - then format them and put them in again. the only thing I am afraid of now is if the data is still available after i made the command [COLOR=#000000][FONT=Monaco]sudo gdisk -l /dev/sdd 
[/FONT][/COLOR] 
hope the data is still there ... 

is it possible to partition / format the HDD with USB connected and then put them in or should I put them in and then format - or does this make no difference with GPT? Actually I formatted them as they were still in their external enclosure.  [CENTER][COLOR=#000000][/COLOR][/CENTER]

---

### Post by oldfred on 2014-06-02
The -l command in gdisk only lists info.
And you have to issue the w command to write updated partition info with gdisk.

 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I have not used an external drive, but usually format with gparted.
      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

