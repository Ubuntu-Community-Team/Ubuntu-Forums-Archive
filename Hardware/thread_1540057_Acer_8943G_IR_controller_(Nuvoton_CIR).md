---
title: "Acer 8943G IR controller (Nuvoton CIR)"
date: 2010-07-27
forum: Hardware
---

### Post by Velaar on 2010-07-27
I'm trying to make it working with 
```
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid

```
And lirc-0.8.6.0ubuntu4 

This driver [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/570700]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/570700")
loads successfully with message: 

```
Jul 27 17:15:52 laptop kernel: [13666.125095] lirc_dev: IR Remote Control driver registered, major 61
Jul 27 17:15:52 laptop kernel: [13666.126408] lirc_wb677 w677hga: chip id high: 0xfc expect:0xb4
Jul 27 17:15:52 laptop kernel: [13666.126414] lirc_wb677 w677hga: chip id low: 0x11
Jul 27 17:15:52 laptop kernel: [13666.126644] input: MCE Remote Keyboard as /devices/virtual/input/input11
Jul 27 17:15:52 laptop kernel: [13666.126713] lirc_dev: lirc_register_driver: sample_rate: 0

```

Than a strange bug appears. It looks like the Enter key is pressed and the only solution is rebooting. 

Can anyone help?

---

