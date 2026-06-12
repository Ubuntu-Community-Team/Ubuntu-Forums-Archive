---
title: "External Hard drive not detected"
date: 2017-10-15
forum: Hardware
---

### Post by RobGoss on 2017-10-15
Hello everyone, I'm having a issue with a **Western digital ** 500-GB external hard drive. I was using this drive for testing ISO's for Ubuntu and had Ubuntu all loaded up and running on this device. One day I decided to boot up the external drive and it would not load the Ubuntu installation any more. On some of my machines it cannot even be detected not sure why 

So I decided to use this device for backups and cloning, for my Ubuntu systems but it will not allow me to save anything to this device. Do I have to format it to be detected on my machines? I've tried formatting and it will not allow me to do so. Any help would be greatly appreciated

---

### Post by westie457 on 2017-10-15
Hi, have you checked the 'smart' data yet?
Another tool to use is testdisk for problems that do not show in a smart report. 
Testdisk will stop with a message about major errors. 

Atm I have no access to Ubuntu so help will be limited.

---

### Post by oldfred on 2017-10-15
You have to partition  it and then format it.

You said testing ISO. Did you use one of the tools that uses DD to image the hybrid DVD/flash drive ISO to drive?
That is then not a standard partitioned drive. You often have to clear the MBR as it has what looks like misc data in the normal part of the drive where partition data is. So it cannot translate random data into correct partitions.

While you can use dd to clear first sector or two, this is safer.
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

If just a data drive and external, I also suggest gpt whether your hardware is UEFI or BIOS based. In future you will be UEFI, so best to start converting to gpt now. I started in 2010 with first gpt drive to boot Ubuntu.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by RobGoss on 2017-10-15
> You said testing ISO. Did you use one of the tools that uses DD to image the hybrid DVD/flash drive ISO to drive?

Hi Oldfred, I just connected the external drive, booted up the live **USB** and chose that external drive to install Ubuntu

---

### Post by oldfred on 2017-10-15
That should have been just a standard install. But grub would have installed to drive seen as sda, if you did not use Something Else.
Anytime you have multiple drives best to partition in advance and use Something Else so you can choose which drive gets grub2 boot loader. Except with UEFI it wants to only install to ESP on sda.

Post this:
sudo parted -l

---

### Post by sudodus on 2017-10-15
> **westie457 said:**
> Hi, have you checked the 'smart' data yet?
Another tool to use is testdisk for problems that do not show in a smart report. 
Testdisk will stop with a message about major errors. 

Atm I have no access to Ubuntu so help will be limited.

An easy way to see the S.M.A.R.T. data is to do it via Disks alias gnome-disks.

[Reformating hard drive after malware damaged boot sector](https://askubuntu.com/questions/948036/reformating-hard-drive-after-malware-damaged-boot-sector/948560#948560)

Look at the section 'Maybe the disk hardware is damaged' at the end of the answer.

---

### Post by RobGoss on 2017-10-15
Here you go Fred, Thanks so much

sudo parted -l


```
Model: ATA WDC WD5000AAKX-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368GB  368GB   primary   ext4            boot
 2      368GB   500GB  132GB   extended
 6      368GB   496GB  128GB   logical   ext4
 5      496GB   500GB  4183MB  logical   linux-swap(v1)


Error: /dev/sdb: unrecognised disk label
Model: WD 3200AAK External (scsi)                                         
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
```

---

### Post by sudodus on 2017-10-15
When you are posting output of command lines, please post also the output of

```
sudo lsblk -f
```

and

```
sudo lsblk -m
```

These commands will sometimes add information, when parted has problems.

---

### Post by RobGoss on 2017-10-15
Thanks Sudodus


$ sudo lsblk -f

```
 $ sudo lsblk -f
NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
loop1  squashf                                            /snap/simplescreenreco
sdb                                                       
&#9500;&#9472;sdb2                                                    
&#9500;&#9472;sdb5                                                    
&#9492;&#9472;sdb1                                                    
loop8  squashf                                            /snap/core/3017
loop6  squashf                                            /snap/keepassxc/24
loop4  squashf                                            /snap/keepassxc/23
sr0                                                       
loop2  squashf                                            /snap/vlc/4
loop0  squashf                                            /snap/keepassxc/25
sda                                                       
&#9500;&#9472;sda5 swap          00f824c8-9860-421e-933f-7f3cbbc02cad [SWAP]
&#9500;&#9472;sda1 ext4          e84a03d8-c592-44b3-a365-26cf13e1f35c /
&#9492;&#9472;sda6 ext4          b9a7b565-5da9-4158-bb49-0f18531e1754 
loop7  squashf                                            /snap/anbox-installer/
loop5  squashf                                            /snap/core/2898
loop3  squashf 
``` 

 $ sudo lsblk -m

```
sudo lsblk -m
NAME     SIZE OWNER GROUP MODE
loop1     85M root  disk  brw-rw----
sdb    298.1G root  disk  brw-rw----
&#9500;&#9472;sdb2     1K root  disk  brw-rw----
&#9500;&#9472;sdb5     2G root  disk  brw-rw----
&#9492;&#9472;sdb1 296.2G root  disk  brw-rw----
loop8     83M root  disk  brw-rw----
loop6   76.4M root  disk  brw-rw----
loop4     76M root  disk  brw-rw----
sr0     1024M root  cdrom brw-rw----
loop2    115M root  disk  brw-rw----
loop0   76.4M root  disk  brw-rw----
sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda5   3.9G root  disk  brw-rw----
&#9500;&#9472;sda1 342.7G root  disk  brw-rw----
&#9492;&#9472;sda6 119.2G root  disk  brw-rw----
loop7      4K root  disk  brw-rw----
loop5   81.4M root  disk  brw-rw----
loop3   81.4M root  disk  brw-rw----
 
```

---

### Post by sudodus on 2017-10-15
There is some information about the partitions, but not much, only about size.

```

NAME     SIZE OWNER GROUP MODE
sdb    298.1G root  disk  brw-rw----
&#9500;&#9472;sdb2     1K root  disk  brw-rw----
&#9500;&#9472;sdb5     2G root  disk  brw-rw----
&#9492;&#9472;sdb1 296.2G root  disk  brw-rw----

```

I think something is wrong. Have you checked the S.M.A.R.T. information yet? The drive might be failing. If the S.M.A.R.T. information indicates that the drive is good, maybe you can try to format it in another computer.

The external box or adapter might also be failing or not cooperating with the hardware or software of your computer. You might try to connect it via another external box or directly to a SATA or PATA/IDE port, if you have one available in some computer.

---

### Post by RobGoss on 2017-10-15
When I try running S.M.A.R.T. data, it will go from 100% down to 10%, then it just sits there and does nothing

---

### Post by sudodus on 2017-10-16
It can take time (several minutes, sometimes maybe hours) to analyse the disk. But if it just sits there and does nothing, without finishing, then something is really wrong.

It seems to me that something is damaged:

- the hard disk drive,

- the external box or

- the port in the computer, where you connect the external box.

You can try to eliminate alternatives by testing different configurations.

---

### Post by RobGoss on 2017-10-16
I think you maybe right, the external drive is old and might be on its last leg. I have the same problem on almost every machine I hook it up to

Guess it's just time to put it to rest. Thanks guys for your efforts much appreciated 

Have a great day

---

