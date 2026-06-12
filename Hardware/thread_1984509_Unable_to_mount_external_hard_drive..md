---
title: "Unable to mount external hard drive."
date: 2012-05-21
forum: Hardware
---

### Post by buckadilla on 2012-05-21
Hello everyone, I hope you are having a wonderful evening. I am trying to mount and access my Lacie 2big 4TB external hard drive and I keep getting this error:
[B]
Unable to mount Terra Firma[/B]

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I've been searching the net for a couple of hours and I haven't found anything that works for me. I'm pretty new to Ubuntu and any help is appreciated. Thanks!

---

### Post by oldfred on 2012-05-21
If you have not downloaded gdisk, download it.  If drive sdc post these commands.

sudo apt-get install gdisk

sudo parted /dev/sdc unit s print
or
sudo gdisk -l /dev/sdc

---

### Post by buckadilla on 2012-05-23
Cool. I'm not sure what 'drive sdc' means, but I installed gdisk, and here are the responses to the commands:


zane@zane-Studio-1737:~$ sudo parted /dev/sdc unit s print
Error: Could not stat device /dev/sdc - No such file or directory.        
Retry/Cancel?   

zane@zane-Studio-1737:~$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.8.1

Problem opening /dev/sdc for reading! Error is 2.
The specified file does not exist!



I also tried **sudo gdisk -l /dev/sdb3**, and here is the output:

zane@zane-Studio-1737:~$ sudo gdisk -l /dev/sdb3
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdb3: 3518828720 sectors, 1.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 983E03B7-C85F-4505-85CF-C0934598DC51
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3518828686
Partitions will be aligned on 2048-sector boundaries
Total free space is 3518828653 sectors (1.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

---

### Post by oldfred on 2012-05-23
**IF** drive sdc which is a drive, it could be sda, sdb etc

Partitions are the numbers after the drive or sda1, sda2  on sda,or  sdb5 first logical partition on sdb.  sda1 thry 4 are primary. If MBR then sda5 is first logical. IF gpt all partitions are primary.

> sudo gdisk -l /dev/sdb3
Creating new GPT entries.If you also said save you may have damaged an existing partition table.  The -l is supposed to be a list only. If unsure of any command always in terminal run 
man command
or
man gdisk
to see what parameters mean.

Lets try this:

```
sudo parted -l
```

And the response from gdisk seems to say you have a sdb and it has no partitions?? As it would report something, but instead seems to want to create a new partition table.

---

### Post by buckadilla on 2012-05-23
Here is the output from **sudo parted -l**

> zane@zane-Studio-1737:~$ sudo parted -l
[sudo] password for zane: 
Model: ATA WDC WD3200BEVT-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  317GB  317GB   primary   ext4            boot
 2      317GB   320GB  3177MB  extended
 5      317GB   320GB  3177MB  logical   linux-swap(v1)


Warning: The driver descriptor says the physical block size is 1024 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?

---

### Post by oldfred on 2012-05-23
That only shows sda a 320GB drive? I thought you had an external drive. 
Was it plugged in? 
Did you get any messages when you plugged it in?
Does BIOS show it?

What does this say?
```

lsusb
sudo lshw -class disk

```

---

### Post by buckadilla on 2012-05-23
The hard drive is plugged in to my eSaTa drive. The hard drive is plugged into AC power and I just used it with a Mac.

When I use the USB port, my original error message pops up. 

When I plug the hard drive into the computer with the eSaTa port, no message is displayed, but it is displayed on the navigation panel under **Devices**. When I try to mount it, I get my original error message.

Here are the outputs to the commands. This is with the eSaTa port.
> zane@zane-Studio-1737:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:63fa Microdia 
Bus 007 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical



>  zane@zane-Studio-1737:~$ sudo lshw -class disk
[sudo] password for zane: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD3200BEVT-7
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WXEY08TW0838
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000842ad
  *-cdrom
       description: DVD-RAM writer
       product: DVDRWBD BC-5600S
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 103B
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk:1
       description: ATA Disk
       product: eSATA-2 LaCie  2
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 0
       serial: MN5220F31BMTBK
       size: 3726GiB (4TB)
       configuration: ansiversion=5


---

### Post by oldfred on 2012-05-23
You say you used it with your Mac, I know nothing about Macs but have heard that only FAT formats work with Windows, Macs & Ubuntu.

 So how is drive formated and partitioned under the Mac?

---

