---
title: "installing a video card for the first time (GeForce 9600GT)"
date: 2012-04-19
forum: Hardware
---

### Post by hopefulkayaker on 2012-04-19
I installed a video card once with Windows Vista, but this is my first time doing it with Ubuntu. I know that Ubuntu is known for being very good at automatically finding the correct drivers, but is there anything I should know or do before installing my card? The card came with a disc, but only has WinXP, Vista, and Win7 drivers, unsurprisingly.

---

### Post by oldfred on 2012-04-19
You will need nomodeset on liveCD or USB and first boot. After you install the nVidia drivers that pops up then you will have no issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

### Post by MonkeyPaw on 2012-04-19
> **oldfred said:**
> You will need nomodeset on liveCD or USB and first boot. After you install the nVidia drivers that pops up then you will have no issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Shouldn't he be able to disable any proprietary drivers and then install the card? When I went from my ATI integrated graphics to a standalone card, that's all I did. It booted into the generic driver, and then I installed the nVidia driver. Does that not always lead to predictable results?

---

### Post by oldfred on 2012-04-19
If you were able to boot that is great. And once the nVidia driver is installed then you should not have any issues.

I have nomodeset built into all my new system boots, so I do not even know if it works or not without nomodeset. But we still see a lot of users with video issues and nomodeset solves the issue on more than just nVidia cards.

---

### Post by efflandt on 2012-04-20
I don't know about 11.04 (which I only ran during development), but 11.10 seems to need **nomodeset** when using nvidia drivers, whereas, 10.10 did not, even when using exact same nvidia driver version.

I think in the past nouveau was blacklisted when using nvidia drivers, but 11.10 seems to use both nouveau and nvidia, which work fine as modules (nomodeset), but not with default kernel mode setting.

```
01:00.0 VGA compatible controller: nVidia Corporation GF116 [GeForce GTX 550 Ti] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 1556
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fbc80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
```

---

