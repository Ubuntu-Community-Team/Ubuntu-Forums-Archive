---
title: "highpoint rocketraid 2720 sgl driver"
date: 2015-10-15
forum: Hardware
---

### Post by gertjan-silkens on 2015-10-15
I have a problem with the latest driver from highpoint rocket raid rr272x_1x after installing. I reboot my computer, the controller is visible but no disk or raid configurations are found. only in the bois of the raid controller. I look in my kernel messages and i found this

[    1.751619] rr272x_1x: module license 'Proprietary' taints kernel.
[    1.751915] rr272x_1x: module verification failed: signature and/or  required key missing - tainting kernel
[    1.752311] rr272x_1x:RocketRAID 272x_1x controller driver v1.5.21
[    2.020492] rr272x_1x:adapter at PCI 6:0:0, IRQ 20
[    4.975133] rr272x_1x:workround irqStatus = 0x300
[    4.995018] rr272x_1x:workround irqStatus = 0xf00
[   34.614248] rr272x_1x:port reset not complete success, ignore the port (0)
[   34.614259] rr272x_1x:port reset not complete success, ignore the port (1)
[   34.614270] rr272x_1x:port reset not complete success, ignore the port (0)
[   34.614276] rr272x_1x:port reset not complete success, ignore the port (1)
[   34.614282] rr272x_1x:port reset not complete success, ignore the port (2)
[   34.614288] rr272x_1x:port reset not complete success, ignore the port (3)
[   34.614567] scsi host4: rr272x_1x

I think this is not normal, 

my kernel version is (uname -a)

Linux srv 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


lubuntu 14.04 LTS

---

