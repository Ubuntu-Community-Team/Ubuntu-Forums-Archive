---
title: "After suspend... freeze on CD drive usage"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by [Rui] on 2005-11-10
Okay, I'm using Breezy, and this problem is pissing me off.

I am extremely gratefull for a distribution that has suspend from source, but my laptop sucks. It doesn't have apm, and acpi is borked (according to HP forums, even on Windows suspend is terribly dangerous, NX9010).

After coming back from suspend, if I even try to access my cd drive it freezes. Just like that.


This is my hardrive:

root@roque:~# hdparm -I /dev/hdc

/dev/hdc:

ATAPI CD-ROM, with removable media
        Model Number:       SONY CD-RW/DVD-ROM CRX830E
        Serial Number:
        Firmware Revision:  JPK4
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-2
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 *mdma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=227ns  IORDY flow control=120ns

The last message on syslog before reboot is:
Nov 10 11:00:40 localhost kernel: [4442827.056000] cdrom: This disc doesn't have any tracks I recognize!

(the CD was a virgin one, but this has happened with data CDs and audio CDs so I suspect the drive not the kind of disks).

Any suggestions?

---

### Post by Davor281 on 2005-11-10
Hi!

Try to uncomment the 

# RESET_DRIVE=true

in /etc/acpi/acpi-support. You will find this text above the line:

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys.

ENjoY!

Davor.

---

### Post by [Rui] on 2005-11-12
Erms... that's /etc/**default**/acpi-support ...

But anyways, it didn't work. Total freeze :|

Thanks anyway.

---

### Post by Davor281 on 2005-11-12
"Erms... that's /etc/default/acpi-support ..."

Akhm ..... feel so lame ...

---

### Post by [Rui] on 2005-11-13
no problem :) happens to all!

---

