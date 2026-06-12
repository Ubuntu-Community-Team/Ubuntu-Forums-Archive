---
title: "virtual raid disk is not recognized"
date: 2022-02-11
forum: Hardware
---

### Post by mircot80 on 2022-02-11
Hello
I have a LSI MegaRaid SAS 9341-4i 12Gb/s controller on an MSI X399 GAMING PRO CARBON AC motherboard, Ubuntu 20.04.3 LTS desktop, I cannot detect the virtual disk created in the raid.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290002&stc=1[/IMG]

```
$ sudo ./storcli64 show all
Status Code = 0
Status = Success
Description = None


Number of Controllers = 0
Host Name = chia01
Operating System  = Linux5.13.0-28-generic
```

lspci -v

```
0b:00.0 RAID bus controller: Broadcom / LSI MegaRAID SAS-3 3008 [Fury] (rev 02)
    Subsystem: Broadcom / LSI MegaRAID SAS-3 3008 [Fury]
    Flags: fast devsel, IRQ 52, NUMA node 0
    I/O ports at 1000 [size=256]
    Memory at ba500000 (64-bit, non-prefetchable) [size=64K]
    Memory at ba400000 (64-bit, non-prefetchable) [size=1M]
    Expansion ROM at ba300000 [disabled] [size=1M]
    Capabilities: <access denied>
    Kernel modules: megaraid_sas
```

Here is a failed:

```
$ dmesg | grep mega
[    0.788382] megasas: 07.714.04.00-rc1
[    0.841025] megaraid_sas 0000:0b:00.0: BAR:0x1  BAR's base_addr(phys):0x00000000ba500000  mapped virt_addr:0x0000000071d55ddb
[    0.841030] megaraid_sas 0000:0b:00.0: FW now in Ready state
[    0.841031] megaraid_sas 0000:0b:00.0: 63 bit DMA mask and 32 bit consistent mask
[    0.841308] megaraid_sas 0000:0b:00.0: firmware supports msix    : (96)
[    0.841969] megaraid_sas 0000:0b:00.0: requested/available msix 25/25 poll_queue 0
[    0.841973] megaraid_sas 0000:0b:00.0: current msix/online cpus    : (25/24)
[    0.841975] megaraid_sas 0000:0b:00.0: RDPQ mode    : (disabled)
[    0.841977] megaraid_sas 0000:0b:00.0: Current firmware supports maximum commands: 272     LDIO threshold: 237
[    0.842486] megaraid_sas 0000:0b:00.0: Performance mode :Latency (latency index = 1)
[    0.842487] megaraid_sas 0000:0b:00.0: FW supports sync cache    : Yes
[    0.842489] megaraid_sas 0000:0b:00.0: megasas_disable_intr_fusion is called outbound_intr_mask:0x40000009
[    0.899500] megaraid_sas 0000:0b:00.0: Init cmd return status FAILED for SCSI host 1
[    0.899859] megaraid_sas 0000:0b:00.0: Failed from megasas_init_fw 6540
```


Also it seems that the driver is not in /sys:
[COLOR=#232629][FONT=-apple-system]
```
$ sudo find /sys | grep drivers.*0b:00
```

[/FONT][/COLOR]returns nothing


Is there a solution or is the controller not compatible with my motherboard?
Thank you

---

### Post by SeijiSensei on 2022-02-11
Let's make sure you have the SAS module installed.  What does lsmod return? See any entries with "sas"? If not, try running "sudo modprobe mpt3sas". Any better?

---

### Post by mircot80 on 2022-02-11
no way
```
$ lsmod | grep sas
mpt3sas               299008  0
raid_class             16384  1 mpt3sas
scsi_transport_sas     45056  1 mpt3sas
megaraid_sas          163840  0
xhci_pci_renesas       20480  1 xhci_pci
```

---

### Post by mircot80 on 2022-02-15
With an ASRock X99 Extreme3 motherboard the controller works.

---

