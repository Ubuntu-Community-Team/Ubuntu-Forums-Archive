---
title: "Intel Tiger Lake GSPI + F-RAM issue"
date: 2024-07-29
forum: Hardware
---

### Post by dlp2501 on 2024-07-29
[LEFT]Hi,

[/LEFT]
  [LEFT]I have a board with Intel Tiger Lake CPU, and its GSPI#0 is connected to a Cypress F-RAM device (CY15B104Q).[/LEFT]
 [LEFT]I'm having trouble accessing this F-RAM from Ubuntu (using version 23.10).[/LEFT]
  [LEFT]From reading up on Cypress F-RAM, my understanding is that it should behave the same as a normal spi-nor device:[/LEFT]
 [LEFT][F-RAM  Support under Linux (infineon.com)]("https://community.infineon.com/t5/Knowledge-Base-Articles/F-RAM-Support-under-Linux/ta-p/248959?emcs_t=S2h8ZW1haWx8dG9waWNfc3Vic2NyaXB0aW9ufExZWVdGUldGTk1WSVowfDgxMTM1N3xTVUJTQ1JJUFRJT05TfGhL#.")
[/LEFT]
 [LEFT]However  I noticed that in Linux kernel 6.5: drivers/mtd/spi-nor/spansion.c  source file, there is an entry specifically only for CY15V104QN device:

[/LEFT]
  ```
[LEFT]{ "cy15x104q",  INFO6(0x042cc2, 0x7f7f7f, 512 * 1024, 1)
[/LEFT]
 [LEFT]FLAGS(SPI_NOR_NO_ERASE) },[/LEFT]

```

 [LEFT]I have tried adding my device as a new entry:
[/LEFT]
 [LEFT] 
[/LEFT]
 ```
[LEFT]{ "cy15b104q",  INFO6(0x0826c2, 0x7f7f7f, 512 * 1024, 1)
[/LEFT]
 [LEFT]FLAGS(SPI_NOR_NO_ERASE) },
[/LEFT]

```  

[LEFT]Then I built the spi-nor module and loaded it, but didn't notice any changes.
[/LEFT]
  [LEFT]Looking at recognized SPI and MTD devices, I only see "spi0.0" and "mtd0" which is the regular SPI connected to BIOS Flash:

[/LEFT]
  ```

[LEFT]$ ls /dev/mtd*
[/LEFT]
 [LEFT]/dev/mtd0  /dev/mtd0ro[/LEFT]
  [LEFT]$ ls /sys/bus/spi/devices/[/LEFT]
 [LEFT]spi0.0[/LEFT]
  [LEFT]$ cat /sys/bus/spi/devices/spi0.0/spi-nor/partname [/LEFT]
 [LEFT]n25q256a
[/LEFT]
  [LEFT]$ cat /proc/mtd[/LEFT]
 [LEFT]dev:    size   erasesize  name[/LEFT]
 [LEFT]mtd0: 02000000 00001000 "BIOS"
[/LEFT]

```   

[LEFT]My suspicion is that the GSPI controller is not functioning as needed.[/LEFT]
 [LEFT]However it seems to be recognised correctly on the PCI bus and has the appropriate driver attached to it:

[/LEFT]
  ```
[LEFT]$ sudo lspci -vv -s 1e.2
[/LEFT]
 [LEFT]00:1e.2 Serial bus controller: Intel Corporation Device a0aa (rev 20)[/LEFT]
 [LEFT]    Subsystem: Intel Corporation Device 7270[/LEFT]
 [LEFT]    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/LEFT]
 [LEFT]    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/LEFT]
 [LEFT]    Latency: 0[/LEFT]
 [LEFT]    Interrupt: pin C routed to IRQ 255[/LEFT]
 [LEFT]    Region 0: Memory at 81741000 (64-bit, non-prefetchable) [size=4K][/LEFT]
 [LEFT]    Capabilities: [80] Power Management version 3[/LEFT]
 [LEFT]        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)[/LEFT]
 [LEFT]        Status: D3 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-[/LEFT]
 [LEFT]    Capabilities: [90] Vendor Specific Information: Len=14 <?>
[/LEFT]
 [LEFT]    Kernel modules: intel_lpss_pci[/LEFT]

```   

[LEFT]Is  there anything else I need to do after loading the updated spi-nor  module as descried above? Do I need to "probe" the SPI/MTD devices  somehow?
[/LEFT]
 [LEFT]What else could be the issue?

[/LEFT]
  [LEFT]Thanks,[/LEFT]
 Dmitri

---

### Post by Doug S on 2024-07-29
Given the changes since the article you reference was written, what you did seems okay. It it were me, I would just recompile the entire kernel and use that.
I observe that things have changed further since kernel 6.5. For 6.11-rc1 I think the change would be:

```
doug@s19:~/kernel/linux/drivers/mtd/spi-nor$ git diff
diff --git a/drivers/mtd/spi-nor/spansion.c b/drivers/mtd/spi-nor/spansion.c
index 6cc237c24e07..a185a8fbacb0 100644
--- a/drivers/mtd/spi-nor/spansion.c
+++ b/drivers/mtd/spi-nor/spansion.c
@@ -921,6 +921,12 @@ static const struct flash_info spansion_nor_parts[] = {
                .size = SZ_512K,
                .sector_size = SZ_512K,
                .flags = SPI_NOR_NO_ERASE,
+       }, {
+               .id = SNOR_ID(0x08, 0x26, 0xc2, 0x7f, 0x7f, 0x7f),
+               .name = "cy15b104q",
+               .size = SZ_512K,
+               .sector_size = SZ_512K,
+               .flags = SPI_NOR_NO_ERASE,
        }, {
                .id = SNOR_ID(0x34, 0x2a, 0x1a, 0x0f, 0x03, 0x90),
                .name = "s25hl512t",
```

EDIT: By the way: 23.10 is past EOL.

---

### Post by dlp2501 on 2024-07-30
Thanks for the response. I have installed 24.04 and made all appropriate modifications as above, but still have the same issue.
I&#8217;ll continue debugging, will update here if I manage to solve it..

---

