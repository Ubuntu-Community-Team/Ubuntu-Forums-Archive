---
title: "Compiling the kernel issues"
date: 2005-12-06
forum: General Help
---

### Post by cougem on 2005-12-06
Hi I'm compiling my kernel using the config from here:
[http://ubuntuforums.org/showthread.php?t=46536](http://ubuntuforums.org/showthread.php?t=46536)

It gets a fair way through, but then it dies for the following reason:

  CC [M]  drivers/scsi/libata-core.o
In file included from drivers/scsi/libata-core.c:45:
include/linux/libata.h:41:24: warning: extra tokens at end of #undef directive
drivers/scsi/libata-core.c: In function `ata_device_resume':
drivers/scsi/libata-core.c:3732: error: `ATA_FLAG_SUSPENDED' undeclared (first u se in this function)
drivers/scsi/libata-core.c:3732: error: (Each undeclared identifier is reported only once
drivers/scsi/libata-core.c:3732: error: for each function it appears in.)
drivers/scsi/libata-core.c: In function `ata_device_suspend':
drivers/scsi/libata-core.c:3759: error: `ATA_FLAG_SUSPENDED' undeclared (first u se in this function)
drivers/scsi/libata-core.c: In function `ata_host_init':
drivers/scsi/libata-core.c:3864: error: structure has no member named `port_flag s'
drivers/scsi/libata-core.c: At top level:
drivers/scsi/libata-core.c:4569: error: `ata_scsi_device_suspend' undeclared her e (not in a function)
drivers/scsi/libata-core.c:4569: error: initializer element is not constant
drivers/scsi/libata-core.c:4569: error: (near initialization for `__ksymtab_ata_ scsi_device_suspend.value')
drivers/scsi/libata-core.c:4570: error: `ata_scsi_device_resume' undeclared here  (not in a function)
drivers/scsi/libata-core.c:4570: error: initializer element is not constant
drivers/scsi/libata-core.c:4570: error: (near initialization for `__ksymtab_ata_ scsi_device_resume.value')
drivers/scsi/libata-core.c:4569: error: __ksymtab_ata_scsi_device_suspend causes  a section type conflict
drivers/scsi/libata-core.c:4570: error: __ksymtab_ata_scsi_device_resume causes a section type conflict
make[3]: *** [drivers/scsi/libata-core.o] Error 1
make[2]: *** [drivers/scsi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2


Anyone any idea why? :(

---

