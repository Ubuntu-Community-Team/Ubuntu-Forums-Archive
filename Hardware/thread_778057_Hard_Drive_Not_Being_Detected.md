---
title: "Hard Drive Not Being Detected"
date: 2008-05-01
forum: Hardware
---

### Post by Ek0nomik on 2008-05-01
My hard drive isn't detected during the Ubuntu Live CD installation.  I tried using GParted 0.3.6-7 to change the partitions, and I receive the following:

```
ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
ahci 0000.00:1f.2: flags: 64 bit ncq pm led slum part
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
ata1: SATA max UDMA/133 cmd 0xf8830d00 ctl 0x00000000 bmdma 0x00000000 irq 22
ata2: SATA max UDMA/133 cmd 0xf8830d80 ctl 0x00000000 bmdma 0x00000000 irq 22
ata3: SATA max UDMA/133 cmd 0xf8830e00 ctl 0x00000000 bmdma 0x00000000 irq 22
ata4: SATA max UDMA/133 cmd 0xf8830e80 ctl 0x00000000 bmdma 0x00000000 irq 22
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: qc timeout (cmd 0x27)
ata1.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (781422768)
ata1.00: ATA-7: HDS724040KLSA80, KFA0A20N, max UDMA/133
ata1.00: 781422768 sectors, multi 8: LBA48
ata1.00: failed to set xfermode (err_mask=0x40)
ata1: failed to recover some devices, retrying in 5 secs
ata1: port is slow to respond, please be patient (Status 0x80)
ata1: COMRESET failed (errno=-16)
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: qc timeout (cmd 0x27)
ata1.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (781422768)
ata1.00: failed to set xfermode (err_mask=0x40)
ata1.00: limiting speed to UDMA/133:P103
ata1: failed to recover some devices, retrying in 5 secs
ata1: port is slow to respond, please be patient (Status 0x80)
ata1: COMRESET failed (errno=-16)
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: qc timeout (cmd 0x27)
ata1.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (781422768)
ata1.00: failed to set xfermode (err_mask=0x40)
ata1.00: disabled
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Done.
Begin: Mounting root file system... ...
```

Once I get the GUI in GParted it also doesn't detect anything.

However, Fedora seems to actually find the hard drive.  When I open GParted in the Fedora 8 Live CD I am unable to resize the NTFS partition because of this error:

```

The device /dev/sda1 doesn't exist.
Failed to check '/dev/sda1' mount state: No such file or directory
Probably /etc/mtab is missing. It's too risky to continue.

```

So, I saw that the hard drive was being detected, I just couldn't "make use of it". So I was curious to see if I could mount the thing and look at the Windows files on it. I was. I was able to mount it through the terminal to /media/Windows, and I was able to browse all the files on the hard drive. When I did that and opened GParted again, obviously it showed the hard drive as being locked since it was mounted, but it actually showed how much data was being used graphically this time around. That light brown color was shading in how much data had been used. So I unmounted it, but again, the same problem persists.

If anyone can offer some help I'd greatly appreciate it, as this seems to be a serious error across multiple distributions.

Output of lsmod:  [http://paste.ubuntu.com/9673/](http://paste.ubuntu.com/9673/)
Output of lspci -v:  [http://paste.ubuntu.com/9675/](http://paste.ubuntu.com/9675/)

---

### Post by Ek0nomik on 2008-05-02
More information:

The testing version of GParted 0.3.7-2, is able to find my hard drive without any errors.

Does this settle it that it's a kernel issue?  Even if the testing version of GParted can find my hard drive, it seems as though all the linux distros still won't be able to find it.

---

