---
title: "Card reader not working. Ubuntu 20.04. Lenovo P53 laptop."
date: 2020-08-13
forum: Hardware
---

### Post by jbl-at-mydefence on 2020-08-13
No device is mounted when inserting SD card into card reader. 

I'm running Ubuntu 20.04 on a Lenovo P53 laptop

Card reader is enabled in BIOS.

Card reader seems to be found by the system
```

&#10095; sudo lspci -s 54:00.0 -v
54:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
        Subsystem: Lenovo RTS525A PCI Express Card Reader
        Flags: fast devsel, IRQ 19
        Memory at ee100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [80] Power Management version 3
        Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [b0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [148] Device Serial Number 00-00-00-01-00-4c-e0-00
        Capabilities: [158] Latency Tolerance Reporting
        Capabilities: [160] L1 PM Substates
        Kernel modules: rtsx_pci

&#10095; dmesg | grep 54:00.0 
[    0.443484] pci 0000:54:00.0: [10ec:525a] type 00 class 0xff0000
[    0.443515] pci 0000:54:00.0: reg 0x14: [mem 0xee100000-0xee100fff]
[    0.443624] pci 0000:54:00.0: supports D1 D2
[    0.443626] pci 0000:54:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.700407] pci 0000:54:00.0: Adding to iommu group 10
[    0.700410] pci 0000:54:00.0: DMAR: Device uses a private identity domain.
[    0.969659] rtsx_pci 0000:54:00.0: enabling device (0000 -> 0002)
[    0.970438] rtsx_pci 0000:54:00.0: DMAR: 32bit DMA uses non-identity mapping

&#10095; dmesg | grep rtsx_pci
[    0.969659] rtsx_pci 0000:54:00.0: enabling device (0000 -> 0002)
[    0.970438] rtsx_pci 0000:54:00.0: DMAR: 32bit DMA uses non-identity mapping

&#10095; dmesg | grep mmc

&#10095; lsmod | grep rts     
rtsx_pci               73728  0

&#10095; 

```

However, nothing happens when inserting/removing an SD card in/from the reader. No new entries in dmesg output. I was expecting an mmc block device to be mounted.

Has anyone gotten the card reader in a Lenovo P53 to work on Ubuntu 20.04?

/Jesper

---

### Post by tea for one on 2020-08-13
I do not have your laptop but I have an [COLOR="#0000CD"]unusual[/COLOR] suggestion for you to consider.

A friend of mine has an Intel NUC6AYH which has a Realtek RTS5229 PCI Express Card Reader (not exactly your device but similar)

The card reader recognised SD Cards during a **live** session using Ubuntu 20.04.

Ubuntu 20.04 was installed in UEFI mode with GPT and only UEFI boot mode was checked in the set-up firmware

The SD Card Reader did not recognise any cards after installation to the internal SSD.

Now, here is the ridiculous suggestion:-

We went into the UEFI firmware and enabled **Legacy boot mode together with UEFI boot mode**.

We booted Ubuntu 20.04 in UEFI mode and the SD Card Reader worked.

Updating the Intel BIOS/UEFI firmware has not improved the situation so my friend simply leaves the Legacy boot mode activated so that the Card Reader works.

We also double checked with other Linux distros such as PCLinuxOS and Xubuntu - same problem and same solution.

It's madness, I know............but worth a shot.

---

### Post by jbl-at-mydefence on 2020-08-14
Thanks, this pushed me in the right direction. To enable legacy boot Kernel DMA protection needs to be disabled. As it turns out this is the culprit. 

Only Kernel DMA protection needs to be disabled to get the card reader working on my setup.

In the BIOS go to Security -> Virtualization menu and disable Kernel DMA protection.

Once this is disabled the security level on the Thunderbolt port is set to "User Authorization", which means that devices connected through e.g. a Thunderbolt dock (keyboard, mouse, ...) needs to be authorized before they work. To accept all devices when they appear insert the following in /etc/udev/99-local.rules:

```
[FONT=&amp]ACTION=="add", SUBSYSTEM=="thunderbolt", ATTR{authorized}=="0", ATTR{authorized}="1"[/FONT]
```

Or set the Thunderbolt security level to "None" in BIOS (Config->Thunderbolt menu).

Both methods are essentially the same. They bypass the security functions and leave the PC vulnerable to DMA attacks. Read more on authorizing individual devices on [https://www.kernel.org/doc/html/latest/admin-guide/thunderbolt.html](https://www.kernel.org/doc/html/latest/admin-guide/thunderbolt.html)

---

### Post by tea for one on 2020-08-14
I'm surprised and delighted that my comments helped you find the correct solution for your PC.

Unfortunately, for my friend, the UEFI/BIOS firmware on the Intel NUC6AYH is less sophisticated than yours and there isn't a dedicated field for [COLOR="#000080"]disable Kernel DMA protection[/COLOR]

The only similar field is to enable/disable **Intel VT for Directed I/O (VT-d)**.

We tried both enable and disable settings but no joy.

The Card Reader would only work on this NUC if **Legacy Boot Mode** is enabled.

Anyway, it's only a minor irritant in a cheap 'n' cheerful device.

---

### Post by hxhlb on 2021-01-04
I found a method, although it is more troublesome, but there is no need to disable Kernel DMA protection.


After entering the system, open the terminal, run "lspci -v | grep Card" , you can see the output "Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader", then, unplug the SDCard, insert it, card reader working now.

---

### Post by hardiebotha on 2021-02-01
> **hxhlb said:**
> I found a method, although it is more troublesome, but there is no need to disable Kernel DMA protection.


After entering the system, open the terminal, run "lspci -v | grep Card" , you can see the output "Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader", then, unplug the SDCard, insert it, card reader working now.

I can confirm this worked for me - Lenovo P72 running 20.04
Dolphin does not update when removing the SD card either - running ```
"lspci -v | grep Card"
```  after removing the card is necessary to remove it from Dolphin.
Change the card's physical state before doing this, i.e. 
[LIST]
[*]Insert the card and run to command above to make it show up.
[*]Mount, access files and unmount.
[*]Eject and run the command above again to update the fact that it is no longer in the machine.
[/LIST]

---

