---
title: "Cannot access DVDs - neither Data nor Video"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by claude_c on 2007-08-29
Hi there,

I'm running Ubuntu Feisty on a Tinkpad T40, stock kernel (generic). CD reading and writing works fine, mounting DVDs however does not work since installation. The drive however worked fine before.

dmesg notifies that the drive is

```

 scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[...]
[    4.916000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.916000] sr 1:0:0:0: Attached scsi CD-ROM sr0

```

lshw reports its dvd capabilities:

```

 *-cdrom
       description: DVD reader
       product: UJDA745 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom

```

and when trying to mount a dvd all it says it "No medium found.".
nothing more. 
as said, mounting CDs and writing CDRs works without any problems.

any help would be appreciated.. :)

claude

---

