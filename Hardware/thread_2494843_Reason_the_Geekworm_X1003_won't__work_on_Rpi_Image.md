---
title: "Reason the Geekworm X1003 won't  work on Rpi Imager Ubuntu Image"
date: 2024-01-28
forum: Hardware
---

### Post by etyrnal3 on 2024-01-28
[B]Is there a logical reason the Geekworm X1003 would not work on the Ubuntu image that the Raspberry Pi Imager can create? 
[/B]
I have a whole server set up and running perfectly on a **Raspberry Pi 5B** 8GB **using the latest Ubuntu image the Raspberry Pi Imager produces**, and also i added Nextcloud, PlexMediaServer, Airsonic, samba, webmin, etc. All works great -- even mdadm. 

Even after following ALL directions in Geekworm's wiki first, updating eeprom, updating /boot/firmware/config.txt, etc., sudo lsblck, and sudo dmesg **don't seem to see this device or the attached "KingSpec 512GB 2230 SSD NVMe Gen3x4, M.2 PCIe 3.0 SSD with 3D NAND Flash"**.

I can't see any lights on the geekworm X1003, nor on the M.2.

**Is there anything that would be missing in the Ubuntu image that would prevent this from working?**

~$ [B]sudo lsblk
[/B]NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS
loop0 7:0 0 4K 1 loop /snap/bare/5
loop1 7:1 0 177M 1 loop /snap/airsonic/167
[redacted]
loop25 7:25 0 35.5M 1 loop /snap/snapd/20298
**mmcblk0** 179:0 0 238.8G 0 disk
&#9500;&#9472;**mmcblk0p1** 179:1 0 512M 0 part /boot/firmware
&#9492;&#9472;**mmcblk0p2** 179:2 0 238.2G 0 part /var/snap/firefox/common/host-hunspell
**/**
:~$

:~$ [B]sudo dmesg | grep pcie
[/B][ 0.000000] Kernel command line: coherent_pool=1M 8250.nr_uarts=1 pci=pcie_bus_safe snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 smsc95xx.macaddr=D8:3ADB:55:22 vc_mem.mem_base=0x3fc00000 vc_mem.mem_size=0x40000000 zswap.enabled=1 zswap.zpool=z3fold zswap.compressor=zstd multipath=off dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 rootwait fixrtc quiet splash
[ 0.558187] brcm-pcie 1000110000.pcie: host bridge /axi/pcie@110000 ranges:
[ 0.558198] brcm-pcie 1000110000.pcie: No bus range found for /axi/pcie@110000, using [bus 00-ff]
[ 0.558220] brcm-pcie 1000110000.pcie: MEM 0x1b00000000..0x1bfffffffb -> 0x0000000000
[ 0.558230] brcm-pcie 1000110000.pcie: MEM 0x1800000000..0x1affffffff -> 0x0400000000
[ 0.558241] brcm-pcie 1000110000.pcie: IB MEM 0x0000000000..0x0fffffffff -> 0x1000000000
[ 0.559371] brcm-pcie 1000110000.pcie: Forcing gen 2
[ 0.559585] brcm-pcie 1000110000.pcie: PCI host bridge to bus 0000:00
[ 0.992568] brcm-pcie 1000110000.pcie: link down
[ 0.992918] pcieport 0000:00:00.0: PME: Signaling with IRQ 43
[ 0.993033] pcieport 0000:00:00.0: AER: enabled with IRQ 43
[ 0.993642] brcm-pcie 1000120000.pcie: host bridge /axi/pcie@120000 ranges:
[ 0.993649] brcm-pcie 1000120000.pcie: No bus range found for /axi/pcie@120000, using [bus 00-ff]
[ 0.993673] brcm-pcie 1000120000.pcie: MEM 0x1f00000000..0x1ffffffffb -> 0x0000000000
[ 0.993685] brcm-pcie 1000120000.pcie: MEM 0x1c00000000..0x1effffffff -> 0x0400000000
[ 0.993708] brcm-pcie 1000120000.pcie: IB MEM 0x1f00000000..0x1f003fffff -> 0x0000000000
[ 0.993721] brcm-pcie 1000120000.pcie: IB MEM 0x0000000000..0x0fffffffff -> 0x1000000000
[ 0.994854] brcm-pcie 1000120000.pcie: Forcing gen 2
[ 0.994938] brcm-pcie 1000120000.pcie: PCI host bridge to bus 0000:00
[ 1.100577] brcm-pcie 1000120000.pcie: link up, 5.0 GT/s PCIe x4 (!SSC)
[ 1.112778] pcieport 0000:00:00.0: enabling device (0000 -> 0002)
[ 1.112839] pcieport 0000:00:00.0: PME: Signaling with IRQ 44
[ 1.112973] pcieport 0000:00:00.0: AER: enabled with IRQ 44
:~$


$ [B]sudo rpi-eeprom-update
[/B]BOOTLOADER: up to date
CURRENT: **Wed Jan 24** 12:16:01 UTC 2024 (1706098561)
LATEST: Mon Sep 25 10:44:03 UTC 2023 (1695638643)
RELEASE: default (/lib/firmware/raspberrypi/bootloader-2712/default)
Use raspi-config to change the release.
:~$




:~$ [B]sudo rpi-eeprom-config
[/B][all]
BOOT_UART=1
POWER_OFF_ON_HALT=0
[B]PCIE_PROBE=1
[/B]BOOT_ORDER=0xf41
:~$


:~$ [B]cat /boot/firmware/config.txt | tail
[/B]

# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2


# Enable the PCIe External connector.
[B]dtparam=pciex1
[/B]# This line is an alias for above (you can use either/or to enable the port).
#dtparam=nvme
#dtparam=pciex1_gen=2
:~$


:~$ **sudo apt update**
Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) mantic InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) mantic-updates InRelease
Ign:3 [https://download.webmin.com/download/newkey/repository](https://download.webmin.com/download/newkey/repository) stable InRelease
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) mantic-security InRelease
Hit:5 [https://download.webmin.com/download/newkey/repository](https://download.webmin.com/download/newkey/repository) stable Release
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
[B]All packages are up to date.
[/B]:~$

---

### Post by MAFoElffen on 2024-01-29
I went to Geekworm's support page and found this:
> 
**[COLOR=#ff2a00][Important Notes][/COLOR]**

 NVMe SSD Incompatibility List:

 We recommend avoiding the following NVMe SSD drives which is equipped with a **Phison controller** due to their proven incompatibility:
 
[LIST]
[*]WD Blue SN550/SN580 series 
[*]WD Green SN350 series 
[*]WD Black SN850 series 
[*]Other NVMe SSD drivers equipped with the same **Phison controller** 
[/LIST]
 These specific models have demonstrated compatibility issues, and it  is advisable to avoid them when considering NVMe SSD options for the  X10xx series NVMe shield.

 We hope the Raspberry Pi Foundation will resolve this issue soon.
 Also note:
 
[LIST]
[*]Compatible with M.2 **NVMe** SSDs 
[*] **Not** compatible with M.2 SATA SSDs, M.2 PCIe AHCI SSDs, or other M.2 non-NVMe devices 
[*]Older NVMe drives with less efficient flash media may not perform as well as newer drives 
[*]New NVMe SSDs are not partitioned and will need to be both  partitioned and formatted when first connected to the Raspberry Pi  before they will be accessed in the Explorer. 
[/LIST]

Being Phizon is one of the largest manufacturers of NVMe Controllers in the industry ([https://blocksandfiles.com/2023/06/12/phison-largest-ssd-supplier-no-one-knows-about/](https://blocksandfiles.com/2023/06/12/phison-largest-ssd-supplier-no-one-knows-about/)), that list also includes Seagate, Micron, Crucial, Kioxia/WD, Samsung, SK hynix/Solidigm, YMTC, and Kingston. A shorter list may be what NVMe drives are actually compatible with that board. (Sorry for that news.)

Since KingSpec is a Chinese knockoff, it may also be on that list under their sticker. They don't say who's controller they use. Nor does their documents and faq.

I suspect maybe there may be a compatibility problem between the GeekWorm Adapter board, and the KingSpec NVMe drive. Either contact GeekWorm to check if they know that drive will work with that drive, or ask KingSpec which controller chip they use on your drive... If it is a Phizon chip.

But... It may have a Maxio MAP1000 series controller. I'm not sure.

I think are really only 4 major controller chip manufacturers: Phison, Silicon Motion, InnoGrit and Maxio.

---

