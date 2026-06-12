---
title: "TI 5-in-1 SmartMedia card reader not mounting for HP Compaq nc6120 in Karmic 9.10"
date: 2009-12-17
forum: Hardware
---

### Post by Ace42 on 2009-12-17
Hello all, I'm having a problem with my HP laptop:
The built-in SmartMedia card reader doesn't auto-mount; nor generate a mountable devices under /dev or /media.  HOWEVER, dmesg DOES indicate that the machine detects the card being inserted
{**[ 3990.536089] tifm_core: SmartMedia/xD card detected in socket 0:2**}
and removed
{**[ 3988.654843] tifm0 : demand removing card from socket 0:2**}
which is accompanied by the card reader's indicator led flashing.

My guess (as a linux user of about a week now, and thus rather ill-informed) is that the mmc_block module isn't doing its job as an intermediary of some sort between the hardware driver and the OS.

The fellows in #ubuntu-beginners-help had no clue and asked me to make a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/493328") which has received no recognition whatsoever on this issue, and there are many similar bug reports going back 3 years on launchpad.

I have tried various legacy fixes (starting with double checking that modules are loaded; then [using the setpci trick to force SD mode]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/91429"); then trying to[ recompile the kernel with different .ko files]("http://ubuntuforums.org/showthread.php?t=420721"), which resulted in me pulling my hair out when depmod broke the module compatibility, modprobe saying the modules were incompatible, and me having to reformat the whole drive).

I really need some advice on some contemporary fixes I could try.

Here's the information I am working with:

$ uname -r
2.6.31-16-generic

$ dmesg | grep tifm
[    9.221246] tifm_7xx1 0000:02:06.3: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    9.288034] tifm_core: SmartMedia/xD card detected in socket 0:2
[ 3858.117977] tifm0 : demand removing card from socket 0:2

$ dmesg | grep sdhci
[    8.238047] sdhci: Secure Digital Host Controller Interface driver
[    8.238050] sdhci: Copyright(c) Pierre Ossman
[    8.240447] sdhci-pci 0000:02:06.4: SDHCI controller found [104c:8034] (rev 0)
[    8.240481] sdhci-pci 0000:02:06.4: PCI INT D -> GSI 20 (level, low) -> IRQ 20

$ dmesg | grep mmc
[    1.143799] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    8.240556] Registered led device: mmc0::
[    8.240598] mmc0: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.240635] Registered led device: mmc1::
[    8.240658] mmc1: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.240695] Registered led device: mmc2::
[    8.240718] mmc2: SDHCI controller on PCI [0000:02:06.4] using PIO

$ lsmod | grep tifm
tifm_sd                 9252  0 
tifm_7xx1             5372  0 
tifm_core              7832  2 tifm_sd,tifm_7xx1

$ lsmod | grep sd
tifm_sd                 9252  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
tifm_core               7832  2 tifm_sd,tifm_7xx1
led_class               4096  1 sdhci

$ lsmod | grep mmc
mmc_block              10592  0 

$ lspci | grep Texas
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller

$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9546    76678213+  83  Linux
/dev/sda2            9547        9729     1469947+   5  Extended
/dev/sda5            9547        9729     1469916   82  Linux swap / Solaris

**SDA2 is my encrypted home-folder** [edit:  Prolly hibernation partition in retrospect]** I believe, the memory card inserted is 16mb, not 1gb.**

Thanks.

---

### Post by IcarusR on 2009-12-18
If I remember correctly these card readers do not work with xD cards under linux.

---

### Post by Ace42 on 2009-12-18
> **IcarusR said:**
> If I remember correctly these card readers do not work with xD cards under linux.

Technically the card I am using is an SM (SmartMedia) card, which is similar but distinct from the xD format.  I am guessing it's not supported, though.  Which bites.

---

### Post by isaacd on 2010-03-29
Hello.

My system:
ubuntu 9.10
efilm pocket reader with a smart media card of 32mb

My problem: I can not access images from the card.

What happens when I insert the card:
-It does not mount
-It is not shown in /media as a folder at all
-The only trace of it (to my knowledge) is that when I go into Places >> Computer, I see something called:

SCM Microsystems Inc. eUSB SmartMedia Adapter

When I double click it, nothing happens, and there is no options to mount it.

Thanks.

Isaac.

---

