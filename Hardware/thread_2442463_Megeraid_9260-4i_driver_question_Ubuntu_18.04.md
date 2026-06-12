---
title: "Megeraid 9260-4i driver question Ubuntu 18.04"
date: 2020-05-04
forum: Hardware
---

### Post by ddebevec on 2020-05-04
I have installed an LSI Megaraid 9260-4i and I've been searching for a compatible driver for my Ubuntu 18.04 install.  My first question, is support for LSI raid cards already built into the newer releases of Ubuntu.  I also found drivers on the Broadcom website, but they look to be for older releases of Ubuntu.  Looks like maybe release 9.  They also don't give instructions as to how to install it.  Anyone have any experience with LSI cards and newer releases of Ubuntu that may be able to give some direction.  Thanks!

---

### Post by SeijiSensei on 2020-05-04
The megaraid drivers have been in the kernel for years.  You shouldn't need to do anything special to enable them.  If the system detects the LSI card, it should load the modules needed.  On my 20.04 system, there is 

```
/usr/lib/modules/5.4.0-14-generic/kernel/drivers/scsi/megaraid
```

You should have the equivalent directory on 18.04.

Quick test is to run "lsmod" and see if there's a megaraid module loaded.  If you attach a drive to the card, is it detected?

---

### Post by ddebevec on 2020-05-04
I ran lsmod and the following items showed up:
mpt3sas               245760  0
raid_class             16384  1 mpt3sas
scsi_transport_sas     40960  1 mpt3sas
mptctl                 40960  0
mptbase                94208  1 mptctl
megaraid_sas          155648  3

Looks like I can stop spinning my wheels looking for a driver.
Thanks for your help.

---

### Post by SeijiSensei on 2020-05-04
You're welcome.  Please mark the thread as [SOLVED] in the Thread Tools drop-down above.

---

