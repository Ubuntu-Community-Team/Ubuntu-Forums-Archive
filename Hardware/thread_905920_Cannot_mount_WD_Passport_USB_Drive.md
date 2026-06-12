---
title: "Cannot mount WD Passport USB Drive"
date: 2008-08-30
forum: Hardware
---

### Post by jbor7755 on 2008-08-30
I'm using both gnome and kde on Hardy x64.  I cannot mount my 320GB Western Digital Passport Drive.

Strangely I was able to mount it in the 32bit version of ubuntu.

When I plug it in to gnome I get the message:
"Invalid mount option when attempting to mount the volume 'My Passport'"

The drive is formatted Fat32 and I was able to take all of my music off Ubuntu 32bit before doing a clean install of the x64 version.  It mounts in WinXP fine.

Any ideas?

Cheers

---

### Post by jbor7755 on 2008-08-30
Also in Kubuntu the message when trying to open this drive is:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1
missing codepage or helper program

---

### Post by nicedude on 2008-08-30
Try using pysdm or learn the mount command.


Here is to install pysdm

sudo apt-get install pysdm

Here is to run it

sudo pysdm

Then select the drive on left part of gui and click mount.

Also I would recommend you look at the mount commands manual page

man mount

as if you learned how mount works you can do it for yourself but if you can't figure out etc then pysdm will 90% chance do it for you.

PS this behavior can happen again if you don't click remove or eject ( I use Windows so little these days I forget which it is ) in Windows or Unmount in Linux although I would say that more than likely you did not eject or remove drive in Windows and this is why it won't mount easily in Linux.

---

### Post by jbor7755 on 2008-08-31
I have never not "safely removed" a drive in windows. It turns out that this behaviour is not limited to my Passport drive.  I have 3 other flash drives which have all worked fine in Ubuntu 32bit 8.04.1 and which do not mount.  All with the same error message:

"Invalid mount option when attempting to mount the volume"

I can mount them manually but these things were supposed to be easily tranferable and portable they should mount automatically.  I shouldn't have to install another program just to handle USB drives.

The irony is that I installed Ubuntu x64 from a live USB after having no end of trouble trying to find a reliable CD.

Surely I cannot be the only one with this problem, this is a clean install of Hardy.

---

### Post by Rocket2DMn on 2008-08-31
Can you please post the output of the following commands with the drive plugged in?
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by jbor7755 on 2008-09-01
> **Rocket2DMn said:**
> Can you please post the output of the following commands with the drive plugged in?
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

result of sudo fdisk -l

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738       38913   266486220    5  Extended
/dev/sda5           38392       38913     4192965   82  Linux swap / Solaris
/dev/sda6           33293       38391    40957686   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

```

fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=4ad3a10f-8e61-458c-bf96-0a41dcc327a2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=25205de3-3084-46bb-aa57-aaf3c833e31f none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

sudo blkid

```

/dev/sda1: UUID="82845E70845E6727" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="25205de3-3084-46bb-aa57-aaf3c833e31f" 
/dev/sda6: UUID="4ad3a10f-8e61-458c-bf96-0a41dcc327a2" TYPE="ext3" 
/dev/sdb1: LABEL="My Passport" UUID="E0BF-6A5A" TYPE="vfat" 

```

mount

```

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jacob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jacob)

```

Found another thread on similar (same?) topic.  Same sort of info being passed around there also.
[HTML]http://ubuntuforums.org/showthread.php?t=821405&highlight=USB+flash+automount[/HTML]

thanks for offering help.

---

### Post by Rocket2DMn on 2008-09-01
OK, the problem is that you have an fstab entry for /dev/sdb1 which is set to be a cd/dvd drive.  Did you have a secondary cd/dvd drive that you removed?  We need to disable that entry in fstab, so open it for editing:
```
gksudo gedit /etc/fstab
```
and place a # in front of the /dev/sdb1 line
```
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Save and close.  Disconnect your camera, wait a moment, then plug it back in.  It should automount.

---

### Post by jbor7755 on 2008-09-01
<snipped response to deleted post>

Thanks Rocket2DMn for not being an arrogant bore and diagnosing the problem.

