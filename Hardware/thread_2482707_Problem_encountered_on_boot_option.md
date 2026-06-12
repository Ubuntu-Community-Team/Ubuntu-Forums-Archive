---
title: "Problem encountered on boot option"
date: 2023-01-09
forum: Hardware
---

### Post by satimis on 2023-01-09
Hi all,

Ubuntu 22.04 desktop

I have 2 PCIe 3.0 Nvme SSDs installed on PC

PCIe 3.0 Nvme SSD-1 - 1TB (installed on M2_1(SOCKET3)
PCIe 3.0 Nvme SSD-2 - 2TB (installed on M2_2(SOCKET3)

BIOS can detect both.
But on Boot Option #1 - PCIe 3.0 Nvme SSD-2 can't be found.  Only PCIe 3.0 Nvme SSD-1
PCIe 3.0 Nvme SSD-2 can be found on Option #2 / #3 etc

$ cat /sys/devices/virtual/dmi/id/board_{vendor,name,version}```

ASUSTeK COMPUTER INC.
PRIME X570-P
Rev X.0x

```

Motherboard drawings are attached.

Pls advise how to fix the problem.  Thanks

Regards

Photos
1. screenshot_mobo_drawing.png
2. screenshot_mobo_socket3.png

---

### Post by TheFu on 2023-01-11
I don't have that specific board, but I happened to be in my Asus ROG B450 BIOS yesterday due to a CPU upgrade and saw that my SSD wasn't in the boot list. Only the spinning rust HDDs were listed.  At the time, there were 3 storage devices connected:
* Micron 1100 SATA-SSD m.2 format
* Hitachi 500GB internal SATA HDD (this doesn't have any boot files on it)
* WD Blue 250GB external USB2 HDD (this was accidentally powered on, never used for boot)

The Micron wasn't in the list for boot drives.  Just below that option on the same BIOS page were 2 boot parameter options.  I opened the 1st and saw the Micron listed as 2nd there.  I swapped the order in that page and backed out. Not the main boot order page showed the Micron SSD.  

Sorry, I don't have any NVMe in that system, so I don't know what, that does.  On another system, also with the exact same MB and BIOS version, I have a Samsung 970 EVO 500G NVMe SSD, but I can't reboot that and look at the settings until the weekend. It is the boot device for the system.

If you boot into a "Try Ubuntu" flash drive, does the system see all the storage?  Is it just a boot issue or is it missing completely regardless of the OS?

Beware, UUIDs in cloned disks confuse Linux systems, so if you cloned any storage and both are still connected, unexpected things are likely, usually not what you want.  Be certain to check the UUIDs are different for all connected storage.

And the motherboard manual might have some hints about specific supported storage configs.  My Asus MB does odd things when an x16 PCIe GPU and m.2 NVMe and m.2 SATA storage connected.  Be certain you find the 2-3 places in the manual which explains those limitations.  If you CPU is an APU (CPU + iGPU), there are other restrictions.  Just because there is a slot, that doesn't mean it can be used for some mix of storage and PCIe devices.

---

### Post by satimis on 2023-01-11
> **TheFu said:**
> I don't have that specific board, but I happened to be in my Asus ROG B450 BIOS yesterday due to a CPU upgrade and saw that my SSD wasn't in the boot list. Only the spinning rust HDDs were listed.  At the time, there were 3 storage devices connected:
* Micron 1100 SATA-SSD m.2 format
* Hitachi 500GB internal SATA HDD (this doesn't have any boot files on it)
* WD Blue 250GB external USB2 HDD (this was accidentally powered on, never used for boot)
......
..... 
Hi TheFu,

Lot of thanks for your detailed advice and for your time spent to help me as well.

I already solved my problem as follows;
1) Boot into BIOS
It detects all drives connected in the PC
2) On Boot window
There are 7 boot options
Option-1
Option-2
Option-3
Option-4
Option-5
Option-6
Option-7

Option-1 and Option-2 can't detect
PCIe 3.0 Nvme SSD-2 - 2TB (installed on M2_2(SOCKET3)
but detect the rest drives

Option-3 detect;
PCIe 3.0 Nvme SSD-2 - 2TB (installed on M2_2(SOCKET3)
including other drives

It is very strange to me.

3) I disable Option-1 and Option-2

and on Option-3 I select;
PCIe 3.0 Nvme SSD-2 - 2TB (installed on M2_2(SOCKET3)

4) Save and reboot BIOS

5) Now this time Option-1 detects;
PCIe 3.0 Nvme SSD-2 - 2TB (installed on M2_2(SOCKET3)

I solved the problem in this way.  It looks to me quite strange.

Thanks and Regards

---

