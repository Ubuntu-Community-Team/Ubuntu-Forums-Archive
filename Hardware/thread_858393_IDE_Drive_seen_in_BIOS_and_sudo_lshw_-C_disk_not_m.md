---
title: "IDE Drive seen in BIOS and sudo lshw -C disk not mountable in Linux"
date: 2008-07-13
forum: Hardware
---

### Post by IanWood on 2008-07-13
Hi,

I am using 8.04.

I have a main IDE hard disk 160GB big.

I have an old 40GB hard disk. This morning I created a full ext3 partition destroying and old Windoze partition.

I was moving a large (15GB) directory from the big disk to the old disk and then canceled it as I changed my mind. After that the computer became very sluggish and occasionally unresponsive. I then decided to reboot it. After the reboot the machine booted into Busybox mode saying that the disk had problems. 

I moved the disk into another Hardy machine I have to see if I had any more joy there. I didn't.

The drive shows up in BIOS. I some looking around and found these commands

```
sudo fdisk -l
```
Which returns:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05e0e356

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3581       19457   127532002+   7  HPFS/NTFS
/dev/sda2               1         131     1052226   82  Linux swap / Solaris
/dev/sda3             132         784     5245222+  83  Linux
/dev/sda4             785        3580    22458870   83  Linux

Partition table entries are not in disk order
```

As you can see only the 160GB disk shows up


```
sudo lshw -C disk
```
It returns this.
```
  *-disk:0                
       description: ATA Disk
       product: ST3160023A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda
       version: 8.01
       serial: 3JS3W4E6
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=05e0e356
  *-disk:1 UNCLAIMED
       description: ATA Disk
       product: IC35L040AVER07-0
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       version: ER4O
       serial: SXPTXHD0184
       configuration: ansiversion=5
```

I also ran this:
```
cat /proc/partitions
```
Which returns this:
```
major minor  #blocks  name

   8     0  156290904 sda
   8     1  127532002 sda1
   8     2    1052226 sda2
   8     3    5245222 sda3
   8     4   22458870 sda4
   8    16   40209120 sdb
   8    17   40202631 sdb1
```

In Nautilus the drive appears as SCSI Drive but when I double click it it says "Unable to mount location", "Can't mount file".

The drive had nothing on so I am happy to create a new FS on it. 

How do I fix this?

Thanks in advance,

Ian

---

### Post by tech0007 on 2008-07-13
Try reinstalling grub

Boot your computer up with Ubuntu CD 
Open a terminal window or switch to a tty. 
Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary. 

Type "grub" 
Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". Use whatever your computer spits out for the following lines. 
Type "root (hd1,0)", or whatever your harddisk + boot partition numbers are for Ubuntu. 
Type "setup (hd1,0)", ot whatever your harddisk nr is. 
Quit grub by typing "quit". 
Reboot and remove the bootable CD.

---

### Post by IanWood on 2008-07-13
Thanks for the quick response.

Isn't GRUB just for the machine to decide the boot device?

I am a little worried about changing my GRUB as I am pretty certain there is a problem with this drive and don't want to make things worse. 

I have put this disk in two machines, and neither machine can see it in Linux but both can in the BIOS.

Is there not a cmd to blow away a file system on a disk and create a new one?

I have also looked in the log messages ```
 dmesg | grep sdb 
```
 and seen this - there is quite a bit but I see the word error once or twice...
```

