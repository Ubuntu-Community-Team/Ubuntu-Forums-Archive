---
title: "i need external hard drive help"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by prow on 2007-06-23
i have a maxtor one touch usb external hdd that will not mount on ubuntu.  The drive works fine on a windows machine and a can get a lacie external hdd to mount on ubuntu.

The only thing i could see going wrong is that the maxtor requires me to install the backup software/driver cd it came with to work on windows.  Does anyone know of anything that'll work to get my maxtor to mount?   

Please help me get my maxtor to work on ubuntu...i love that thing!

---

### Post by schallstrom on 2007-06-23
You should give the community some diagnostics to get a clue on what is going wrong. To start with, maybe you want to post the output of ```
$ lsusb
``` one time before you plug the maxtor drive in and one time after you do it.

---

### Post by prow on 2007-06-23
thank you for helping.....

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 043d:007b Lexmark International, Inc. 
Bus 001 Device 004: ID 043d:007c Lexmark International, Inc. 
Bus 001 Device 003: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  


AFTER....

Bus 004 Device 012: ID 067b:2507 Prolific Technology, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 043d:007b Lexmark International, Inc. 
Bus 001 Device 004: ID 043d:007c Lexmark International, Inc. 
Bus 001 Device 003: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by logos34 on 2007-06-23
Lexmark is your printer, ALcor might be a memory card reader, prolific?

what about this command:

**sudo lshw **

look under *usb section for anything resembling external hard disk (might say somehting like 'mass storage device' and/or have a driver like "usb_storage")

---

### Post by logos34 on 2007-06-23
try also unplugging/replugging, different ports, etc.  Is this a 2.5 or 3.5" drive? if the former, is it runningon bus-power or using ac adapter?

---

### Post by prow on 2007-06-23
*-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: USB Hub
                   vendor: Lexmark
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=8mA slots=2 speed=12.0MB/s
                 *-usb:0 UNCLAIMED
                      description: Generic USB device
                      product: X1100 Series
                      vendor: Lexmark
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 1.00
                      serial: 4105874
                      capabilities: usb-1.10
                      configuration: maxpower=0mA speed=12.0MB/s
                 *-usb:1
                      description: Printer
                      product: Lexmark X1100 Series
                      vendor: Lexmark
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 1.00
                      serial: 4105874
                      capabilities: usb-1.10 bidirectional
                      configuration: driver=usblp maxpower=4mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d000-d01f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d400-d41f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 1
                   bus info: usb@3:1
                   logical name: scsi3
                   version: 1.00
                   serial: 9205291
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB

im not sure what size the drive is but it runs on ac power not motherboard power.  Would the fact that it needs to have the driver disk installed on a windows machins installed before it'll work be the reason why.........my lacie external hdd does not require a driver disk to work and it mounts fine.

---

### Post by prow on 2007-06-23
i also get this...

[78856.151475] end_request: I/O error, dev sdb, sector 0
[78856.152723] end_request: I/O error, dev sdb, sector 0
[78856.153973] end_request: I/O error, dev sdb, sector 0
[78856.155227] end_request: I/O error, dev sdb, sector 0
[78856.156474] end_request: I/O error, dev sdb, sector 0
[78856.157721] end_request: I/O error, dev sdb, sector 0
[78856.158972] end_request: I/O error, dev sdb, sector 0
[78856.160221] end_request: I/O error, dev sdb, sector 0
[78856.161471] end_request: I/O error, dev sdb, sector 0
[78856.162720] end_request: I/O error, dev sdb, sector 0

and please note that this hdd does work on a windows machine and the linux machine will mount a different ex. hdd........so its not the fault of hardware.......i need to edit something or configure a file.....im a total newb at mounting external hdd's

---

### Post by schallstrom on 2007-06-24
If you post terminal output into the forums, please wrap it in code tags for a better readability.

It is possible that your drive does not have a generic interface and works only with binary drivers, which of corse are only available for Windows. If so, the drive sucks; try to give it back and tell the salesman it is defective by design. But let's sort things out first.

