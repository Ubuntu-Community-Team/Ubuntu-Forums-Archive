---
title: "External hard drive not detected after upgrade to fiesty"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by YellowSnot on 2007-05-05
I will try to give as much information as possible here, just let me know if you need anything else.

A couple days ago I installed Ubuntu Edgy on my old dell inspiron 8200 laptop. The laptop has an internal 6 GB drive, and I also have a 80 GB external hard drive. After the initial installation my external hard drive was detected and displayed just fine. I then upgraded to fiesty using the update manager. Feisty however will not detect my external hard drive.

The hard drive is connected via firewire, and is a 80 GB seagate drive. It is formatted as one large ntfs partition.

fdisk -l gives this:

Disk /dev/sda: 6007 MB, 6007357440 bytes
255 heads, 63 sectors/track, 730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         696     5590588+  83  Linux
/dev/sda2             697         730      273105    5  Extended
/dev/sda5             697         730      273073+  82  Linux swap / Solaris

so it does not appear to detect the drive at all.

A google search suggested unplugging the drive and plugging it back in until it detects it. I have done this several times to no avail. Any help will be greatly appreciated.

---

### Post by Rizado on 2007-05-05
Had problems with a external drive and a powermac a few days ago. It was not detected because the right modules were never loaded.

Try running  ```
sudo modprobe libata sbp2
```That did it for me. If it works add thoose modules to /etc/modules. Also check dmesg before and after plugging the drive in.

---

### Post by techbiker on 2007-05-05
I have the same problem with external Seagate 400 GB USB drive.
Was detected and ran perfectly under Edgy but after upgrade
to Feisty it is not auto mounted.
It is detected with    *fdisk -l*:

[COLOR="Blue"]Disk /dev/sdj: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1       48641   390708801    c  W95 FAT32 (LBA)[/COLOR]

but I don't know how to get to it.

How do I access the drive at least through the shell
or how can I mount it manually?

---

### Post by Rizado on 2007-05-06
> **techbiker said:**
> I have the same problem with external Seagate 400 GB USB drive.
Was detected and ran perfectly under Edgy but after upgrade
to Feisty it is not auto mounted.
It is detected with    *fdisk -l*:

[COLOR="Blue"]Disk /dev/sdj: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1       48641   390708801    c  W95 FAT32 (LBA)[/COLOR]

but I don't know how to get to it.

How do I access the drive at least through the shell
or how can I mount it manually?sudo mount -t vfat /dev/sdj1 /path/where/you/want/it/must/exist

Then you probalby want to edit your fstab. Try to make a label on sdj1 by following [_this_](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/) guide. Then add ```
LABEL=DISKLABEL /path/where/you/want/it/must/exist vfat rw,user,noauto 0 0
```to your fstab.

Also read: [http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

Doing this that drive will always be mounted in the same place regardless how many other drives you have. It might not fix the automount problem though.

---

### Post by techbiker on 2007-05-12
It works great.
Thanks
It even works for my memory card reader.

---

### Post by estel2000 on 2007-06-02
to automount the drive at startup, change

```
/path/where/you/want/it/must/exist vfat rw,user,**noauto** 0 0
```
to
```
/path/where/you/want/it/must/exist vfat rw,user,**auto** 0 0
```

---

### Post by StickyCube on 2007-08-29
This thread is from awhile ago, but I'm having the same problem now, so I'm going to resurrect this if possible.  I have a WD 320 GB in a Nexstar 3 enclosure, connected through eSATA, but my fdisk -l only give my three partitions of the internal disk.  No file that I can find in /dev/ that matches hd* or sd* except the internal partitions and drive as well.  
I do notice, however, when unplugging the device:

```
[  872.317132] ata1: (irq_stat 0x00400000, PHY RDY changed)
[  873.547930] ata1: soft resetting port
[  873.547941] ata1: SATA link down (SStatus 0 SControl 300)
[  873.547949] ata1: EH complete

```
and on replugging,
```
[  921.324175] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x2 frozen
[  921.324180] ata1: (irq_stat 0x00000040, connection status changed)
[  921.867580] ata1: waiting for device to spin up (8 secs)
[  930.037957] ata1: soft resetting port
[  930.542338] ata1: softreset failed (1st FIS failed)
[  930.542346] ata1: softreset failed, retrying in 5 secs
[  935.541748] ata1: hard resetting port
[  936.494796] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  936.495741] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  937.511719] ata1: hard resetting port
[  938.391207] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  938.392993] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  938.392998] ata1.00: limiting speed to UDMA7:PIO5
[  939.412310] ata1: hard resetting port
[  940.291979] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  940.294409] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  941.308581] ata1: hard resetting port
[  942.188086] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  942.188099] ata1: EH complete

```

So any ideas on how to proceed would, as always, be wonderful.

---

