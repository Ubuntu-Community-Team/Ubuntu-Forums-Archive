---
title: "Curtiss Wright 5453J block device errors"
date: 2018-04-11
forum: Hardware
---

### Post by vanbynight on 2018-04-11
I made the mistake of buying some NVRAM cards off ebay because the price was right. They appear to be from a EMC SAN. According to the listing they're both Curtiss Wright 5453J and there are some markings on the PCB that confirm this. It's a battery backed DRAM card with 1GB of usable space, it is supposed to appear as a block device to the operating system and is basically a small NVME SSD that wipes its storage if it loses power for more than a day. In the past they were mostly used for external journals for files systems before SSD storage became affordable. 




The problem I'm encountering is when I tried booting up into kernel 4.4.0 I received an error from the umem driver that the magic number didn't match. I looked into this error and found that someone made a patch for ubuntu 14.04 running kernel 3.13. So I installed ubuntu 14.04.5 and patched the umem.ko driver and now kernel 3.13 tries to initalize the devices but I receive memory access errors. 


This driver looks like it was last patched in 2002 according to the source files so I'm guessing there was a compatibility problem between kernel 2.6 and later kernels that wasn't fixed. It also was written for PCI and PCI-X (maybe older interfaces too) so I would think it should work using PCIE.


this is the patch I applied originally from [https://patchwork.kernel.org/patch/8180661/](https://patchwork.kernel.org/patch/8180661/)
```

Comments
Dr. Net! - Eugen Rieck - Feb. 1, 2016, 3:33 p.m.
From: Eugen Rieck <eugen@drnet.at>


Allow for multiple magic numbers per model and include the magic number
for the PCIe-based 5453CN, that shares the device id of the older
PCI-X-based 5425CN.


Signed-off-by: Eugen Rieck <eugen@drnet.at>
---
The umem driver for Micro Memory (now Curtiss-Wright) NVRAM cards relied
on a unique magic number for each PCI device id. Newer cards violate this
and were thus rejected by the driver.
Developed for 3.13.0 (Ubuntu 14.04,  ubuntu 3.13.0-76-generic), but merges
cleanly into current (4.5-rc2) as the driver is old and largely unchanged.


 umem.c |   29 +++++++++++++++++++++++------
 umem.h |    2 ++
 2 files changed, 25 insertions(+), 6 deletions(-)
Patch
--- drivers/block/umem.c.orig    2016-02-01 14:51:07.463944676 +0100
+++ drivers/block/umem.c    2016-02-01 15:03:52.815934423 +0100
@@ -32,6 +32,8 @@ 
  * 17May2002:NeilBrown   - remove init_mem initialisation.  Instead detect
  *             - a sequence of writes that cover the card, and
  *             - set initialised bit then.
+ * 01Feb2016:Eugen Rieck - allow multiple magic numbers per pci id to
+ *               acommodate newer models
  */
 
 #undef DEBUG    /* #define DEBUG if you want debugging info (pr_debug) */
@@ -799,6 +801,9 @@ 
     unsigned long    csr_base;
     unsigned long    csr_len;
     int        magic_number;
+    int        magic_numbers[MAGIC_NUMBERS_PER_DEV];
+    int         magic_number_ok = 0;
+    int         i;
     static int    printed_version;
 
     if (!printed_version++)
@@ -850,27 +855,39 @@ 
     switch (card->dev->device) {
     case 0x5415:
         card->flags |= UM_FLAG_NO_BYTE_STATUS | UM_FLAG_NO_BATTREG;
-        magic_number = 0x59;
+        magic_numbers[0] = 0x59;
+        magic_numbers[1] = 0x100;
         break;
 
     case 0x5425:
         card->flags |= UM_FLAG_NO_BYTE_STATUS;
-        magic_number = 0x5C;
+        magic_numbers[0] = 0x5C;
+        magic_numbers[1] = 0x5E;
+        magic_numbers[2] = 0x100;
         break;
 
     case 0x6155:
         card->flags |= UM_FLAG_NO_BYTE_STATUS |
                 UM_FLAG_NO_BATTREG | UM_FLAG_NO_BATT;
-        magic_number = 0x99;
+        magic_numbers[0] = 0x99;
+        magic_numbers[1] = 0x100;
         break;
 
     default:
-        magic_number = 0x100;
+        magic_numbers[0] = 0x100;
         break;
     }
 
-    if (readb(card->csr_remap + MEMCTRLSTATUS_MAGIC) != magic_number) {
-        dev_printk(KERN_ERR, &card->dev->dev, "Magic number invalid\n");
+    magic_number = readb(card->csr_remap + MEMCTRLSTATUS_MAGIC);
+    for (i = 0; i < MAGIC_NUMBERS_PER_DEV; i++) {
+        if (magic_numbers[i] == magic_number) {
+            magic_number_ok = 1;
+            break;
+        }
+        if (magic_numbers[i] >= 0x100) break;
+    }
+    if (!magic_number_ok) {
+        dev_printk(KERN_ERR, &card->dev->dev, "Magic number 0x%02x invalid for device 0x%04x\n", magic_number, card->dev->device);
         ret = -ENOMEM;
         goto failed_magic;
     }


--- drivers/block/umem.h.orig    2016-02-01 14:51:16.055944561 +0100
+++ drivers/block/umem.h    2016-02-01 14:47:38.463947477 +0100
@@ -15,6 +15,8 @@ 
 
 #define IRQ_TIMEOUT (1 * HZ)
 
+#define MAGIC_NUMBERS_PER_DEV    2
+
 /* CSR register definition */
 #define MEMCTRLSTATUS_MAGIC    0x00
 #define  MM_MAGIC_VALUE        (unsigned char)0x59



```


I rebuilt the module and now I can see the devices as /dev/umem[a,b]


lsblk reports the following


```

sda      8:0    0    20G  0 disk
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0  19.5G  0 part /
sdb      8:16   0 524.5G  0 disk
&#9492;&#9472;sdb1   8:17   0 524.5G  0 part /usr
umema  251:0    0     1G  0 disk
umemb  251:64   0     1G  0 disk

```


However dmesg reports all this garbage on boot


```

root@ubuntu-test:/home/cscott# dmesg | grep umem
[    5.409505] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409509] umem 0000:05:00.0: I/O error on sector 16/4096
[    5.409511] umem 0000:05:00.0: DMAstat -
[    5.409552] umem 0000:05:00.0: DMAstat -
[    5.409555] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409556] umem 0000:05:00.0: Multi-bit EDC error
[    5.409558] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[    5.409560] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409564] umem 0000:05:00.0: I/O error on sector 0/4096
[    5.409565] umem 0000:05:00.0: DMAstat -
[    5.409604] umem 0000:05:00.0: DMAstat -
[    5.409607] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409608] umem 0000:05:00.0: Multi-bit EDC error
[    5.409610] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[    5.409612] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409615] umem 0000:05:00.0: I/O error on sector 0/4096
[    5.409616] umem 0000:05:00.0: DMAstat -
[    5.409659] umem 0000:05:00.0: DMAstat -
[    5.409662] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409663] umem 0000:05:00.0: Multi-bit EDC error
[    5.409665] umem 0000:05:00.0: Fault Address 0x0000001f00, Fault Data 0x116c30a4425832b1
[    5.409667] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409670] umem 0000:05:00.0: I/O error on sector 8/4096
[    5.409671] umem 0000:05:00.0: DMAstat -
[    5.409712] umem 0000:05:00.0: DMAstat -
[    5.409715] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409716] umem 0000:05:00.0: Multi-bit EDC error
[    5.409718] umem 0000:05:00.0: Fault Address 0x0000002f00, Fault Data 0x10f4104798a000f0
[    5.409719] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409729] umem 0000:05:00.0: I/O error on sector 16/4096
[    5.409731] umem 0000:05:00.0: DMAstat -
[    5.409781] umem 0000:05:00.0: DMAstat -
[    5.409784] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409785] umem 0000:05:00.0: Multi-bit EDC error
[    5.409787] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[    5.409789] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409792] umem 0000:05:00.0: I/O error on sector 0/4096
[    5.409794] umem 0000:05:00.0: DMAstat -
[    5.409833] umem 0000:05:00.0: DMAstat -
[    5.409836] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409838] umem 0000:05:00.0: Multi-bit EDC error
[    5.409840] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[    5.409841] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409845] umem 0000:05:00.0: I/O error on sector 0/4096
[    5.409846] umem 0000:05:00.0: DMAstat -
[    5.409888] umem 0000:05:00.0: DMAstat -
[    5.409891] umem 0000:05:00.0: Memory access error detected (err count 0)
[    5.409892] umem 0000:05:00.0: Multi-bit EDC error
[    5.409895] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[    5.409896] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[    5.409900] umem 0000:05:00.0: I/O error on sector 0/4096
[    5.409901] umem 0000:05:00.0: DMAstat -
[    5.409939] umem 0000:05:00.0: DMAstat -


and so on and so forth


[   21.878134] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878136] umem 0000:05:00.0: Multi-bit EDC error
[   21.878140] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878142] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878148] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878150] umem 0000:05:00.0: DMAstat -
[   21.878195] umem 0000:05:00.0: DMAstat -
[   21.878199] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878201] umem 0000:05:00.0: Multi-bit EDC error
[   21.878205] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878207] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878213] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878215] umem 0000:05:00.0: DMAstat -
[   21.878262] umem 0000:05:00.0: DMAstat -
[   21.878266] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878268] umem 0000:05:00.0: Multi-bit EDC error
[   21.878272] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878275] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878280] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878282] umem 0000:05:00.0: DMAstat -
[   21.878327] umem 0000:05:00.0: DMAstat -
[   21.878332] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878334] umem 0000:05:00.0: Multi-bit EDC error
[   21.878337] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878340] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878345] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878347] umem 0000:05:00.0: DMAstat -
[   21.878396] umem 0000:05:00.0: DMAstat -
[   21.878400] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878402] umem 0000:05:00.0: Multi-bit EDC error
[   21.878406] umem 0000:05:00.0: Fault Address 0x0000003f00, Fault Data 0x620c20a3b81580a0
[   21.878409] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878414] umem 0000:05:00.0: I/O error on sector 24/4096
[   21.878416] umem 0000:05:00.0: DMAstat -
[   21.878462] umem 0000:05:00.0: DMAstat -
[   21.878467] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878469] umem 0000:05:00.0: Multi-bit EDC error
[   21.878473] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878475] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878481] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878483] umem 0000:05:00.0: DMAstat -
[   21.878528] umem 0000:05:00.0: DMAstat -
[   21.878532] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878535] umem 0000:05:00.0: Multi-bit EDC error
[   21.878538] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878541] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878545] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878548] umem 0000:05:00.0: DMAstat -
[   21.878593] umem 0000:05:00.0: DMAstat -
[   21.878598] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878600] umem 0000:05:00.0: Multi-bit EDC error
[   21.878604] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878607] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878612] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878614] umem 0000:05:00.0: DMAstat -
[   21.878658] umem 0000:05:00.0: DMAstat -
[   21.878662] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878665] umem 0000:05:00.0: Multi-bit EDC error
[   21.878668] umem 0000:05:00.0: Fault Address 0x0000007f00, Fault Data 0xe5754bb094460c14
[   21.878671] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878676] umem 0000:05:00.0: I/O error on sector 56/4096
[   21.878678] umem 0000:05:00.0: DMAstat -
[   21.878723] umem 0000:05:00.0: DMAstat -
[   21.878728] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878730] umem 0000:05:00.0: Multi-bit EDC error
[   21.878734] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878737] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878742] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878744] umem 0000:05:00.0: DMAstat -
[   21.878788] umem 0000:05:00.0: DMAstat -
[   21.878792] umem 0000:05:00.0: Memory access error detected (err count 0)
[   21.878795] umem 0000:05:00.0: Multi-bit EDC error
[   21.878798] umem 0000:05:00.0: Fault Address 0x0000000f00, Fault Data 0xf6ee04e64a340280
[   21.878800] umem 0000:05:00.0: Fault Check 0x00, Fault Syndrome 0x00
[   21.878805] umem 0000:05:00.0: I/O error on sector 0/4096
[   21.878807] umem 0000:05:00.0: DMAstat -

```


I get these error when I try to access either one of the block devices for a read/write operation


Right now they are sharing IRQs with other devices I'm not sure if that matters but in the bios I have them mapped to IRQs that have some USB peripherals too.


and some more debug info


output of ```
 lscpi -nnk 
```


```



04:00.0 Memory controller [0580]: Micro Memory MM-5425CN PCI 64/66 Memory Module with Battery Backup [1332:5425] (rev 08)
        Subsystem: Micro Memory Device [1332:5453]
        Kernel driver in use: umem
05:00.0 Memory controller [0580]: Micro Memory MM-5425CN PCI 64/66 Memory Module with Battery Backup [1332:5425] (rev 08)
        Subsystem: Micro Memory Device [1332:5453]

```


I'm not sure if it matters but this is reporting that they are 5425-CN devices which are considerably older than the 5453J


```

root@ubuntu-test:/# uname -a
Linux ubuntu-test 3.13.0-144-generic #193-Ubuntu SMP Thu Mar 15 17:03:53 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```


From what I understand these were used in an EMC or Nutanix storage server of some sort as an external journal device. I've used older versions of these cards before for external journals and they have been quite reliable along with providing performance that is up there with the new NVME storage technology. I'm not expecting a miracle but if someone has trouble shooting advice for this type of error I'll gladly take it. I have coded a little before and can try and fix the driver if someone can point me in the right direction of what should be fixed.

---

