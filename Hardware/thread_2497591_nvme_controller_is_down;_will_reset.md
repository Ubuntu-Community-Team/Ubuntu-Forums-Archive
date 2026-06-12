---
title: "nvme controller is down; will reset"
date: 2024-05-11
forum: Hardware
---

### Post by alekzunder on 2024-05-11
Hi, all!
In the beginning of December 2023, i bough SSD Kingston FURY Renegade PCIe 4.0 NVMe M.2 (SFYRD2000G FW:EIFK31.6, 2.00 TB)
Motherboard: ASrock Z77 extreme6
CPU: Intel(R) Core(TM) i7-3770T CPU @ 2.50GHz
SSD installed to PCI-e slot over adapter

Perfectly installed and work Ubuntu mate 22.04.4 LTS. Only!
From December to end of January, everything worked fine.... and beginning!
For a long time I did not understand what was the matter, until the failure occurred during the load.
I make photo.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293752&stc=1[/IMG]
Fast (and slow) googling said me, add options to kernel:
```
 cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-6.8.8-060808-generic root=UUID=bf222031-3d3a-4237-bd68-23cd8e4faea0 ro acpi_enforce_resources=lax nvme_core.default_ps_max_latency_us=0 pcie_aspm=off

```
Options added over GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax nvme_core.default_ps_max_latency_us=0 pcie_aspm=off"
I tried to change kernell: 6.2* 6.4.* 6.7.* 6.8.*  There is no updates fw for SSD and motherboard.
Nothing helps.
In syslog - nothing, fs switch to read-only mode, helpful only hard-reset.

---

### Post by MAFoElffen on 2024-05-11
What are the results of these posted within CODE Tags:
```

sudo nvme error-log /dev/nvme0n1 | grep -e 'error_count       : ' | grep -v '0'
sudo smartctl -a /dev/nvme0n1 | awk '/Error Information/,EOF {print $0}'

```
Sunstitute the device name to what your drive in question is.

---

### Post by alekzunder on 2024-05-12
```
sudo nvme error-log /dev/nvme0n1 | grep -e 'error_count : ' | grep -v '0'
error_count    : 158
error_count    : 157
```

```
sudo nvme error-log /dev/nvme0n1
Error Log Entries for device:nvme0n1 entries:63
.................
 Entry[ 0]   
.................
error_count    : 158
sqid        : 0
cmdid        : 0x300f
status_field    : 0x2002(INVALID_FIELD: A reserved coded value or an unsupported value in a defined field)
phase_tag    : 0
parm_err_loc    : 0x28
lba        : 0
nsid        : 0
vs        : 0
trtype        : The transport type is not indicated or the error is not transport related.
cs        : 0
trtype_spec_info: 0
.................
 Entry[ 1]   
.................
error_count    : 157
sqid        : 0
cmdid        : 0xd
status_field    : 0x2002(INVALID_FIELD: A reserved coded value or an unsupported value in a defined field)
phase_tag    : 0
parm_err_loc    : 0xffff
lba        : 0
nsid        : 0
vs        : 0
trtype        : The transport type is not indicated or the error is not transport related.
cs        : 0
trtype_spec_info: 0
.................
 Entry[ 2]   
.................
error_count    : 0
sqid        : 0
cmdid        : 0
status_field    : 0(SUCCESS: The command completed successfully)
phase_tag    : 0
parm_err_loc    : 0
lba        : 0
nsid        : 0
vs        : 0
trtype        : The transport type is not indicated or the error is not transport related.
cs        : 0
trtype_spec_info: 0
.................


```
Entry 2....63 - the same.

```
sudo smartctl -a /dev/nvme0n1 | awk '/Error Information/,EOF {print $0}'
Error Information Log Entries:      158
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 2:               58 Celsius

Error Information (NVMe Log 0x01, 16 of 63 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0        158     0  0x300f  0x4004  0x028            0     0     -
  1        157     0  0x000d  0x4004      -            0     0     -



```

---

### Post by MAFoElffen on 2024-05-12
Looks like that drive is starting to fail at the hardware level.

Do you have good backups of what is on it?

---

### Post by alekzunder on 2024-05-12
> **MAFoElffen said:**
> Looks like that drive is starting to fail at the hardware level.
What to do with it? The drive is new. 

> **MAFoElffen said:**
> Do you have good backups of what is on it?
Yes of course.
It's regular computer, but works as server for video surveillance and home automation.

---

### Post by MAFoElffen on 2024-05-12
Just me, but I would do a long-test on it. The sytax for smartctl to do tests are:
```

sudo smartctl -t <short|long|conveyance|select> <disk_name>

```
Is it still under warranty? You said a year old. For your drive ---> Limited 5-year warranty with free technical support...

I might call them before doing any destructive tests, to see what they need to warranty it.

---

