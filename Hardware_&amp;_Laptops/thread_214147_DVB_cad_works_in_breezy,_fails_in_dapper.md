---
title: "DVB cad works in breezy, fails in dapper"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Orpheus- on 2006-07-12
I have a DViCO FusionHDTV DVB-T Plus card which I've successfully been using in breezy for a while now. I tried a clean install of dapper, and now the card fails. I reinstalled breezy - card works again, which suggests it's not a hardware fault. I would, however, like to get it working under dapper.

The card fails to tune any channels:

orpheus@hawkins:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ sudo scan au-Perth 
scanning au-Perth
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 0 3 1 1 0
initial transponder 177500000 1 2 0 3 1 2 0
initial transponder 191625000 1 3 0 3 1 1 0
initial transponder 219500000 1 3 0 3 1 1 0
initial transponder 536625000 1 2 0 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: >>> tuning failed!!!

Every channel it tries gets the "tuning failed" message.

Any ideas? Other potentially useful information:

orpheus@hawkins:~$ uname -a
Linux hawkins 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686

orpheus@hawkins:~$ lsmod
Module                  Size  Used by
rfcomm                 43604  0 
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0 
cpufreq_userspace       6496  0 
cpufreq_stats           6688  0 
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        7752  0 
cpufreq_conservative     9000  0 
ipv6                  286976  24 
ext2                   74152  1 
dm_mod                 63256  1 
af_packet              24520  2 
md_mod                 76052  0 
lp                     12356  0 
parport_pc             37988  1 
parport                39400  3 ppdev,lp,parport_pc
snd_emu10k1_synth       8096  0 
snd_emux_synth         39968  1 snd_emu10k1_synth
snd_seq_virmidi         8384  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_seq_dummy           3908  0 
snd_seq_oss            37216  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      7520  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
floppy                 64676  0 
snd_seq                58160  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  2244  0 
emu10k1_gp              3904  0 
gameport               16776  2 emu10k1_gp
snd_emu10k1           134628  1 snd_emu10k1_synth
snd_rawmidi            26848  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         99808  1 snd_emu10k1
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss
psmouse                40004  0 
snd_pcm                96708  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              26884  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11304  2 snd_emu10k1,snd_pcm
snd_util_mem            4928  2 snd_emux_synth,snd_emu10k1
serio_raw               7748  0 
snd_hwdep               9952  2 snd_emux_synth,snd_emu10k1
nvidia               4552660  0 
cx88_blackbird         21692  0 
cx88_dvb               10660  0 
cx8802                 12740  2 cx88_blackbird,cx88_dvb
mt352                   7236  1 cx88_dvb
or51132                10564  1 cx88_dvb
video_buf_dvb           6884  1 cx88_dvb
dvb_core               88424  1 video_buf_dvb
cx8800                 34668  1 cx88_blackbird
cx88xx                 64384  4 cx88_blackbird,cx88_dvb,cx8802,cx8800
i2c_algo_bit            9800  1 cx88xx
video_buf              22724  6 cx88_blackbird,cx88_dvb,cx8802,video_buf_dvb,cx8800,cx88xx
ir_common               9892  1 cx88xx
tveeprom               15312  1 cx88xx
v4l1_compat            15204  1 cx8800
v4l2_common             6080  1 cx8800
btcx_risc               5288  3 cx8802,cx8800,cx88xx
videodev               10144  3 cx88_blackbird,cx8800,cx88xx
nxt200x                16036  1 cx88_dvb
lgdt330x                8636  1 cx88_dvb
cx22702                 6980  1 cx88_dvb
dvb_pll                11044  4 cx88_dvb,or51132,nxt200x,cx22702
e100                   40964  0 
mii                     6176  1 e100
i2c_piix4               9168  0 
i2c_core               22848  11 nvidia,cx88_dvb,mt352,or51132,cx88xx,i2c_algo_bit,tveeprom,nxt200x,lgdt330x,cx22702,i2c_piix4
snd                    60004  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10784  1 snd
shpchp                 49504  0 
pci_hotplug            30788  1 shpchp
intel_agp              24700  1 
agpgart                36784  2 nvidia,intel_agp
evdev                  10176  0 
xfs                   649696  2 
exportfs                6528  1 xfs
ide_generic             1504  0 
uhci_hcd               35408  0 
usbcore               139076  2 uhci_hcd
ide_cd                 35780  0 
cdrom                  41408  1 ide_cd
ide_disk               19136  6 
piix                   11652  1 
generic                 5124  0 
processor              26344  0 
capability              4968  0 
commoncap               7328  1 capability
vga16fb                13992  1 
vgastate               10208  1 vga16fb
fbcon                  43904  71 
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

(bits of dmesg)
[   64.272711] Linux video capture interface: v1.00
[   64.391439] cx2388x v4l2 driver version 0.0.5 loaded
[   64.391618] PCI: Found IRQ 10 for device 0000:00:0f.0
[   64.391650] PCI: Sharing IRQ 10 with 0000:00:0f.2
[   64.391677] cx88[0]: quirk: PCIPCI_NATOMA -- set TBFX
[   64.391788] CORE cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
[   64.391802] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[   64.486277] cx2388x dvb driver version 0.0.5 loaded
[   64.619279] cx88[0]/0: found at 0000:00:0f.0, rev: 5, irq: 10, latency: 165, mmio: 0xe9000000
[   64.619537] cx88[0]/0: registered device video0 [v4l2]
[   64.619662] cx88[0]/0: registered device vbi0
[   64.621070] PCI: Found IRQ 10 for device 0000:00:0f.2
[   64.621100] PCI: Sharing IRQ 10 with 0000:00:0f.0
[   64.621128] cx88[0]/2: found at 0000:00:0f.2, rev: 5, irq: 10, latency: 64, mmio: 0xea000000
[   64.621149] cx88[0]/2: cx2388x based dvb card
[   64.623161] DVB: registering new adapter (cx88[0]).
[   64.623173] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   64.665191] cx2388x blackbird driver version 0.0.5 loaded

---

### Post by h6w on 2007-06-26
Bump!

Same for Feisty. :(

Any news on this one?  Has anyone even submitted a bug report?

---