Could you double check if this entry
```
Bus 004 Device 012: ID 067b:2507 Prolific Technology, Inc. 
```
is only appearing in the 'lsusb' output if the drive is plugged in? If so, we know that the kernel is at least recognizing *something*.

Then you could run the 'lshw' with and without the drive plugged in and look for any differences, so we know certainly which entry is describing your drive.

Then you could try to mount the drive manually with commands similar to this:
```

$ sudo mkdir /media/usb
$ sudo mount /dev/sda /media/usb

```
Try the different devices which are most probably some of these: /dev/sda, /dev/sdb, /dev/sdc, /dev/sdd.

If you get an error involving something about file systems, try to run the mount command with explicit file system specification like this:
```

$ sudo mount -t vfat /dev/sda /media/usb

```
or
```

$ sudo mount -t ntfs /dev/sda /media/usb

```
depending on what file system the usb drive was formatted with.

---

### Post by prow on 2007-06-24
ok i'll try all of that......please dont go away....i need to get this to work

---

### Post by prow on 2007-06-24
here are the differences in the lshw commands

without the drive plugged in:

```
*-usb

                   description: Mass storage device

                   product: USB Reader

                   physical id: 1

                   bus info: usb@3:1

                   version: 1.00

                   serial: 9205291

                   capabilities: usb-1.10 scsi

                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s


```

with the drive plugged in:

```
 *-usb

                   description: Mass storage device

                   product: USB Reader

                   physical id: 1

                   bus info: usb@3:1

                   logical name: scsi3

                   version: 1.00

                   serial: 9205291

                   capabilities: usb-1.10 scsi emulated scsi-host

                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s

                 *-disk:0

                      description: SCSI Disk

                      product: USB SD Reader

                      vendor: Generic

                      physical id: 0.0.0

                      bus info: scsi@3:0.0.0

                      logical name: /dev/sdc

                      version: 1.00

                      capabilities: removable

                    *-disc

                         physical id: 0

                         logical name: /dev/sdc

                 *-disk:1

                      description: SCSI Disk

                      product: USB CF Reader

                      vendor: Generic

                      physical id: 0.0.1

                      bus info: scsi@3:0.0.1

                      logical name: /dev/sdd

                      version: 1.01

                      capabilities: removable

                    *-disc

                         physical id: 0

                         logical name: /dev/sdd

                 *-disk:2

                      description: SCSI Disk

                      product: USB SM Reader

                      vendor: Generic

                      physical id: 0.0.2

                      bus info: scsi@3:0.0.2

                      logical name: /dev/sde

                      version: 1.02

                      capabilities: removable

                    *-disc

                         physical id: 0

                         logical name: /dev/sde

                 *-disk:3

                      description: SCSI Disk

                      product: USB MS Reader

                      vendor: Generic

                      physical id: 0.0.3

                      bus info: scsi@3:0.0.3

                      logical name: /dev/sdf

                      version: 1.03

                      capabilities: removable

                    *-disc

                         physical id: 0

                         logical name: /dev/sdf



```

i also found this (which is the drive im looking for):

```
*-usb:3

             description: USB Controller

             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller

             vendor: Intel Corporation

             physical id: 1d.7

             bus info: pci@00:1d.7

             version: 02

             width: 32 bits

             clock: 33MHz

             capabilities: ehci bus_master cap_list

             configuration: driver=ehci_hcd latency=0

             resources: iomemory:ee080000-ee0803ff irq:23

           *-usbhost

                product: EHCI Host Controller

                vendor: Linux 2.6.20-16-generic ehci_hcd

                physical id: 1

                bus info: usb@4

                logical name: usb4

                version: 2.06

                capabilities: usb-2.00

                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s

              *-usb

                   description: Mass storage device

                   product: ATAPI-6 Bridge Controller

                   vendor: Prolific Technology Inc.

                   physical id: 6

                   bus info: usb@4:6

                   logical name: scsi15

                   version: 0.01

                   serial: 134100E4

                   capabilities: usb-2.00 scsi emulated scsi-host

                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s

                 *-disk

                      description: SCSI Disk

                      product: OneTouch III

                      vendor: Maxtor

                      physical id: 0.0.0

                      bus info: scsi@15:0.0.0

                      logical name: /dev/sdb

                      version: 0341

                      serial: L42GBVJG

                      size: 189GB

                      configuration: ansiversion=4

```

