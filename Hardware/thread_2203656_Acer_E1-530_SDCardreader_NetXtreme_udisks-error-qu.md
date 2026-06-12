---
title: "Acer E1-530 SDCardreader NetXtreme udisks-error-quark,0"
date: 2014-02-04
forum: Hardware
---

### Post by jauntyjackalope2 on 2014-02-04
**[COLOR=#ff0000]edit: [/COLOR]**[COLOR=#000000]If this affects someone else (simply another buyer of this acer book who runs ubuntu linux on it ) here is the bugreport :[/COLOR][COLOR=#ff0000]
[/COLOR][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1279796](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1279796)

Hello Community,

i have a new Acer Aspire Laptop and the **Sd-cardreader cant write to SD Cards**. I cant format them nor write Images, just little Files < 180mb work.
[COLOR=#ff0000]
**Error**:[/COLOR]**udisks-error-quark,0** (is what Palimpsest [Disk Utility] gives me on 13.10)

**OS**:Ubuntu 12.04.4 Precise Pangolin Linux box 3.11.0-15-generic #25~precise1-Ubuntu SMP i686 i686 i386 GNU/Linux
**Notebook**:[FONT=Verdana][SIZE=2]Acer Aspire E1-530-21174G50Mnkk NX.MEQEG.004 Linux[/SIZE][/FONT]
**Cardreader**:Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 01) (prog-if 01)

**Dmesg:**
```
[  532.477831] Buffer I/O error on device mmcblk0p1, logical block 393
[  532.477833] lost page write due to I/O error on mmcblk0p1
[  542.490457] mmc0: Timeout waiting for hardware interrupt.
```

**I have found this Patch (?) here which may help :**
[https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a](https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a)

But i have **no idea how to applie** it, any hints would be wonderfull** (-:**

---

