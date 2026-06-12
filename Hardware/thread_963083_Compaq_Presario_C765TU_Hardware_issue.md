---
title: "Compaq Presario C765TU Hardware issue"
date: 2008-10-29
forum: Hardware
---

### Post by lasitha on 2008-10-29
Hi I am new to Ubuntu. Got tired of Vista and chose  to install Ubuntu instead of the other alternative. Throw the damn laptop.

Anyway.. can't seem to get my webcam working nor the wireless LAN (Atheros)
they worked fine on Vista, though. Hardware Drivers indicate that the Atheros LAN is enabled but the indicator does not light up. Nor am I getting a connection.

Can anyone tell me how to get these two working pls?

Thanks heaps

---

### Post by ardvark71 on 2008-10-30
> **lasitha said:**
> Hi I am new to Ubuntu. Got tired of Vista and chose  to install Ubuntu instead of the other alternative. Throw the damn laptop.

Anyway.. can't seem to get my webcam working nor the wireless LAN (Atheros)
they worked fine on Vista, though. Hardware Drivers indicate that the Atheros LAN is enabled but the indicator does not light up. Nor am I getting a connection.

Can anyone tell me how to get these two working pls?

Thanks heaps

Hi...

I'm not sure if I can help but I can hopefully get things started. :) Could you please post the results of...

```
lspci
```

Best Regards...

---

### Post by lasitha on 2008-10-30
Hey Ardwark,
the results are as follows...

lasitha@lasitha-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by lasitha on 2008-10-30
Aardwaar
want to mention here that at start up the Web Cam indicator lights up for a few seconds///

---

### Post by ardvark71 on 2008-10-30
Hi...

For your wireless chipset, "madwifi" might do the job. It might be included in the packages found in Synaptic. Here is a thread with further information and instructions...

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

In case it's not available through any other means, you can download it at madwifi.org's homepage...

[http://madwifi.org/](http://madwifi.org/)

As to your webcam, I didn't see the device listed in your results. Do you, by any chance, know the chipset model and number?

Hope this helps. :)

Best Regards...

---

### Post by lasitha on 2008-11-03
Hey Aardwark
m8, tred it in so many ways... no success yet... no worries. Will wait.

Thanks for your help. Appreciate it a lot.

---