---

### Post by prow on 2007-06-24
```
prow@prow-desktop:~$ sudo mount -t ntfs /dev/sdb /media/usb
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

whats a superblock? missing codepage?

```
prow@prow-desktop:~$ sudo mount -t vfat /dev/sdb /media/usb
mount: /dev/sdb: can't read superblock

```

---

### Post by schallstrom on 2007-06-25
Try the following when the drive is plugged in:
```

$ sudo fdisk /dev/sdb

```
then you type just 'p' and enter and post all of the output here.

---

### Post by prow on 2007-06-25
ok i'll try that when i get home from work.....but what is a superblock? codepage?

---

### Post by schallstrom on 2007-06-25
To be honest, I don't really know what a superblock is exactly. I assume it's a block in the file system where some kind of meta information is stored.

A quick Google search for 'superblock' reveals more information (the 4th search result): [http://www.science.unitn.it/~fiorella/guidelinux/tlk/node97.html](http://www.science.unitn.it/~fiorella/guidelinux/tlk/node97.html)

---

### Post by prow on 2007-06-25
well...i guess that would mean that my maxtor is only able to be read with a windows machine with the driver installed that is able the read the superblock on the drive.  Somehow the file system manager on ext3 is getting blocked by a "lock" on the hard drive.  Damn maxtor!

Im starting to think im superscrewed....:(

---

### Post by prow on 2007-06-25
one other thing before i run fdisk.  will it erase anything on the drive?  Because i have important data on it that cannot be lost!

should i backup my data onto another drive first?

---

### Post by schallstrom on 2007-06-25
Don't jump to conclusions about the superblock thing. The error message you posted is a pretty common one of the mount command. It's just saying that it can't locate the superblock, but it can have a thousand reasons *why* it can't find it.

If you just run fdisk, you won't write anything on your hard disk, so no data will be destroyed. In the fdisk command line, typing 'p' just prints out the current partition table. And as long as you don't type 'w' followed by Enter, nothing will ever be written to the disk. But if you are still feeling uncomfortable running fdisk it's certainly not a mistake to make a backup of your important files.

---

### Post by prow on 2007-06-25
```
prow@prow-desktop:~$ sudo fdisk /dev/sdb 

Unable to read /dev/sdb

```

when i run the code the lights on the front of the drive light up and act like its doing something but then it just says "unable to read /dev/sdb"

---

### Post by schallstrom on 2007-06-25
Are you sure that the drive was connected when you ran the command? If so, I fear that I'm at my wits end. Maybe the drive really only works with binary drivers. Sorry that I wasn't much help to you in the end :(

---

### Post by pingpongboss on 2007-06-25
```
prow@prow-desktop:~$ sudo mount -t ntfs /dev/sdb /media/usb
```

i'm pretty sure you have to type /dev/sdb1 or /dev/sdb2 for the mount command. try it. i could be wrong.

---

### Post by schallstrom on 2007-06-25
> **pingpongboss said:**
> ```
prow@prow-desktop:~$ sudo mount -t ntfs /dev/sdb /media/usb
```

i'm pretty sure you have to type /dev/sdb1 or /dev/sdb2 for the mount command. try it. i could be wrong.

That depends. It is possible to write a file system directly to the drive without any partitioning. But generally you are right. Still I don't see much chances that this will work when even fdisk can't read the disk...

---

### Post by prow on 2007-06-25
still nothing.....looks like this maxtor is junk (i.e. only good for windows :( )

---

### Post by schallstrom on 2007-06-25
> **prow said:**
> still nothing.....looks like this maxtor is junk (i.e. only good for windows :( )

Yes, looks pretty much like it to me. Do you know any folks in your neighborhood running some Linux system where you could plug the device and look if it's working on another machine? If not, you could try to locate any Linux User Group or something like this near your place and ask them to try your disk with their systems.

---

### Post by prow on 2007-06-25
well i have a test machine here that i could install ubuntu onto and maybe even fc 4 to see if it'll work with red hat......give me a few hours and i'll have it up and running

---

### Post by justtech on 2007-06-26
I'm not trying to thread jack here but I am having the same issues.  I have followed what you guys have done so far and this is what I am getting...

fdisk with p command gives me:
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         130     1044193+  82  Linux swap / Solaris
/dev/sda2           15936       36483   165051810    f  W95 Ext'd (LBA)
/dev/sda3             131       15935   126953662+  83  Linux
/dev/sda5           15936       36483   165051778+   7  HPFS/NTFS

Partition table entries are not in disk order

```

