---
title: "Signing a custom kernel device driver"
date: 2014-08-06
forum: Hardware
---

### Post by roy21 on 2014-08-06
First time posting to the forums so thanks in advance for any answers.  I've Googled this to death and did not find any answers on this site either so hopefully someone here can help.

I have written a kernel device driver for some custom hardware, specifically a PCIe Endpoint.  The driver works fine but I noticed in dmesg the following error:

> roy@euclid:~$ dmesg | grep lbi
[   18.465845] lbi: module verification failed: signature and/or required key missing - tainting kernel


From what I've gathered I should be able to sign my driver using my own gpg private key with the > scripts/sign-file tool but I cannot find the kernel's public key which is a required parameter.  Does anyone know where it is?  Am I going about this the wrong way?

I'm running Ubuntu 13.10 64-bit.

> roy@euclid:~$ uname -a
Linux euclid 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

This is the [documentation]("https://www.kernel.org/doc/Documentation/module-signing.txt") I've been working from so far.

Regards,

Roy

---

### Post by roy21 on 2014-08-06
Additional info:
> 
roy@euclid:~$ modinfo lbi
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/lbi/lbi.ko
license:        GPL
description:    Lower Buoy Interface Driver
author:         Roy Johnson <rjohnson@sparton.com>
srcversion:     D27EDD9D44EC56F4E1E2DA5
alias:          pci:v000010EEd00000007sv*sd*bc*sc*i*
depends:        
vermagic:       3.11.0-19-generic SMP mod_unload modversions

---