[   46.845613] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[   46.845635] sd 3:0:0:0: [sdb] Write Protect is off
[   46.845639] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   46.845668] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.845740] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[   46.845756] sd 3:0:0:0: [sdb] Write Protect is off
[   46.845760] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   46.845786] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.845792]  sdb: sdb1
[   46.856598] sd 3:0:0:0: [sdb] Attached SCSI disk
[   74.356106] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   74.356113] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[   74.356138] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[   74.356147] end_request: I/O error, dev sdb, sector 71
[   74.356153] Buffer I/O error on device sdb, logical block 8
[   74.356157] Buffer I/O error on device sdb, logical block 9
[   74.356162] Buffer I/O error on device sdb, logical block 10
[   74.356166] Buffer I/O error on device sdb, logical block 11
[   74.367541] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[   74.374275] sd 3:0:0:0: [sdb] Write Protect is off
[   74.374282] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   74.377480] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   74.403348] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  101.850836] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  101.850842] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  101.850867] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  101.850875] end_request: I/O error, dev sdb, sector 71
[  101.850881] Buffer I/O error on device sdb, logical block 8
[  101.851093] sd 3:0:0:0: [sdb] Write Protect is off
[  101.851098] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  129.237657] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  129.237662] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  129.237685] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  129.237692] end_request: I/O error, dev sdb, sector 71
[  129.237696] Buffer I/O error on device sdb, logical block 8
[  129.237742] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  129.237774] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  129.237791] sd 3:0:0:0: [sdb] Write Protect is off
[  129.237795] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  129.237822] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  156.800358] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  156.800363] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  156.800386] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  156.800393] end_request: I/O error, dev sdb, sector 71
[  156.800397] Buffer I/O error on device sdb, logical block 8
[  156.800437] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  156.800455] sd 3:0:0:0: [sdb] Write Protect is off
[  156.800459] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  156.800486] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  156.800515] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  156.800531] sd 3:0:0:0: [sdb] Write Protect is off
[  156.800535] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  156.800562] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  184.151200] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  184.151206] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  184.151229] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  184.151235] end_request: I/O error, dev sdb, sector 71
[  184.151239] Buffer I/O error on device sdb, logical block 8
[  184.151280] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  184.151297] sd 3:0:0:0: [sdb] Write Protect is off
[  184.151301] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  184.151328] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  184.151356] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  184.151372] sd 3:0:0:0: [sdb] Write Protect is off
[  184.151376] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  184.151402] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  211.538028] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  211.538033] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  211.538057] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  211.538064] end_request: I/O error, dev sdb, sector 71
[  211.538068] Buffer I/O error on device sdb, logical block 8
[  211.538109] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  211.538126] sd 3:0:0:0: [sdb] Write Protect is off
[  211.538131] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  211.538158] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  211.538186] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  211.538203] sd 3:0:0:0: [sdb] Write Protect is off
[  211.538206] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  211.538233] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  238.908888] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  238.908895] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  238.908920] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  238.908929] end_request: I/O error, dev sdb, sector 71
[  238.908934] Buffer I/O error on device sdb, logical block 8
[  266.387765] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  266.387771] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  266.387797] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  266.387806] end_request: I/O error, dev sdb, sector 71
[  266.387812] Buffer I/O error on device sdb, logical block 8
[  266.388061] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  293.730588] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  293.730595] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  293.730621] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  293.730629] end_request: I/O error, dev sdb, sector 71
[  293.730636] Buffer I/O error on device sdb1, logical block 4
[  293.730642] Buffer I/O error on device sdb1, logical block 5
[  293.730647] Buffer I/O error on device sdb1, logical block 6
[  293.730652] Buffer I/O error on device sdb1, logical block 7
[  293.730657] Buffer I/O error on device sdb1, logical block 8
[  293.730662] Buffer I/O error on device sdb1, logical block 9
[  293.730667] Buffer I/O error on device sdb1, logical block 10
[  293.730672] Buffer I/O error on device sdb1, logical block 11
[  293.730677] Buffer I/O error on device sdb1, logical block 12
[  293.730682] Buffer I/O error on device sdb1, logical block 13
[  293.733549] sd 3:0:0:0: [sdb] Write Protect is off
[  293.733556] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  293.800386] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  293.800976] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  293.800999] sd 3:0:0:0: [sdb] Write Protect is off
[  293.801003] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  293.801033] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  321.261279] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  321.261285] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  321.261312] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  321.261321] end_request: I/O error, dev sdb, sector 71
[  321.261331] Buffer I/O error on device sdb1, logical block 4
[  321.261341] Buffer I/O error on device sdb1, logical block 5
[  321.261346] Buffer I/O error on device sdb1, logical block 6
[  321.261351] Buffer I/O error on device sdb1, logical block 7
[  348.616069] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  348.616075] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  348.616101] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  348.616110] end_request: I/O error, dev sdb, sector 71
[  348.616116] Buffer I/O error on device sdb, logical block 8
[  348.616386] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  376.010951] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  376.010958] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  376.010983] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  376.010991] end_request: I/O error, dev sdb, sector 71
[  376.010998] Buffer I/O error on device sdb, logical block 8
[  376.012757] sd 3:0:0:0: [sdb] Write Protect is off
[  376.012764] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  376.027704] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  376.028244] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  376.028267] sd 3:0:0:0: [sdb] Write Protect is off
[  376.028271] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  376.028299] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  403.497706] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  403.497713] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  403.497739] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  403.497748] end_request: I/O error, dev sdb, sector 71
[  403.497755] Buffer I/O error on device sdb1, logical block 4
[  430.884475] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  430.884481] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  430.884507] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  430.884515] end_request: I/O error, dev sdb, sector 73
[  430.884522] Buffer I/O error on device sdb1, logical block 5
[  430.884530] Buffer I/O error on device sdb1, logical block 6
[  430.884535] Buffer I/O error on device sdb1, logical block 7
[  430.884771] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  458.187368] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  458.187375] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  458.187400] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  458.187409] end_request: I/O error, dev sdb, sector 71
[  458.187416] Buffer I/O error on device sdb, logical block 8
[  458.189500] sd 3:0:0:0: [sdb] Write Protect is off
[  458.189507] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  485.534517] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  485.534524] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  485.534550] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  485.534558] end_request: I/O error, dev sdb, sector 71
[  485.534566] Buffer I/O error on device sdb1, logical block 4
[  485.534573] Buffer I/O error on device sdb1, logical block 5
[  485.534578] Buffer I/O error on device sdb1, logical block 6
[  485.534582] Buffer I/O error on device sdb1, logical block 7
[  485.535320] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  485.535360] sd 3:0:0:0: [sdb] 80418240 512-byte hardware sectors (41174 MB)
[  485.535379] sd 3:0:0:0: [sdb] Write Protect is off
[  485.535383] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  485.535410] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