but this is what I get when I try and mount the drive...
```
justtech@JustTechnology:~$ sudo mount -t ntfs /dev/sda /media/maxtor
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

justtech@JustTechnology:~$ sudo mount -t vfat /dev/sda /media/maxtor
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

And Last but not least... the first command...
```
justtech@JustTechnology:~$ lsusb
Bus 005 Device 005: ID 0b05:170b ASUSTek Computer, Inc. 
Bus 005 Device 002: ID 0d49:7201 Maxtor 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 046d:c709 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c70a Logitech, Inc. 
Bus 002 Device 003: ID 046d:c70e Logitech, Inc. 
Bus 002 Device 002: ID 046d:0b02 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 001: ID 0000:0000  
```

I just wanted to post this and maybe this will help Prow or myself.  Any help would be appreciated.

---

### Post by schallstrom on 2007-06-27
> **justtech said:**
> I'm not trying to thread jack here but I am having the same issues.  I have followed what you guys have done so far and this is what I am getting...

fdisk with p command gives me:
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         130     1044193+  82  Linux swap / Solaris
/dev/sda2           15936       36483   165051810    f  W95 Ext'd (LBA)
/dev/sda3             131       15935   126953662+  83  Linux
/dev/sda5           15936       36483   165051778+   7  HPFS/NTFS

Partition table entries are not in disk order

```


Are you sure that /dev/sda is the drive you want to mount and not maybe your internal primary hard disk?
You can find out this by checking the 'lshw' output when the disk is plugged in.

If you are sure, you have to mount a particular partition with 'mount', not the whole disk, by specifying /dev/sdaN instead of /dev/sda.

For example:
```

$ sudo mount -t ntfs /dev/sda5 /media/maxtor

```

---

### Post by MaindotC on 2007-07-14
I'm monitoring this thread (I have the same situation) and I see it hasn't been touched lately. Anyone have any progress so far?

---

### Post by justtech on 2007-07-14
Personally, I gave up.  I ended up using my Vista laptop to connect to the Maxtor One Touch.  I believe that it has something to do with the software needed to unlock it.  I have seen that Maxtor (Seagate) offers open source drivers for it, just not exactly sure how to make that work in Ubuntu.  You can check that page out [here]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=GPL_Source_Code_page_content&vgnextoid=02d819e56cdee010VgnVCM100000dd04090aRCRD")

---

### Post by MaindotC on 2007-07-14
Well, I do have an XP partition. I've spent the last hour searching the Seagate website and googling for the actual software that came with the hard disk. Do you know where it is or have an .iso you can send me? I'm using the 160gb one-touch. Thanks for your prompt reply. I'm going to bed zZzZzZ...

---

