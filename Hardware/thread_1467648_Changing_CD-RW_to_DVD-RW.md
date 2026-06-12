---
title: "Changing CD-RW to DVD-RW?"
date: 2010-04-30
forum: Hardware
---

### Post by MrBaseball34 on 2010-04-30
I have my Ubuntu 9.1 installed into a VM on my windows machine.

Was wondering what I have to do to get it to recognize my DVD writer.  When I installed the VM, I had a CD-RW and changed it to a DVD-RW.

Windows sees it just fine because it installs it automatically.

fstab shows:
```
/dev/scd0     /media/cdrom0    udf,iso9660 user,noauto,exec,utf8  0     0
```

I installed in the VM from an ISO image but have changed it to a drive letter
via VMWare's Removable Devices->Settings dialog.

This is how lshw reports it:
```

*-cdrom
      description: SCSI CD-ROM
      product: DVD RW AW-G170A
      vendor: SONY
      physical id: 0.0.0
      bus info: scsi@1:0.0.0
      logical name: /dev/cdrom
      logical name: /dev/scd0
      logical name: /dev/sr0
      version: 1.62
      serial: [SONY    DVD RW AW-G170A 1.62 Dec19,2006
      capabilities: removable audio
      configuration: ansiversion=5 status=ready
    *-medium
         physical id: 0
         logical name: /dev/cdrom

```

However, tovid (makedvd) doesn't think I have a DVD writer in my machine.

What do I need to do to get the Ubuntu to see it?

---

### Post by MrBaseball34 on 2010-05-01
Using /dev/scd0 with the -device switch on makedvd worked.
Wonder why it is so difficult for it to recognize alone?

---