Commenting out that line in fstab was successful.  When I installed 8.04 I used a live USB made with the Unetbootin software.  I figured that would be easier than burning CDs (which I haven't had much luck with). Perhaps this live USB was mounted as a CD (and then all devices of this type were then assumed to be CDs by default)?

Thanks again for your help.

---

### Post by racecarpete on 2008-09-04
Hi I am having some problems along the same lines as what was going on here.

I have a Dell SX280 running Hardy 8.04. The system is equipped with a removable bay DVD rom drive. I've had problems with the DVD drive from the beginning. Apparently, it is pretty common with these drives but that is another issue altogether.

When I insert a thumb drive it will not mount.

I checked everything that Rocket2DMn suggested and sure enough the thumb drive is trying to mount on the same fstab entry for the dvd rom drive at /dev/sdb1. 

So I commented this out in fstab and the drive mounted and worked properly.

At this point I'm not sure what i am supposed to be adding to fix this. I need both deviced to work. I'm new to ubuntu but I'm learning quickly. 

To me it seems like I should make another entry and manually add the thumb drive to fstab. However, will I be restricted to only this thumb drive?

I took a look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and it was very informative but was not much help with my problem as the document said this: 

> Removable devices such as flash drives *can* be added to fstab, but are typically mounted by gnome-volume-manager and are beyond the scope of this document.

So can anyone assist in what I should be doing?

Thanks,
Peter

---

### Post by Rocket2DMn on 2008-09-04
Let's add your removable cd/dvd drive to fstab using UUID instead of a /dev location.  Please plug in the removable bay drive and post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by racecarpete on 2008-09-04
Thanks for replying. Here is the output.

output of sudo fdisk -l:

```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x140407ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        1399      996030   82  Linux swap / Solaris
/dev/sda3            1400        4863    27824580   83  Linux

```

Output of cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8bbb7fca-ec2b-403d-b24a-7e8e5a26fa2a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=b0e3d372-1e4f-4c71-83df-ef3b20733eac none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Output of sudo blkid:

```
/dev/sda1: UUID="ECA434CFA4349E50" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="b0e3d372-1e4f-4c71-83df-ef3b20733eac" 
/dev/sda3: UUID="8bbb7fca-ec2b-403d-b24a-7e8e5a26fa2a" TYPE="ext3" 

```

Output of mount:

```
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)
/dev/scd0 on /media/Ubuntu 8.04.1 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)

```

-Peter

---

### Post by Rocket2DMn on 2008-09-04
Assuming you have the removable drive plugged in, it should be OK.  It is not appearing from the fdisk command.  However, your sdb entry in fstab is not commented out, so please open it for editing
```
gksudo gedit /etc/fstab
```
Then place a # in front of this line
```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
so that it looks like
```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Save and close.  Both your removable dvd drive and your thumb drive should be mounted automatically now with the entry disabled in fstab.

---

### Post by racecarpete on 2008-09-04
Hi,

When I leave it as is and do not edit. The DVD Drive works but the USB thumb drive will not mount.

If I do as you instructed and comment out:

```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

so that it looks like this:

```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The USB thumb drive mounts but the DVD drive does not work.

---

### Post by Rocket2DMn on 2008-09-04
OK, unplug both devices, please.  Now attach the dvd drive, open a terminal, and copy and paste here the output of
```
dmesg
```
I'm not entirely sure how we're going to pull this off.

---

### Post by racecarpete on 2008-09-05
Hi here is the output of dmesg:

```
[   18.952136] io scheduler noop registered
[   18.952139] io scheduler anticipatory registered
[   18.952140] io scheduler deadline registered
[   18.952153] io scheduler cfq registered (default)
[   18.952169] Boot video device is 0000:00:02.0
[   18.952356] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.952397] assign_interrupt_mode Found MSI capability
[   18.952431] Allocate Port Service[0000:00:01.0:pcie00]
[   18.952517] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.952559] assign_interrupt_mode Found MSI capability
[   18.952593] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.952638] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.952910] isapnp: Scanning for PnP cards...
[   19.303875] isapnp: No Plug & Play device found
[   19.338777] Real Time Clock Driver v1.12ac
[   19.339177] hpet_resources: 0xfed00000 is busy
[   19.339194] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.339330] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.340155] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.341036] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.341110] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.341277] PNP: No PS/2 controller found. Probing ports directly.
[   19.343829] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.343834] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.350833] mice: PS/2 mouse device common for all mice
[   19.350968] EISA: Probing bus 0 at eisa.0
[   19.350973] EISA: Cannot allocate resource for mainboard
[   19.350979] Cannot allocate resource for EISA slot 2
[   19.350999] EISA: Detected 0 cards.
[   19.351005] cpuidle: using governor ladder
[   19.351006] cpuidle: using governor menu
[   19.351089] NET: Registered protocol family 1
[   19.351116] Using IPI No-Shortcut mode
[   19.351150] registered taskstats version 1
[   19.351242]   Magic number: 8:740:330
[   19.351314]   hash matches device tty51
[   19.351339] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.351341] EDD information not available.
[   19.351620] Freeing unused kernel memory: 368k freed
[   20.556297] fuse init (API version 7.9)
[   20.577285] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.033973] usbcore: registered new interface driver usbfs
[   21.034001] usbcore: registered new interface driver hub
[   21.041926] usbcore: registered new device driver usb
[   21.049912] tg3.c:v3.86 (November 9, 2007)
[   21.049936] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.049947] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.059020] USB Universal Host Controller Interface driver v3.0
[   21.070118] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:0f:1f:db:42:45
[   21.070126] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   21.070129] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   21.070157] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 17
[   21.070169] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.070172] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.070411] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.070442] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   21.070573] usb usb1: configuration #1 chosen from 1 choice
[   21.070599] hub 1-0:1.0: USB hub found
[   21.070606] hub 1-0:1.0: 2 ports detected
[   21.158781] SCSI subsystem initialized
[   21.173605] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 18
[   21.173620] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.173624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.173649] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.173679] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   21.173795] usb usb2: configuration #1 chosen from 1 choice
[   21.173820] hub 2-0:1.0: USB hub found
[   21.173827] hub 2-0:1.0: 2 ports detected
[   21.201185] libata version 3.00 loaded.
[   21.277317] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   21.277332] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.277336] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.277363] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   21.277392] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[   21.277507] usb usb3: configuration #1 chosen from 1 choice
[   21.277532] hub 3-0:1.0: USB hub found
[   21.277539] hub 3-0:1.0: 2 ports detected
[   21.381019] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 20
[   21.381034] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   21.381038] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.381065] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   21.381094] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000ff20
[   21.381211] usb usb4: configuration #1 chosen from 1 choice
[   21.381238] hub 4-0:1.0: USB hub found
[   21.381244] hub 4-0:1.0: 2 ports detected
[   21.412822] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   21.484790] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 17
[   21.484806] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.484810] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.484841] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   21.488726] ehci_hcd 0000:00:1d.7: debug port 1
[   21.488732] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   21.488739] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xffa80800
[   21.540458] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.540588] usb usb5: configuration #1 chosen from 1 choice
[   21.540615] hub 5-0:1.0: USB hub found
[   21.540623] hub 5-0:1.0: 8 ports detected
[   21.644377] ata_piix 0000:00:1f.1: version 2.12
[   21.644397] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.644435] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.645442] scsi0 : ata_piix
[   21.646056] scsi1 : ata_piix
[   21.648719] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   21.648722] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   21.648760] ata1: port disabled. ignoring.
[   21.648810] ata2: port disabled. ignoring.
[   21.648846] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   21.803694] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
[   21.803736] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.803784] scsi2 : ata_piix
[   21.803994] scsi3 : ata_piix
[   21.804028] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 21
[   21.804031] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 21
[   21.935288] usb 1-2: device not accepting address 2, error -71
[   21.967510] ata3.00: ATA-6: ST340014AS, 8.12, max UDMA/133
[   21.967514] ata3.00: 78125000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   21.983484] ata3.00: configured for UDMA/133
[   22.780861] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   22.808932] scsi 2:0:0:0: Direct-Access     ATA      ST340014AS       8.12 PQ: 0 ANSI: 5
[   22.822546] Driver 'sd' needs updating - please use bus_type methods
[   22.822637] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[   22.822652] sd 2:0:0:0: [sda] Write Protect is off
[   22.822655] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.822678] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.822730] sd 2:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[   22.822743] sd 2:0:0:0: [sda] Write Protect is off
[   22.822746] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.822767] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.822772]  sda: sda1 sda2 sda3
[   22.847119] sd 2:0:0:0: [sda] Attached SCSI disk
[   22.853304] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   22.952206] usb 1-2: configuration #1 chosen from 1 choice
[   23.191688] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   23.361571] usb 2-1: configuration #1 chosen from 1 choice
[   23.367490] hub 2-1:1.0: USB hub found
[   23.368461] hub 2-1:1.0: 3 ports detected
[   23.679564] usb 2-1.1: new low speed USB device using uhci_hcd and address 3
[   23.819253] usb 2-1.1: configuration #1 chosen from 1 choice
[   23.854081] usbcore: registered new interface driver hiddev
[   23.870733] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input1
[   23.881736] input,hidraw0: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1d.0-2
[   23.896157] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[   23.905664] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-1.1
[   23.940884] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.1/2-1.1:1.1/input/input3
[   23.949524] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-1.1
[   23.949542] usbcore: registered new interface driver usbhid
[   23.949546] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.043847] Attempting manual resume
[   24.043852] swsusp: Resume From Partition 8:2
[   24.043853] PM: Checking swsusp image.
[   24.044018] PM: Resume from disk failed.
[   24.058778] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.058783] EXT3-fs: write access will be enabled during recovery.
[   31.575466] kjournald starting.  Commit interval 5 seconds
[   31.575484] EXT3-fs: sda3: orphan cleanup on readonly fs
[   31.575490] ext3_orphan_cleanup: deleting unreferenced inode 1564707
[   31.575513] EXT3-fs: sda3: 1 orphan inode deleted
[   31.575515] EXT3-fs: recovery complete.
[   31.577051] EXT3-fs: mounted filesystem with ordered data mode.
[   39.137901] Linux agpgart interface v0.102
[   39.229676] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.289630] agpgart: Detected an Intel 915G Chipset.
[   39.289997] agpgart: Detected 7932K stolen memory.
[   39.305143] agpgart: AGP aperture is 256M @ 0xc0000000
[   39.373320] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.580789] input: Power Button (FF) as /devices/virtual/input/input4
[   39.600542] ACPI: Power Button (FF) [PWRF]
[   39.600660] input: Power Button (CM) as /devices/virtual/input/input5
[   39.612516] ACPI: Power Button (CM) [VBTN]
[   41.100464] iTCO_vendor_support: vendor-support=0
[   41.146217] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   41.146356] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   41.146366] iTCO_wdt: No card detected
[   41.383794] intel_rng: Firmware space is locked read-only. If you can't or
[   41.383797] intel_rng: don't want to disable this in firmware setup, and if
[   41.383798] intel_rng: you are certain that your system has a functional
[   41.383800] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   41.720410] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   42.049965] parport_pc 00:06: reported by Plug and Play ACPI
[   42.050023] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   42.284318] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   42.311678] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 20
[   42.311704] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   42.731613] intel8x0_measure_ac97_clock: measured 54845 usecs
[   42.731618] intel8x0: clocking to 48000
[   43.658817] lp0: using parport0 (interrupt-driven).
[   43.717831] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   44.275680] EXT3 FS on sda3, internal journal
[   45.335352] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.677870] No dock devices found.
[   45.844604] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: found ejectable bay
[   45.844611] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: Adding notify handler
[   45.844646] ACPI: Error installing bay notify handler
[   45.844649] ACPI: Bay [\_SB_.PCI0.IDE1.PRI1.MAS1] Added
[   46.891888] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   46.891894] apm: overridden by ACPI.
[   47.012439] ppdev: user-space parallel port driver
[   47.189088] audit(1220311124.642:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4714 profile="/usr/sbin/cupsd" namespace="default"
[   48.117292] Bluetooth: Core ver 2.11
[   48.117933] NET: Registered protocol family 31
[   48.117938] Bluetooth: HCI device and connection manager initialized
[   48.117942] Bluetooth: HCI socket layer initialized
[   48.140079] Bluetooth: L2CAP ver 2.9
[   48.140085] Bluetooth: L2CAP socket layer initialized
[   48.233511] Bluetooth: RFCOMM socket layer initialized
[   48.233526] Bluetooth: RFCOMM TTY layer initialized
[   48.233528] Bluetooth: RFCOMM ver 1.8
[   51.107227] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   51.107233] tg3: eth0: Flow control is on for TX and on for RX.
[   51.549857] [drm] Initialized drm 1.1.0 20060810
[   51.553487] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   51.553496] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   51.553575] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   53.262190] NET: Registered protocol family 17
[   56.173037] NET: Registered protocol family 10
[   56.173519] lo: Disabled Privacy Extensions
[   66.263928] eth0: no IPv6 routers present
[  585.871103] usb 5-7: new high speed USB device using ehci_hcd and address 4
[  586.005414] usb 5-7: configuration #1 chosen from 1 choice
[  586.116068] usbcore: registered new interface driver libusual
[  586.164012] Initializing USB Mass Storage driver...
[  586.179511] scsi4 : SCSI emulation for USB Mass Storage devices
[  586.181158] usbcore: registered new interface driver usb-storage
[  586.181167] USB Mass Storage support registered.
[  586.181638] usb-storage: device found at 4
[  586.181642] usb-storage: waiting for device to settle before scanning
[  591.164096] usb-storage: device scan complete
[  591.164975] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  591.166820] sd 4:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[  591.167692] sd 4:0:0:0: [sdb] Write Protect is off
[  591.167698] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  591.167700] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  591.170675] sd 4:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[  591.171548] sd 4:0:0:0: [sdb] Write Protect is off
[  591.171553] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  591.171555] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  591.171960]  sdb: sdb1
[  591.374221] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  591.374276] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  592.555729] UDF-fs: No partition found (1)
[  592.666280] ISOFS: Unable to identify CD-ROM format.
[28353.509165] UDF-fs: No partition found (1)
[28353.552542] ISOFS: Unable to identify CD-ROM format.
[201671.964840] usb 5-7: USB disconnect, address 4
[201710.894747] usb 5-7: new high speed USB device using ehci_hcd and address 5
[201711.029037] usb 5-7: configuration #1 chosen from 1 choice
[201711.033424] scsi5 : SCSI emulation for USB Mass Storage devices
[201711.035173] usb-storage: device found at 5
[201711.035179] usb-storage: waiting for device to settle before scanning
[201716.020208] usb-storage: device scan complete
[201716.020828] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[201716.029790] sd 5:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[201716.030410] sd 5:0:0:0: [sdb] Write Protect is off
[201716.030416] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[201716.030418] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[201716.033016] sd 5:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[201716.033891] sd 5:0:0:0: [sdb] Write Protect is off
[201716.033895] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[201716.033897] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[201716.033903]  sdb: sdb1
[201716.238681] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[201716.238736] sd 5:0:0:0: Attached scsi generic sg1 type 0
[201717.528125] UDF-fs: No partition found (1)
[201717.571500] ISOFS: Unable to identify CD-ROM format.
[201756.634989] UDF-fs: No partition found (1)
[201756.678116] ISOFS: Unable to identify CD-ROM format.
[201824.715771] UDF-fs: No partition found (1)
[201824.758773] ISOFS: Unable to identify CD-ROM format.
[201845.973212] UDF-fs: No partition found (1)
[201846.017710] ISOFS: Unable to identify CD-ROM format.
[201868.239899] UDF-fs: No partition found (1)
[201868.286643] ISOFS: Unable to identify CD-ROM format.
[201873.229283] UDF-fs: No partition found (1)
[201873.275151] ISOFS: Unable to identify CD-ROM format.
[202243.998813] loop: module loaded
[202319.126700] usb 5-7: USB disconnect, address 5
[202346.261342] usb 5-7: new high speed USB device using ehci_hcd and address 6
[202346.395759] usb 5-7: configuration #1 chosen from 1 choice
[202346.423604] scsi6 : SCSI emulation for USB Mass Storage devices
[202346.428990] usb-storage: device found at 6
[202346.428996] usb-storage: waiting for device to settle before scanning
[202351.414719] usb-storage: device scan complete
[202351.415341] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[202351.424870] sd 6:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[202351.425746] sd 6:0:0:0: [sdb] Write Protect is off
[202351.425752] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[202351.425755] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[202351.428283] sd 6:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[202351.429155] sd 6:0:0:0: [sdb] Write Protect is off
[202351.429160] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[202351.429163] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[202351.429169]  sdb: sdb1
[202351.634191] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[202351.634241] sd 6:0:0:0: Attached scsi generic sg1 type 0
[202877.701293] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xa frozen
[202877.701301] ata1: ACPI event
[202877.701334] ata1: soft resetting link
[202878.033881] ata1.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE01, max UDMA/33
[202878.245211] ata1.00: configured for UDMA/33
[202878.245222] ata1: EH complete
[202878.274034] scsi 0:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE01 PQ: 0 ANSI: 5
[202878.274130] scsi 0:0:0:0: Attached scsi generic sg2 type 5
[202878.377208] Driver 'sr' needs updating - please use bus_type methods
[202878.591741] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[202878.591749] Uniform CD-ROM driver Revision: 3.20
[202878.591832] sr 0:0:0:0: Attached scsi CD-ROM sr0
[202883.172886] usb 5-7: USB disconnect, address 6
[203004.320126] ISO 9660 Extensions: Microsoft Joliet Level 3
[203004.457940] ISO 9660 Extensions: RRIP_1991A
[203049.321443] usb 5-7: new high speed USB device using ehci_hcd and address 7
[203049.455774] usb 5-7: configuration #1 chosen from 1 choice
[203049.480428] scsi7 : SCSI emulation for USB Mass Storage devices
[203049.482821] usb-storage: device found at 7
[203049.482827] usb-storage: waiting for device to settle before scanning
[203054.466882] usb-storage: device scan complete
[203054.467634] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[203054.477468] sd 7:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[203054.478086] sd 7:0:0:0: [sdb] Write Protect is off
[203054.478091] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[203054.478094] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[203054.481318] sd 7:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[203054.482191] sd 7:0:0:0: [sdb] Write Protect is off
[203054.482196] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[203054.482199] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[203054.482206]  sdb: sdb1
[203054.688095] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[203054.688147] sd 7:0:0:0: Attached scsi generic sg1 type 0
[203055.253489] UDF-fs: No partition found (1)
[203055.297357] ISOFS: Unable to identify CD-ROM format.
[203078.618564] usb 5-7: USB disconnect, address 7
[203093.692727] ISO 9660 Extensions: Microsoft Joliet Level 3
[203094.290229] ISO 9660 Extensions: RRIP_1991A
[203104.949618] usb 5-7: new high speed USB device using ehci_hcd and address 8
[203105.084167] usb 5-7: configuration #1 chosen from 1 choice
[203105.109171] scsi8 : SCSI emulation for USB Mass Storage devices
[203105.117277] usb-storage: device found at 8
[203105.117283] usb-storage: waiting for device to settle before scanning
[203110.103012] usb-storage: device scan complete
[203110.103799] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[203110.113470] sd 8:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[203110.114335] sd 8:0:0:0: [sdb] Write Protect is off
[203110.114340] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[203110.114343] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[203110.117317] sd 8:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[203110.117940] sd 8:0:0:0: [sdb] Write Protect is off
[203110.117944] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[203110.117947] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[203110.117953]  sdb: sdb1
[203110.323726] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[203110.323779] sd 8:0:0:0: Attached scsi generic sg1 type 0
[203110.839882] UDF-fs: No partition found (1)
[203110.883999] ISOFS: Unable to identify CD-ROM format.
[205442.313939] UDF-fs: No partition found (1)
[205442.357440] ISOFS: Unable to identify CD-ROM format.
[205487.757995] usb 5-7: USB disconnect, address 8
[205581.147503] usb 5-8: new high speed USB device using ehci_hcd and address 9
[205581.281735] usb 5-8: configuration #1 chosen from 1 choice
[205581.307851] scsi9 : SCSI emulation for USB Mass Storage devices
[205581.310373] usb-storage: device found at 9
[205581.310379] usb-storage: waiting for device to settle before scanning
[205586.292971] usb-storage: device scan complete
[205586.293591] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[205586.301351] sd 9:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[205586.302297] sd 9:0:0:0: [sdb] Write Protect is off
[205586.302302] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[205586.302304] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[205586.304922] sd 9:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[205586.305549] sd 9:0:0:0: [sdb] Write Protect is off
[205586.305554] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[205586.305557] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[205586.305563]  sdb: sdb1
[205586.510698] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[205586.510747] sd 9:0:0:0: Attached scsi generic sg1 type 0
[205587.015390] UDF-fs: No partition found (1)
[205587.058644] ISOFS: Unable to identify CD-ROM format.
[205668.531342] usb 5-8: USB disconnect, address 9
[205700.384936] usb 5-8: new high speed USB device using ehci_hcd and address 10
[205700.519232] usb 5-8: configuration #1 chosen from 1 choice
[205700.545001] scsi10 : SCSI emulation for USB Mass Storage devices
[205700.552627] usb-storage: device found at 10
[205700.552632] usb-storage: waiting for device to settle before scanning
[205705.538317] usb-storage: device scan complete
[205705.538941] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[205705.548410] sd 10:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[205705.549249] sd 10:0:0:0: [sdb] Write Protect is off
[205705.549256] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[205705.549258] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[205705.551760] sd 10:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[205705.552630] sd 10:0:0:0: [sdb] Write Protect is off
[205705.552635] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[205705.552638] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[205705.552644]  sdb: sdb1
[205705.757787] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[205705.757837] sd 10:0:0:0: Attached scsi generic sg1 type 0
[205706.208885] UDF-fs: No partition found (1)
[205706.255136] ISOFS: Unable to identify CD-ROM format.
[235566.609508] usb 5-8: USB disconnect, address 10
[235570.320660] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xa frozen
[235570.320668] ata1: ACPI event
[235570.320701] ata1: soft resetting link
[235570.692491] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[235570.692499] ata1.00: revalidation failed (errno=-5)
[235570.692503] ata1: failed to recover some devices, retrying in 5 secs
[235575.681204] ata1: soft resetting link
[235576.251811] ata1.00: configured for UDMA/33
[235576.251830] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[235576.251834] ata1: ACPI event
[235576.251868] ata1: soft resetting link
[235576.806219] ata1.00: configured for UDMA/33
[235576.806230] ata1: EH complete
[235585.000987] VFS: busy inodes on changed media.
[235585.010353] VFS: busy inodes on changed media.
[235813.036267] VFS: busy inodes on changed media.
[235813.051602] VFS: busy inodes on changed media.
[275432.301704] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xa frozen
[275432.301712] ata1: ACPI event
[275432.301746] ata1: soft resetting link
[275432.673547] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[275432.673555] ata1.00: revalidation failed (errno=-5)
[275432.673560] ata1: failed to recover some devices, retrying in 5 secs
[275437.661784] ata1: soft resetting link
[275438.033598] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[275438.033606] ata1.00: revalidation failed (errno=-5)
[275438.033611] ata1: failed to recover some devices, retrying in 5 secs
[275443.022308] ata1: soft resetting link
[275443.394441] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[275443.394449] ata1.00: revalidation failed (errno=-5)
[275443.394454] ata1.00: disabled
[275443.895790] ata1: soft resetting link
[275444.061625] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[275444.061633] ata1: ACPI event
[275444.061664] ata1: soft resetting link
[275444.225024] ata1: EH complete
[275444.225110] ata1.00: detaching (SCSI 0:0:0:0)
[275444.238263] VFS: busy inodes on changed media.
[275445.924889] scsi 0:0:0:0: rejecting I/O to dead device
[275445.924907] scsi 0:0:0:0: rejecting I/O to dead device
[275445.924913] scsi 0:0:0:0: rejecting I/O to dead device
[275475.746048] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xa frozen
[275475.746057] ata1: ACPI event
[275475.746090] ata1: soft resetting link
[275476.079634] ata1.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE01, max UDMA/33
[275476.275027] ata1.00: configured for UDMA/33
[275476.275040] ata1: EH complete
[275476.298354] scsi 0:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE01 PQ: 0 ANSI: 5
[275476.516852] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[275476.516923] sr 0:0:0:0: Attached scsi CD-ROM sr0
[275476.516971] sr 0:0:0:0: Attached scsi generic sg1 type 5
[275490.505246] ISO 9660 Extensions: Microsoft Joliet Level 3
[275490.643056] ISO 9660 Extensions: RRIP_1991A

```

I see a lot of i/o errors. Is this the problem?

---

### Post by Rocket2DMn on 2008-09-05
I've seen those errors with SATA hard drives during the boot process before, which we solved by using the "irqpoll" kernel boot option.  However, it seems to have done its cycle and gotten around the errors.  You say that it doesn't work - exactly what is happening?  Is there a cd or dvd in the drive when you plug it in?  If not, what happens when you do insert a disc (nothing will mount unless there is a disc in the drive).

---

### Post by racecarpete on 2008-09-05
So it seems a restart fixed the problem.

After editing 

```
gksudo gedit /etc/fstab
```

and commenting out the last line to look like this.

```
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I inserted the thumb drive first then the DVD drive. 

The thumb drive worked, and the DVD drive would appear but I would get a "can not mount data" whenever I inserted a disk.

I restarted and everything is working.

Thanks for your help.

---

