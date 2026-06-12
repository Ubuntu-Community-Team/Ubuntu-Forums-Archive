---
title: "Mounting Sata in fstab"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by snagaslas on 2005-04-22
I can´t seem to mount SATA partitons at fstab, is it cause ubuntu hasn´t configured partitiontable for SATA drivers until later on bootup?

I also mount 2 other partions on a IDE harddrive and it works good just not the SATA one.

(Not sure where to post this assume it´s here)

Ty prehand!

---

### Post by heimo on 2005-04-22
Do you get any error messages? Are the devices present in /dev directory? I've two SATA disks on one of my computers and they work fine with standard Hoary kernel (2.6.10 -386 and -686). Is the hard disk recognized during boot? Try running
```
dmesg | less
```
just after boot and search relevant information.
 
Check the partitions using
```

fdisk -l /dev/sda

```
or what ever the device name is.
 
What motherboard/chipset is it? Also would be helpful to see output of lspci.

---

### Post by snagaslas on 2005-04-22
I can mount it while i in linux and it is showing with fdisk -l /dev/sda as following:

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11473    92156841    7  HPFS/NTFS
/dev/sda2           11474       24321   103201560    f  W95 Ext'd (LBA)
/dev/sda5           11474       24321   103201528+   7  HPFS/NTFS
```


It&#347; just like it hasnt configured SATA when I run fstab. It works perfectly at bootup so thats not the problem.



And here is lspci:


```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:04.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:01:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:01:0a.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:03:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
```



As you can see the SATA is there on third row from bottom.

---

### Post by heimo on 2005-04-22
With what command do you try to mount those partitions? Do you define filesystem, or are those listed in /etc/fstab? What's the type there? auto, ntfs or something else?
 
Do you get any errors in /var/log/messages when you try to mount?

---

### Post by snagaslas on 2005-04-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5	/mnt/downloads  ntfs	umask=0222	0	0
/dev/hda3	/mnt/movies	ntfs	umask=0222	0	0
/dev/hda5	/mnt/mp3	ntfs	umask=0222	0	0
```


That is my fstab file.

I can mount while inside the system but not automount on boot. can it have something to do with the type/options?

---

### Post by heimo on 2005-04-24
It could be. I thought the default is to mount automaticly, but you could put *auto *in the options. During boot *mount -a *is run automaticly. If *mount -a *from command line doesn't mount your partitions, probably it won't happen during boot either. So you can test the settings in fstab and do *mount -a*

Hmm... actually. I think it's  /etc/init.d/mountall.sh that does it:
  ```
#
# Mount local file systems in /etc/fstab.
#
log_begin_msg "Mounting local filesystems..."
mount -av -t nonfs,nonfs4,nosmbfs,nocifs,noncp,noncpfs,nocoda 2>&1 |
		egrep -v '(already|nothing was) mounted'


``` 

Now that nocifs looks a bit familiar... Isn't ntfs cifs? I'd try to run that mount command with those exact parameters, then without that nocifs and see what happens.

Also see this (don't mind about the Warty, fstabs file has been quite stable over years):
[http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions]("http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions")

Disclaimer: I'm almost falling asleep.

---

### Post by alastair on 2005-04-24
No - CIFS is the "modern" terminology for SMB filesystems i.e.. SMBFS etc.

I think we need to see some boot logs i.e.

/var/log/syslog

and have a look at what messages are reported for filesystems being mounted.

---

### Post by heimo on 2005-04-25
alastair's correct. And I totaly missed (on my second post) that the failing mount was SATA and if I understood correctly, you've two ntfs partitions on PATA that are mounted during boot. So my guesses were off.

Anything in logs? *dmesg | less *after boot, search what's happening when disks are detected and partitions mounted. Maybe it's because sata module gets loaded too late.

---

### Post by snagaslas on 2005-04-25
Ok. the /var/log/syslog only contains following:
```

Apr 25 09:10:45 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 25 09:10:45 localhost anacron[8005]: Job `cron.daily' terminated
Apr 25 09:10:45 localhost anacron[8005]: Normal exit (1 job run)
Apr 25 09:15:42 localhost kernel: NTFS volume version 3.1.
```

That last line is after i did mount -a wich worked fine:

```

snaga@Castle:~/$ sudo mount -a
Password:
snaga@Castle:~/$ 
```

So it perhaps is as you say Heimo, SATA modules get loaded to late for fstab. I thought so but Im not sure how to check it.

Here is everything in dmesg | less, not everything just what i think is important was so much text so I took out everything containing SATA.:

```

ata1: SATA max UDMA/100 cmd 0xF8BA8080 ctl 0xF8BA808A bmdma 0xF8BA8000 irq 18
ata2: SATA max UDMA/100 cmd 0xF8BA80C0 ctl 0xF8BA80CA bmdma 0xF8BA8008 irq 18
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000617577]
NET: Registered protocol family 17
ata1: dev 0 cfg 49:2f00 82:346b 83:7f21 84:4003 85:3469 86:3c01 87:4003 88:203f
ata1: dev 0 ATA, max UDMA/100, 390721968 sectors: lba48
ata1(0): applying bridge limits
ata1: dev 0 configured for UDMA/100
scsi0 : sata_sil
ata2: no device found (phy stat 00000000)
scsi1 : sata_sil
  Vendor: ATA       Model: WDC WD2000JD-00G  Rev: 02.0
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
eth1: network connection up using port A
    speed:           10
    autonegotiation: yes
    duplex mode:     full
    flowctrl:        none
    irq moderation:  disabled
    scatter-gather:  enabled
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0315d40(lo)
IPv6 over IPv4 tunneling driver

```

---

### Post by heimo on 2005-04-26
Sorry for not posting in this thread for awhile.

See that Dr Gonzo suggested for a fix on this thread:
[http://www.ubuntuforums.org/showpost.php?p=136098&postcount=8](http://www.ubuntuforums.org/showpost.php?p=136098&postcount=8)

However, you're not using piix (Intel chipset ICH5/6) for you SATA contoller, so sata_sil may be better option. I'm not sure about that, but a module with that name exists and would be my guess.

What I'd do before making new initrd is install another kernel (for example -i386 and -686) so that I have an easy option to boot to another when I mess the other.  Maybe that initrd is not even required in your case - check what you have in /etc/modules and consider putting sata_sil (and those other modules DrG listed, except piix) there.

At your own risk. :-|

---

### Post by ekravche on 2005-08-28
Didn't work for me. I'm getting the following errors on bootup when mounting the drives attached to the EIDE raid controller.

                   mount: special device /dev/hdc1 does not exist
                   mount: special device /dev/hde1 does not exist

---

### Post by Vidar on 2005-09-07
Snaga: Had any luck mounting your SATA-drives at boot? I have both a sata and an usb2-drive that fail to mount at boot, but works fine if I mount them later on (after booting up).

Would be great if I could get them to mount at boot-time instead... :)

Btw, anyone know how to prevent the system from trying to load the OS from the USB-drive (Lacie 250gb) when booting? I've disabled every other boot option but hdd01 in my bios, still it tries to boot from the external drive if it's connected at boot.

---

