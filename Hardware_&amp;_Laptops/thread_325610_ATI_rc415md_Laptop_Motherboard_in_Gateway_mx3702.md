---
title: "ATI rc415md Laptop Motherboard in Gateway mx3702"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by JacksSmolderingServer on 2006-12-26
Gateway mx3702 - no sound, appears no host/south bridge communtication (missing drivers, modules)

Trying to find drivers for missing hardware, ATI/AMD site is useless (shock!)

edgy 6.10

kernel 6.17-20

Manufacturer site:  (great links for hardware details)

[http://support.gateway.com/s/Mobile/Q106/Bishop/2905898Rcl3.shtml]("http://support.gateway.com/s/Mobile/Q106/Bishop/2905898Rcl3.shtml")

lspci output 

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Capabilities: [b0] #0d [0000]

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0100000-d01fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [b0] #0d [0000]
	Capabilities: [b8] HyperTransport: MSI Mapping
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [b0] #0d [0000]
	Capabilities: [b8] HyperTransport: MSI Mapping
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
	Memory at d0504000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
	Memory at d0505000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
	Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at d0507000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at 8410 [size=16]
	Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, slow devsel, latency 64, IRQ 209
	Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Gateway 2000 Unknown device 0318
	Flags: bus master, fast devsel, latency 0, IRQ 233
	Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
	Capabilities: [100] Advanced Error Reporting

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8185 (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8185
	Flags: bus master, medium devsel, latency 64, IRQ 225
	I/O ports at b000 [size=256]
	Memory at d0200000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2

lsmod output

Module                  Size  Used by
ac97_codec             20364  0 
snd_hda_intel          20116  0 
iptable_filter          4224  0 
ip_tables              15204  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  272288  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_centrino      9760  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  4 
joydev                 11200  0 
tsdev                   9152  0 
snd_hda_codec         164608  1 snd_hda_intel
sky2                   43012  0 
r818x                  95372  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
psmouse                41352  0 
ieee80211_rtl          85640  1 r818x
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
ati_agp                10636  0 
agpgart                34888  1 ati_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
pcspkr                  4352  0 
serio_raw               8452  0 
snd                    58372  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
evdev                  11392  1 
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ide_generic             2432  0 
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  3 ehci_hcd,ohci_hcd
ide_disk               18560  3 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
generic                 6276  0 
atiixp                  7824  1 
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by themasquerade1013 on 2008-01-13
I'm having the same problem with the RC415MD chipset.  No sound at all.

---