### Post by darkeyes825 on 2007-09-21
I'm having a similar problem, but- my maxtor external (80 gig, portable, no external power) worked last night on my home computer using a Ubuntu Multimedia live cd, but won't read at work on a Ubuntu hard drive install (I think Feisty, not sure- I build pc's for a living, so I go through several every week..) I've added internal hard drives before by modifying fstab, couldn't it be done the same way? Been a while, though; and I'm in a hurry this morning, no time to research until tomorrow...
Any suggestions?

---

### Post by MaindotC on 2007-09-21
I'll try and replicate the problem.  I'm at school and when I go home today I gotta spend the time with chicky, but I come back on Sunday and I'll try to come up with a solution.  However I do have a math test on Monday and I gotta study so I can't guarantee how much time I can devote to it :(

---

### Post by mekas2024 on 2007-10-24
Hello guys, 

I have a problem with a USD to IDE External HDD, i try everything of what u mention in this thread, but nothing works, could someone help me please... 

My external hdd have a fat32 partition so I been trying a lot of things... 

mekas@mekas-laptop:~$ sudo mount -t vfat /dev/sdb /media/usb
mount: No medium found

---

mekas@mekas-laptop:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

-----

mekas@mekas-laptop:~$ sudo fdisk /dev/sdb 

Unable to open /dev/sdb

-----

Fdisk -l doesnt even recognize it :(

mekas@mekas-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21779f84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1406    11293663+   7  HPFS/NTFS
/dev/sda2            1407       24028   181703680    7  HPFS/NTFS
/dev/sda3           24029       24525     3992152+  82  Linux swap / Solaris
/dev/sda4           24526       30401    47198970   83  Linux

-----

I think this doesnt even recognize it :(

mekas@mekas-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  


WELL This is my sad story lol, so please if someone know how to solve it please i will apreciate if u let me know!

THX

Regards

---

### Post by zekopeko on 2007-10-24
are you using feisty fawn? if so know that i also had problems with my external 2.5" HDD.
i think that feisty has USB support broken for a number of devices because they changed something in the kernel in the last minute.
 i suggest that you upgrade to gutsy gibbon and then try.

BTW. if the HDD works in gutsy (99.9999999% that it will) you can format the drive to NTFS because gutsy has read/write by default for NTFS.

---

### Post by mekas2024 on 2007-10-24
HEY man, thanks for the fast reply, 
U know what.. i was reading, i didnt found the answer so i went to my vista partition use the HDD to read it in ubuntu from the vista partiton lol so when i restart the computer ubuntu recognize it... i dont know why but lol i have my External HDD  working :D

Thanks anyway !

By the way, im usuin gusty !

Regards!

---

### Post by prow on 2007-10-24
if you have a maxtor one touch external hdd you can not use it on linux

why? you might ask....the software required to unlock the drive is windows only software
yay!...case closed....do not buy a maxtor one touch hdd!!!

---

### Post by arunsub on 2007-11-29
> **prow said:**
> if you have a maxtor one touch external hdd you can not use it on linux

why? you might ask....the software required to unlock the drive is windows only software
yay!...case closed....do not buy a maxtor one touch hdd!!!

I bought Maxtor Onetouch 4 EHD last week. Ubuntu Gutsy recognizes it, but I can't access the folder. Do you think formatting the hard drive will unlock the drive?

---

### Post by amubu on 2007-12-23
..too
i filled with music and videos my hard disk and now i cannot see them in my computer :guitar:
my pc is ubuntu 7.10 
what could i do now??

---

### Post by arunsub on 2007-12-24
I tried formatting it with QTParted and GParted, but QTParted didn't recognize the drive and  the option to select format was disabled in GParted. I couldn't format the drive too, I then booted my system into Windows and used Partition Magic to format the drive. I partitioned it in NTFS and I'm backing up my files now. 

Amubu, Since you already have data in the disk, use Windows to extract the data and then format it using some Windows partition editor.

---

### Post by amubu on 2008-01-03
thanks arunsub! so do partitions must have a maximum size? i think yes 
and what about filesystem? fat32 its ok for all uses ..?

---

### Post by arunsub on 2008-01-03
NTFS is better. FAT32 has it's own limitation esp for big files. I formatted it with NTFS and didn't have any problem writing (except some access error if i use user switching feature in Gutsy couple of times). You should install ntfs-3g and ntfs configuration program from synaptic.

---