To me it looks like there is a problem with the disk. Is it a physical problem with the disk or a problem with the filesystem? I.e. if I can destroy the partition and add another ext3 partition will it work again, or or is the disk physically broken?

Thank again.

Ian

---

### Post by ajgreeny on 2008-07-13
With both disks connected to your computer, run the ubuntu live CD and go to Partition Editor.  With that you should be able to delete the current partition(s) on sdb and then create a new one and format it to ext3.  Now hopefully when you boot, you will not get the problem with the busybox error.

If you don't want to try that you could always see if you can fsck on the unmounted partitions on it, also using the live CD, which should be ```
sudo fsck /dev/sdb*
``` for each of the partitions seen on sdb.

I hope that does the trick.

---

### Post by IanWood on 2008-07-15
Hi ajgreeny,

I did what you said with the Live CD and this time it could see the drive in GParted - however I wasn't able to format if to ext3

I got this message

```
GParted 0.3.5

Libparted 1.7.1

Create Primary Partition #1 (ext3, 38.34 GiB) on /dev/sda  22:37    ( ERROR )
     	
create empty partition  16:02    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 80405324
size: 80405262 (38.34 GiB)
set partitiontype on /dev/sda1  06:35    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/sda1
     	
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

========================================
```

What could have caused this to happen? The drive is old, circa late 2001 and was used for several years, but not the last two, is it just too old?

Is there anything else to try or is it now a bin job? Considering how much disks cost these days I may just buy one for less than filling my van with diesel...

Cheers

Ian

---

### Post by ajgreeny on 2008-07-15
Was the disk definitely unmounted when you tried to work on it?  Could you right click on the partitions already on it and delete them one by one?  I presume you used gparted in terminal from the error messages you got, but I presume you were seeing the GUI as well, is that right?  This seems a bit strange unless the disk is broken and unusable for some reason.

---

### Post by IanWood on 2008-07-16
Hi ajgreeny,

Thanks again for your response. 

The drive was defo unmounted - and I was only using the GParted GUI.

The error message I posted above was copied from the html report GParted created. 

I think the drive is a bin job and I am worried that something I did or Ubunto did broke the disk. Is that possible?

Cheers

Ian

---

### Post by ajgreeny on 2008-07-16
Seems unlikely, but before you bin it try running [**Dukes boot and nuke**]("http://dban.sourceforge.net/") on it and then try gparted again.

---

### Post by liljoentx on 2009-01-30
> **IanWood said:**
> 

sudo lshw -C disk
It returns this.
*-disk:0                
       description: ATA Disk
       product: ST3160023A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda


Gentlemen,

I'm having a similar problem but I don't believe Mr. Greeny's reply is quite accurate. It appears from your sudo query that the disk is being recognized as a SCSI drive, just like mine.

It clearly shows it to be an ST3160023A, which is an IDE drive and should appear under bus info as ide not scsi and the logical name should be hda not sda! Mine is an ST380215A, which is an 80 Gig IDE drive and alsoo shows the same SCSI indications.

I don't know why or if that is as it should be, but I'm almost certain that is why Gparted doesn't work right and why the CD will not install Ubuntu to that drive.

Any takers on resolving this issue?

Lil'Joe

---

