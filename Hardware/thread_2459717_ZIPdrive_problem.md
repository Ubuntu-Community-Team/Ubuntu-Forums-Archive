---
title: "ZIPdrive problem"
date: 2021-03-24
forum: Hardware
---

### Post by Dan Z on 2021-03-24
Hello all-I

 am trying to mount an old ZIPDRIVE model #Z100ATIPA, the drive , when a disk is inserted hums as it should

OS is Ubuntu 18.04

Using an IDE/SATA to USB adapter

>>>ide adapter is found

>>>>>lsusb
Bus 002 Device 009: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

Bus 001 Device 004: ID 152d:1561 JMicron Technology Corp. / JMicron USA Technology Corp. 

>>>But no drive is seen 

>>>jazipconfig
There are currently no entries in /etc/jazip.conf.

There are no Zip devices detected on the system.

There are no Jaz devices detected on the system.

Available commands:
 (c)reate an entry from scratch.
 (q)uit without saving.
 (e)xit and save changes.
                           ?

>>>I am a user of floppy

>>>sudo adduser danxxx floppy
[sudo] password for danxxx: 
The user `danxxx' is already a member of `floppy'.

 
>>>also no disks seen
>>>lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  55.4M  1 loop /snap/core18/1944
loop1    7:1    0  64.4M  1 loop /snap/gtk-common-themes/1513
loop2    7:2    0   276K  1 loop /snap/gnome-characters/570
loop3    7:3    0   548K  1 loop /snap/gnome-logs/103
loop4    7:4    0   219M  1 loop /snap/gnome-3-34-1804/66
loop5    7:5    0   276K  1 loop /snap/gnome-characters/550
loop6    7:6    0   956K  1 loop /snap/gnome-logs/100
loop7    7:7    0   2.5M  1 loop /snap/gnome-calculator/884
loop8    7:8    0   7.5M  1 loop /snap/gnome-easytag/11
loop9    7:9    0 140.7M  1 loop /snap/gnome-3-26-1604/98
loop10   7:10   0  55.5M  1 loop /snap/core18/1988
loop11   7:11   0 162.9M  1 loop /snap/gnome-3-28-1804/145
loop12   7:12   0  64.8M  1 loop /snap/gtk-common-themes/1514
loop13   7:13   0  97.7M  1 loop /snap/halo-weather/246
loop14   7:14   0  99.2M  1 loop /snap/core/10908
loop15   7:15   0   2.2M  1 loop /snap/gnome-system-monitor/157
loop16   7:16   0  95.8M  1 loop /snap/halo-weather/172
loop17   7:17   0 140.7M  1 loop /snap/gnome-3-26-1604/100
loop18   7:18   0 217.9M  1 loop /snap/gnome-3-34-1804/60
loop19   7:19   0 161.4M  1 loop /snap/gnome-3-28-1804/128
loop20   7:20   0   2.2M  1 loop /snap/gnome-system-monitor/148
loop21   7:21   0   2.5M  1 loop /snap/gnome-calculator/826
loop22   7:22   0  99.2M  1 loop /snap/core/10859
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 224.5G  0 part /
&#9492;&#9472;sda3   8:3    0   7.9G  0 part [SWAP]
sdb      8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0 242.2G  0 part /media/dandell/DanDell_UB_BU
&#9492;&#9472;sdb2   8:18   0 223.6G  0 part /media/dandell/timeshift
sr0     11:0    1  1024M  0 rom  


>>>>But---

>>>sudo lshw | less  (exert)(is this the ZIP DRIVE?)
  *-usb:5
                      description: Mass storage device
                      product: USB to ATA/ATAPI bridge
                      vendor: JMicron
                      physical id: 7
                      bus info: usb@2:1.7
                      version: 1.00
                      serial: 1A2203021002
                      capabilities: usb-2.00 scsi
                      configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s

 *-scsi
       physical id: 1
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage

Any help getting the drive mounted would be appreciated,

thanks dan

---

