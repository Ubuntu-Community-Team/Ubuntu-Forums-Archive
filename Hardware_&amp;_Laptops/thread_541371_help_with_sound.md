---
title: "help with sound"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by Caton420 on 2007-09-02
Let me start out with saying iv asked this in the beginers forum and nobody has a clue other than "Reinstall Ubuntu?" My problem is i have absolutlly no sound of any kind, when i installed this before (same dvd) it had sound perfectally, but now i have dual boot winxp and Ubuntu 7.04 fiesty. 
```
caton420@caton420-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
caton420@caton420-laptop:~$ 

```
i was thinking reinstall drivers mabey?

---

### Post by moore.bryan on 2007-09-02
*[here]("https://answers.launchpad.net/ubuntu/+question/12617")'s a similar issue and resolution... can you [rube goldberg]("http://en.wikipedia.org/wiki/Rube_Goldberg") it to make it work for you?*

---

### Post by Caton420 on 2007-09-02
nope there situation worked with headphones, mine dont

---

### Post by ninhobomba on 2007-09-02
Hello.... I don't know if this might be useful but my gf and i had a similar problem and we solved it installing a *fresh* alsa system and sound drivers... here is our thread....

[http://ubuntuforums.org/showthread.php?p=3216934]("http://ubuntuforums.org/showthread.php?p=3216934")

I hope it is any help...we have not had any problems since we did this fix.
Luck!

---

### Post by moore.bryan on 2007-09-03
^^^^^
[I]i was going to suggest the same thing.  the alsa steps it took for me, i posted in some other thread, but i can't remember which, so here they are:
[/I]> [I]try this... it took all this to get my sound working on a lenovo thinkpad z61e...
grab the alsa stuff and compile from source:
[alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")
[alsa-lib-1.0.14a]("ftp://ftp.alsa-project.org/pub/driver/alsa-lib-1.0.14a.tar.bz2")
[alsa-utils-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-utils-1.0.14.tar.bz2")
[alsa-tools-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-tools-1.0.14.tar.bz2")
[alsa-firmware-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-firmware-1.0.14.tar.bz2")
[alsa-plugins-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-plugins-1.0.14.tar.bz2")
[alsa-oss-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-oss-1.0.14.tar.bz2")
[pyalsa-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/pyalsa-1.0.14.tar.bz2")
and then run ```

     alsamixergui 
```
 to set the volumes,      ```

     sudo alsactl store 
```
 to keep your settings and add      ```

     alsactl restore 
```
 to your /etc/rc.local file.
[/I]

---