### Post by alekzunder on 2024-05-15
Thanks for your reply.
Yes, under warranty. I will try to contact the Kingston, but I'm afraid that my motherboard is old and EFI in beta-stage.
However, the problem is not solved.

I try...
```
sudo nvme cmdset-ind-id-ns /dev/nvme0n1 -H
NVMe status: INVALID_FIELD: A reserved coded value or an unsupported value in a defined field(0x2002)
```
and error in SMART increment!
It looks like an error in firmware of drive!
I reproduce the issue with a large write using fio like here[: https://unix.stackexchange.com/questions/742360/heavy-io-causes-nvme-controller-is-down-will-reset]("https://unix.stackexchange.com/questions/742360/heavy-io-causes-nvme-controller-is-down-will-reset"):
```
fio --name=write_test_50 --rw=write --size=50GB --filename=fio.file
```
Don't buy Kingston!

---

### Post by MAFoElffen on 2024-05-17
Do they had new firmware for that drive?

---

### Post by alekzunder on 2024-05-17
Now - last firmware on drive and motherboard

---

### Post by MAFoElffen on 2024-05-18
Did you contact Kingston about your Tech Support and Warranty options yet?

---

### Post by alekzunder on 2024-05-20
Yes, requested me full hardware configuration. Offered add kernel options: libata.allow_tpm=1 nvme_core.default_ps_max_latency_us=0
In general, nothing interesting. There were a weekend, maybe they will write something today. Waiting....

---

### Post by digitaloxide42 on 2024-05-22
Kingston solid states are actually pretty good, we have had better luck with them than samsung lately, and we go through a lot of hard drives at my office.


That being said I think you won the silicon lottery on this one, it certianly looks like you have a bad SSD drive. But I would also upgrade your motherboard, processor and ram while your at it... I've never liked the pcie expansion cards for nvme slots very much, its much better to have a board with native nvme slots in my opinion.

---

### Post by alekzunder on 2024-05-28
I got answer from support of Kingston: return to the store.

Addition:
I repeated check over fio, and noticed, that nvme controller down, if temperature more then 47...48 degrees!
I bought a new NVME Samsung, check fio. It work fine! At temperature above 60 degrees!
I'm shure that case in heated of NVME-controller.

I don't close topic yet...

Addition: on new nvme SSD, the error counter is also growing. How critical is it? I found [https://github.com/linux-nvme/nvme-cli/issues/2029#issuecomment-1862744947](https://github.com/linux-nvme/nvme-cli/issues/2029#issuecomment-1862744947)

```
sudo nvme error-log /dev/nvme0n1
Error Log Entries for device:nvme0n1 entries:64
.................
 Entry[ 0]   
.................
error_count    : 3
sqid        : 0
cmdid        : 0x4009
status_field    : 0x2002(INVALID_FIELD: A reserved coded value or an unsupported value in a defined field)
phase_tag    : 0
parm_err_loc    : 0xffff
lba        : 0
nsid        : 0
vs        : 0
trtype        : The transport type is not indicated or the error is not transport related.
cs        : 0
trtype_spec_info: 0
.................


```

---

### Post by vinnyoflegend on 2024-09-05
Did you end up returning this drive? There is a new firmware available for it now that solves a read degradation issue. It's not clear if this is the issue you were experiencing but I would try it if you still have the drive.

see:

[https://www.overclock.net/threads/corsair-mp510-980gb-slooooooooow-with-older-files-like-7-10mb-s-read-speed-slow.1801829/#post-29305985](https://www.overclock.net/threads/corsair-mp510-980gb-slooooooooow-with-older-files-like-7-10mb-s-read-speed-slow.1801829/#post-29305985)

[https://media.kingston.com/support/downloads/SKC3000_SFYR_EIFK31.7_RN.pdf](https://media.kingston.com/support/downloads/SKC3000_SFYR_EIFK31.7_RN.pdf)

Firmware Rev. EIFK31.7 (07-08-2024)• Improved decoding flow to prevent excessive latency found on certainplatforms

> **alekzunder said:**
> I got answer from support of Kingston: return to the store.

Addition:
I repeated check over fio, and noticed, that nvme controller down, if temperature more then 47...48 degrees!
I bought a new NVME Samsung, check fio. It work fine! At temperature above 60 degrees!
I'm shure that case in heated of NVME-controller.

I don't close topic yet...

Addition: on new nvme SSD, the error counter is also growing. How critical is it? I found [https://github.com/linux-nvme/nvme-cli/issues/2029#issuecomment-1862744947](https://github.com/linux-nvme/nvme-cli/issues/2029#issuecomment-1862744947)



---

### Post by alekzunder on 2024-09-08
I still have a drive, i tried to put to the store, but he laid back and began to work normally, but other pc. Thank you for answer about new firmware, i will definitely update.

---

