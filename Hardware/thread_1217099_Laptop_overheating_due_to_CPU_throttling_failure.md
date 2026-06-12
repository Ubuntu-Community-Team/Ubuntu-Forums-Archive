---
title: "Laptop overheating due to CPU throttling failure"
date: 2009-07-19
forum: Hardware
---

### Post by irwjager on 2009-07-19
Hi all,

I have an old laptop here (Twinhead Pentium III 1133Mhz) which regularly overheats on Jaunty/9.04. It turns out that CPU throttling is not working. None of the frequency setting modules will load.
'modprobe acpi-cpufreq' yields 'No such device', as do the older deprecated speedstep-<x> modules.

There's nothing in the Kernel ring buffer (dmesg) other than a reassuring "ACPI: Processor [CPU0] (supports 8 throttling states)", no errors.

I'm really lost! Anyone have any ideas?

Thanks!

Ivo



$cat /proc/ioports | grep CPU
1010-1015 : ACPI CPU throttle

$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Pentium(R) III CPU             1133MHz
stepping	: 1
cpu MHz		: 1133.437
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips	: 2266.87
clflush size	: 32
power management:

$ cat /proc/acpi/processor/CPU0/throttling
state count:             8
active state:            T1
state available: T0 to T7
states:
    T0:                  100%
   *T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

$ lsmod
Module                  Size  Used by
binfmt_misc             8200  1 
input_polldev           3976  0 
video                  17040  0 
output                  3072  1 video
lp                      9124  0 
arc4                    2048  2 
ecb                     2944  2 
ath5k                  98176  0 
snd_ali5451            17804  3 
mac80211              203256  1 ath5k
snd_ac97_codec        103844  1 snd_ali5451
joydev                  9792  0 
led_class               4228  1 ath5k
ac97_bus                1920  1 snd_ac97_codec
cfg80211               29968  2 ath5k,mac80211
snd_pcm_oss            37760  0 
snd_mixer_oss          14592  1 snd_pcm_oss
snd_pcm                71304  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2948  0 
snd_seq_oss            28800  0 
snd_seq_midi            6400  0 
snd_rawmidi            20608  1 snd_seq_midi
snd_seq_midi_event      7040  2 snd_seq_oss,snd_seq_midi
snd_seq                45296  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 34156  0 
snd_timer              19588  2 snd_pcm,snd_seq
snd_seq_device          7180  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   7556  0 
psmouse                53396  0 
parport_pc             31652  1 
snd                    53028  16 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24332  2 
rsrc_nonstatic         11264  1 yenta_socket
i2c_ali15x3             6660  0 
ali_agp                 5760  1 
pcspkr                  2560  0 
serio_raw               5380  0 
parport                33224  3 lp,ppdev,parport_pc
snd_page_alloc          8968  1 snd_pcm
pcmcia_core            35088  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_ali1535             6148  0 
agpgart                33584  1 ali_agp
shpchp                 32276  0 
ohci1394               29616  0 
ieee1394               83900  1 ohci1394
floppy                 53220  0 

$ lspci -v
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-ali
	Kernel modules: ali-agp

00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
	Flags: bus master, slow devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ea100000-efffffff
	Prefetchable memory behind bridge: 28000000-280fffff
	Kernel modules: shpchp

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10)
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:03.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 28100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02) (prog-if 10)
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at ea001000 (32-bit, non-prefetchable) [size=2K]
	Memory at ea004000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: Device 168f:0002
	Flags: medium devsel
	Capabilities: <access denied>
	Kernel driver in use: ali1535_smbus
	Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535

00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: alim7101_wdt, alim1535_wdt

00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 2000 [size=256]
	Memory at ea002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ALI 5451
	Kernel modules: snd-ali5451

00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c3) (prog-if fa)
	Subsystem: Device 168f:0002
	Flags: bus master, medium devsel, latency 64, IRQ 255
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_ali

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
	Subsystem: Device 168f:0002
	Flags: 66MHz, medium devsel, IRQ 9
	Memory at ee000000 (32-bit, non-prefetchable) [size=32M]
	Memory at ea400000 (32-bit, non-prefetchable) [size=4M]
	Memory at ec000000 (32-bit, non-prefetchable) [size=32M]
	Memory at ea100000 (32-bit, non-prefetchable) [size=32K]
	[virtual] Expansion ROM at 28000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: tridentfb

02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a12
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 24000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k

---

### Post by EvilJeff on 2009-09-08
Hey, are you still pursuing this problem?
 
I've got a very similar problem with my KDS 681XH (P3 1000MHZ, Ali CHipset); on mine, the ACPI CPU Throttle is overlapping the Ali M5451 Audio's I/O Port Ragne. My Ali M5451 is using the 1000-10ff range, and the ACPI CPU Throttle is on the 1010-1015 I/O range. The sound does not initialize, and so I have no sound, but i DO have CPU throttling. BTW, if I disable ACPI at boot with the argument ACPI=off, I DO get sound working.
 
Sort of the opposite of what you're experiencing, but probably related. BTW, I'm running AntiX MEPIS 8. I would like to see your complete /proc/ioports - mine clearly shows the conflicting range, where 00:08.0 (Ali M5451) is getting "cut off" by the ACPI CPU Throttle. I can't figure out just yet how to reassign one of them, but I DID notice your Ali M5451 is using a different I/O rangel. Maybe we can help each ther out.
 
Thanks,
EvilJeff

---

