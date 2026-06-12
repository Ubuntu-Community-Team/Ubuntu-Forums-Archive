---
title: "Audio CD Freeze in Edgy, Data CDs Work"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by catfishk on 2007-10-07
my Thinkpad can read and write data cds fine, however it will lock the whole machine when an audio CD is inserted.  i have updated the drive's firmware to no avail.  the device is registered at /dev/scd0, /dev/sr0

dmesg | grep DVD:

[17179573.008000]   Vendor: HL-DT-ST  Model: RW/DVD GCC-4247N  Rev: 1.02

dmesg | grep CD:

[17179569.184000] ACPI: ECDT (v001 LENOVO TP-79    0x00002060 LNVO 0x00000001) @ 0x7fededcc
[17179570.348000] ACPI: Found ECDT
[17179573.008000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179589.020000] Uniform CD-ROM driver Revision: 3.20
[17179589.020000] sr 1:0:0:0: Attached scsi CD-ROM sr0

any ideas?

---

### Post by catfishk on 2007-10-08
DVD playback works flawlessly, i can add.  however, i believe that DVDs are mounted before they are read and audio CDs are not.  this is probably my issue

i am not getting errors when accessing audio CDs, just a system freeze

---

### Post by catfishk on 2007-10-08
i have also downgraded cdparanoia as per this [[COLOR="Blue"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000") to no avail :(

---

### Post by catfishk on 2007-11-23
upgraded to Gutsy, finally.  all is well!

---

