---
title: "Hard Resetting Link Daily"
date: 2010-03-18
forum: Hardware
---

### Post by eMask on 2010-03-18
I run a Large file server with many users. It runs Debian Lenny with kernel 2.6.26-2-amd64.

I have a software (mdadm) raid 5 array with 6 Seagate 7200.11 ST31500341AS 1.5TB hard disks running on an Intel ICH10R motherboard controller using AHCI for hot swappable capabilities.  These drives are almost constantly being accessed with large file transfers going on a majority of the day.

Lately I have been experiencing some very random errors that are happening just about 1-3 times a day.  Searching around very rigorously on google and these terrific forums, I have found some very similar issues but not exactly what I'm looking at.

Basically I am getting hard resetting link notifications based on Drive timeouts.

Looking at the errors below and trying to interpret them using this very helpful guide:
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)
It seems to me that the problem stems from either their being to much load on the controller or disk, or the possibility of a problem with NCQ (Native Command Queueing) on the kernel or drive side. Im not really sure and that is why I have come here to see if anyone has an ironclad idea of what these errors represent.

I have not been able to try swapping cables or trying the ejected cd-rom trick but i have made sure nvidia drivers are fully uninstalled as these were all things that contributed to very similar "hard resetting link" errors for many others using similar kernels and either ubuntu or debian.

So now for some logs:
lsmod command (list of modules being used by kernel)

```
Module                  Size  Used by
jfs                   158032  0
nls_base               12932  1 jfs
ppdev                  11656  0
parport_pc             31016  0
lp                     14724  0
parport                41776  3 ppdev,parport_pc,lp
ipv6                  288456  30
acpi_cpufreq           11792  0
cpufreq_userspace       8452  0
cpufreq_powersave       6400  0
cpufreq_ondemand       11792  4
cpufreq_stats           9120  0
cpufreq_conservative    11784  0
freq_table              9344  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
xt_state                6656  2
xt_tcpudp               7680  27
xt_multiport            7424  1
iptable_filter          7424  1
iptable_mangle          7424  0
iptable_nat             9872  0
nf_nat                 23192  1 iptable_nat
nf_conntrack_ipv4      19352  5 iptable_nat,nf_nat
nf_conntrack           71440  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
ip_tables              21520  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               25224  5 xt_state,xt_tcpudp,xt_multiport,iptable_nat,ip_tables
coretemp               11008  0
it87                   28952  0
hwmon_vid               7296  1 it87
loop                   19468  0
snd_hda_intel         436696  1
serio_raw               9988  0
psmouse                42268  0
snd_pcm                81800  1 snd_hda_intel
pcspkr                  7040  0
i2c_i801               13596  0
snd_seq                54304  0
i2c_core               27936  1 i2c_i801
snd_timer              25744  2 snd_pcm,snd_seq
snd_seq_device         11668  1 snd_seq
snd                    63688  7 snd_hda_intel,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12064  1 snd
intel_agp              31856  0
button                 11680  0
snd_page_alloc         13072  2 snd_hda_intel,snd_pcm
joydev                 14848  0
evdev                  14208  4
ext3                  125072  1
jbd                    51240  1 ext3
mbcache                12804  1 ext3
raid10                 23680  0
raid456               125984  1
async_xor               8448  1 raid456
async_memcpy            6912  1 raid456
async_tx               11764  3 raid456,async_xor,async_memcpy
xor                     9744  2 raid456,async_xor
raid1                  24192  0
raid0                  10624  0
multipath              11392  0
linear                  8960  0
md_mod                 80292  6 raid10,raid456,raid1,raid0,multipath,linear
jmicron                 6912  0 [permanent]
sg                     36448  0
sd_mod                 29376  9
sr_mod                 19652  0
cdrom                  37928  1 sr_mod
ide_pci_generic         9220  0 [permanent]
ide_core              128284  2 jmicron,ide_pci_generic
usbhid                 45792  0
hid                    41792  1 usbhid
ff_memless              9224  1 usbhid
floppy                 61672  0
e1000                 117312  0
ata_generic            10116  0
ahci                   33036  8
libata                165600  2 ata_generic,ahci
sky2                   48132  0
scsi_mod              161016  4 sg,sd_mod,sr_mod,libata
dock                   14112  1 libata
ehci_hcd               36108  0
uhci_hcd               25760  0
thermal                22688  0
processor              42304  2 acpi_cpufreq,thermal
fan                     9352  0
thermal_sys            17728  3 thermal,processor,fan
```And Here are the kern.log's of a few implications (separated by spaces) of the error:

