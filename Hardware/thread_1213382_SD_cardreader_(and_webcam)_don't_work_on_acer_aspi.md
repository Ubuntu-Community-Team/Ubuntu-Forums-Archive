---
title: "SD cardreader (and webcam) don't work on acer aspire 9410"
date: 2009-07-14
forum: Hardware
---

### Post by Adriaan S on 2009-07-14
Hi

I've installed 9.4 on the acer aspire 9410 of my girlfriend because her laptop was always crashing with windows (even after a fresh install and a lot of visits to a computerspecialist). I've already googled the problem and tried an irc channel but without succes. My girlfriend is a huge fotofan and absolutly wants the cardreader working.

Here some output of some terminal code I ran for the conversation on irc.

```

lien@lien-laptop ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

```
lien@lien-laptop ~ $ sudo fdisk -l
[sudo] password for lien: 

Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xeb1ddf44

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1         182     1461883+  82  Linux wisselgeheugen
/dev/sda2             183       19457   154826437+   5  Uitgebreid
/dev/sda5             183         790     4883728+  83  Linux
/dev/sda6             791       19457   149942646   83  Linux
```

```
lien@lien-laptop ~ $ dmesg| tail
[ 1276.930285] wlan0: authenticate with AP 00:12:bf:12:33:40
[ 1276.931961] wlan0: authenticated
[ 1276.931965] wlan0: associate with AP 00:12:bf:12:33:40
[ 1276.933963] wlan0: authenticate with AP 00:12:bf:12:33:40
[ 1276.936794] wlan0: authenticated
[ 1276.936797] wlan0: associate with AP 00:12:bf:12:33:40
[ 1276.938633] wlan0: RX ReassocResp from 00:12:bf:12:33:40 (capab=0x461 status=0 aid=5)
[ 1276.938636] wlan0: associated
[ 1282.121037] wlan0: no IPv6 routers present
[ 1809.689140] CE: hpet increasing min_delta_ns to 22500 nsec
```

```
lien@lien-laptop ~ $ lsmod| grep -i sd
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
```

```
lien@lien-laptop ~ $ lsmod| grep -i mmc

there was no output here
```

```
lien@lien-laptop ~ $ lsmod| grep -i tifm
tifm_7xx1              13824  0 
tifm_core              15900  1 tifm_7xx1
```

```
lien@lien-laptop ~ $ tail -f /var/log/messages
Jul 13 21:23:38 lien-laptop gnome-screensaver-dialog: pam_sm_authenticate: Called 
Jul 13 21:23:38 lien-laptop gnome-screensaver-dialog: pam_sm_authenticate: username = [lien] 
Jul 13 21:23:38 lien-laptop gnome-screensaver-dialog: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jul 13 21:32:32 lien-laptop kernel: [ 1809.689140] CE: hpet increasing min_delta_ns to 22500 nsec
Jul 13 21:33:36 lien-laptop sudo: pam_sm_authenticate: Called 
Jul 13 21:33:36 lien-laptop sudo: pam_sm_authenticate: username = [lien] 
Jul 13 21:33:36 lien-laptop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jul 13 21:36:00 lien-laptop kernel: [ 2017.877137] ACPI: EC: missing confirmations, switch off interrupt mode.
Jul 13 22:02:35 lien-laptop -- MARK --
Jul 13 22:22:35 lien-laptop -- MARK --
Jul 13 22:42:35 lien-laptop -- MARK --
Jul 13 22:42:47 lien-laptop kernel: [ 6025.100154] tifm_core: MemoryStick card detected in socket 0:0
```

```
lien@lien-laptop ~ $ lsusb
Bus 001 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

That's all I have. If you need more output, just ask. There were also some issues with her webcam, but to have her cardreader working is the most important thing.
 
Oh, i have a toshiba satellite A300-16I and the SD card also doesn't mount on my system but if I mount on XP, it works out-of-the-box.

Thanks in advance

---

### Post by Adriaan S on 2009-07-15
Already down to page 3 in 8 hours, thats fast. I hope I get help her, my girlfriend is thinking about switching back to windows because of this problem. That should be a pitty. Her laptop works so much faster know, but the cardreader doesn't work and that's a big deal for her. :(

---

### Post by Adriaan S on 2009-07-15
Nobody that wants to give a shot at it?

---

### Post by Adriaan S on 2009-07-30
maybe a bump will help!

---

