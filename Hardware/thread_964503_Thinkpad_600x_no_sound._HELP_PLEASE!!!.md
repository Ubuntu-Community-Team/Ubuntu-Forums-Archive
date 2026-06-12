---
title: "Thinkpad 600x no sound. HELP PLEASE!!!"
date: 2008-10-31
forum: Hardware
---

### Post by grumpy_jew on 2008-10-31
I have recently installed the latest ubuntu onto my thinkpad 600x notebook. i have been racking my head and reading many different forums and searches on google and have not been able to in anyway to actually get the sound to work on this notebook. If anyone can help me i would be greatly appreciated. My skill level is mediocre.

thanks in advance. i will will be happy to supply any other info about my comp that would be in any way helpful to slove this issue.

---

### Post by ardvark71 on 2008-10-31
> **grumpy_jew said:**
> My skill level is mediocre.

Hi...

Don't feel bad, so is mine. ;)

I can't promise I'll fix your problem but I can take a shot at it. First, could you post the results of...

```
lspci
```

Best Regards...

---

### Post by grumpy_jew on 2008-10-31
I do appreciate the help weather it works or not. all of this is a learning tool for me. So again i Thank you.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: Neomagic Corporation NM2360 [MagicMedia 256ZX]
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by ardvark71 on 2008-10-31
Hi...

I'm not sure what threads you've read so far but I did find these...

Did you lose sound after using "suspend" to turn off your notebook? Here is a bug report that addresses that...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/11149](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/11149)

Also here is another person who had a similar problem...

[http://www.uluga.ubuntuforums.org/showthread.php?t=643175](http://www.uluga.ubuntuforums.org/showthread.php?t=643175)

There are other commands given on that thread that might help you to narrow down what the problem is. On the 4th post is this troubleshooting guide which you may have already seen:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Please post back with any results or if you have any questions or still can't get it working. :)

Best Regards...

---