```
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x6 frozen
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/80:00:80:80:e0/00:00:34:00:00/40 tag 0 ncq 65536 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/80:08:00:81:e0/00:00:34:00:00/40 tag 1 ncq 65536 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/48:10:80:81:e0/00:00:34:00:00/40 tag 2 ncq 36864 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/18:18:c8:81:e0/00:00:34:00:00/40 tag 3 ncq 12288 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/08:20:e0:81:e0/00:00:34:00:00/40 tag 4 ncq 4096 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: cmd 60/18:28:e8:81:e0/00:00:34:00:00/40 tag 5 ncq 12288 in
Mar 15 23:10:12  kernel: [1660963.723266]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 15 23:10:12  kernel: [1660963.723266] ata5.00: status: { DRDY }
Mar 15 23:10:12  kernel: [1660963.723266] ata5: hard resetting link
Mar 15 23:10:13  kernel: [1660964.568115] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 15 23:10:13  kernel: [1660964.681372] ata5.00: configured for UDMA/133
Mar 15 23:10:13  kernel: [1660964.681372] ata5: EH complete
Mar 15 23:10:13  kernel: [1660964.681372] sd 4:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
Mar 15 23:10:13  kernel: [1660964.681372] sd 4:0:0:0: [sdc] Write Protect is off
Mar 15 23:10:13  kernel: [1660964.681372] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Mar 15 23:10:13  kernel: [1660964.681372] sd 4:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA



Mar 16 01:32:27  kernel: [1675458.041370] ata6.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
Mar 16 01:32:27  kernel: [1675458.041370] ata6.00: cmd 60/80:00:80:f6:d3/00:00:08:00:00/40 tag 0 ncq 65536 in
Mar 16 01:32:27  kernel: [1675458.041370]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 01:32:27  kernel: [1675458.041370] ata6.00: status: { DRDY }
Mar 16 01:32:27  kernel: [1675458.041370] ata6.00: cmd 60/00:08:80:f6:d3/01:00:08:00:00/40 tag 1 ncq 131072 in
Mar 16 01:32:27  kernel: [1675458.041370]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 01:32:27  kernel: [1675458.041370] ata6.00: status: { DRDY }
Mar 16 01:32:27  kernel: [1675458.041370] ata6: hard resetting link
Mar 16 01:32:28  kernel: [1675458.757015] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 16 01:32:28  kernel: [1675458.866206] ata6.00: configured for UDMA/133
Mar 16 01:32:28  kernel: [1675458.866227] ata6: EH complete
Mar 16 01:32:28  kernel: [1675458.866206] sd 5:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
Mar 16 01:32:28  kernel: [1675458.866206] sd 5:0:0:0: [sdb] Write Protect is off
Mar 16 01:32:28  kernel: [1675458.866206] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Mar 16 01:32:28  kernel: [1675458.866206] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA



Mar 16 10:44:56  kernel: [1718884.999736] ata6.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x6 frozen
Mar 16 10:44:56  kernel: [1718884.999747] ata6.00: cmd 60/e8:00:18:fc:e8/00:00:89:00:00/40 tag 0 ncq 118784 in
Mar 16 10:44:56  kernel: [1718884.999749]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999755] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999762] ata6.00: cmd 60/80:08:80:fc:e8/00:00:89:00:00/40 tag 1 ncq 65536 in
Mar 16 10:44:56  kernel: [1718884.999764]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999769] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999775] ata6.00: cmd 60/d8:10:00:fd:e8/00:00:89:00:00/40 tag 2 ncq 110592 in
Mar 16 10:44:56  kernel: [1718884.999777]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999782] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999789] ata6.00: cmd 60/00:18:00:fd:e8/01:00:89:00:00/40 tag 3 ncq 131072 in
Mar 16 10:44:56  kernel: [1718884.999791]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999796] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999802] ata6.00: cmd 60/10:20:d8:fd:e8/00:00:89:00:00/40 tag 4 ncq 8192 in
Mar 16 10:44:56  kernel: [1718884.999804]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999809] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999816] ata6.00: cmd 60/18:28:e8:fd:e8/00:00:89:00:00/40 tag 5 ncq 12288 in
Mar 16 10:44:56  kernel: [1718884.999818]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 16 10:44:56  kernel: [1718884.999822] ata6.00: status: { DRDY }
Mar 16 10:44:56  kernel: [1718884.999830] ata6: hard resetting link
Mar 16 10:44:57  kernel: [1718885.492378] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 16 10:44:57  kernel: [1718885.614325] ata6.00: configured for UDMA/133
Mar 16 10:44:57  kernel: [1718885.614325] ata6: EH complete
Mar 16 10:44:57  kernel: [1718885.614325] sd 5:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
Mar 16 10:44:57  kernel: [1718885.614325] sd 5:0:0:0: [sdb] Write Protect is off
Mar 16 10:44:57  kernel: [1718885.614325] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Mar 16 10:44:57  kernel: [1718885.614325] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
```

As you can see, it seems the drives are timing out and not responding to commands therefore they are hard reset yet this does not seem to affect the array at all.  These resets seem to happen transparently and usually during I/O activity but I have not been able to test yet without it. These errors have also happened to pretty much every drive in the array they occur on sdb and sdg more than on most of the other drives but its too random to make a difference.

It is somewhat hard to do troubleshooting in a server environment but I do have some time later this week that the server will be going down for a few days to run some tests and try different scenarios to figure out what is going on.  

Looking at similar people on the Seagate forums who have had similar issues, many of them suggested turning of write cache which you can see I have done on all the drives. This greatly decreased the reocurences of these errors but did not deplete them. 

Now I'm wondering if maybe NCQ must be disabled as well or if these are natural because of the large bandwidth on the controller or maybe the kernel is at fault.

Thanks.

-eMask

---

