---
title: "cd/dvd drive &quot;opens&quot; after waking from sleep"
date: 2010-12-28
forum: Hardware
---

### Post by editrix on 2010-12-28
I'm using Mint9 KDE, but I suspect this is a kernel issue, and when I posted on the Mint forums I got no reply, so I'm trying here.

I have a Sony CDRWDVD in an HP DC5100 desktop computer.

The drive works fine until I suspend to RAM. When I wake it up, the drive won't work.

When the drive works:
**sudo lshw -C disk**

  ```
*-cdrom                 
       description: DVD reader
       product: CDRWDVD CRX310EE
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SDK3
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 [COLOR="Red"]status=nodisc[/COLOR]

```
After waking from suspend:
```

*-cdrom                 
       description: DVD reader
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd
       configuration: [COLOR="Red"]status=open[/COLOR]
```

Note no product, vendor or version lines, either.

Again, when the drive works:
**sudo hdparm -I /dev/cdrom**

```
/dev/cdrom:

ATAPI CD-ROM, with removable media
        Model Number:       SONY CD-RW/DVD-ROM CRX310EE             
        Serial Number:      2006030800037033    
        Firmware Revision:  SDK3    
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-2 
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
        cache/buffer size  = unknown
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=227ns  IORDY flow control=120ns
```

After waking from suspend:

```
/dev/cdrom:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange

```
My googling has turned up a lot of problems with optical drives, but not this one.

My fstab has no line for the drive--I believe this is how Mint wrote the fstab.

What I've tried so far:

1. Upgrading & downgrading kernels (currently using 2.6.32-21-generic #32-Ubuntu). With some kernels, I couldn't even get the drive to physically open by pushing the button.

2. adding "noacpi" to /etc/default/grub

3. adding various mount points for the drive

I have no idea if the problems are connected, but I can't use the menu to suspend/sleep. The panel widget, however, does work.

None of this makes any sense to me. Has anyone any other ideas I could try?

---

