---
title: "No sound with my SB128..."
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by mmortier on 2005-02-15
Hi everybody,

I'm not fluent in english, well sorry...  :? 

I've a problem with the sound and I don't understand why!!
I have a SoundBlaster 128 with an ASUS P4C800-E motherboard.

the command [FONT=Courier New]lsmod[/FONT] :
[FONT=Courier New]
Module                  Size  Used by
proc_intf               4128  0
freq_table              4512  0
cpufreq_userspace       7072  0
cpufreq_powersave       1952  0
button                  6808  0
ac                      5036  0
battery                 9612  0
ipv6                  273956  10
af_packet              23496  2
emu10k1_gp              3808  0
snd_emu10k1            99496  2
snd_util_mem            4736  1 snd_emu10k1
snd_hwdep               9632  1 snd_emu10k1
ohci1394               36004  0
e1000                  83908  0
snd_intel8x0           36524  3
snd_ac97_codec         68772  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            53864  0
snd_mixer_oss          19744  4 snd_pcm_oss
snd_pcm                99552  3 snd_emu10k1,snd_intel8x0,snd_pcm_oss
snd_timer              26756  1 snd_pcm
snd_page_alloc         11688  3 snd_emu10k1,snd_intel8x0,snd_pcm
gameport                5024  2 emu10k1_gp,snd_intel8x0
snd_mpu401_uart         8416  1 snd_intel8x0
snd_rawmidi            25664  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          8296  2 snd_emu10k1,snd_rawmidi
snd                    57828  16 snd_emu10k1,snd_util_mem,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10688  4 snd
piix                   13504  1
hw_random               5780  0
ehci_hcd               32068  0
uhci_hcd               33008  0
usbcore               119044  4 ehci_hcd,uhci_hcd
shpchp                100364  0
pciehp                 96908  0
pci_hotplug            34716  2 shpchp,pciehp
intel_agp              22336  0
intel_mch_agp          10544  1
agpgart                34316  2 intel_agp,intel_mch_agp
rtc                    14088  0
md                     50184  0
dm_mod                 58592  1
capability              4744  0
commoncap               7392  1 capability
parport_pc             35680  1
lp                     11044  0
parport                42216  2 parport_pc,lp
sbp2                   24488  0
ieee1394              110744  2 ohci1394,sbp2
tsdev                   7488  0
evdev                   9696  0
ide_generic             1632  0
ide_disk               19136  0
ide_cd                 42180  0
ide_core              138896  4 piix,ide_generic,ide_disk,ide_cd
mousedev               10480  1
psmouse                19976  0
sr_mod                 17316  0
cdrom                  39808  2 ide_cd,sr_mod
ext3                  126344  2
jbd                    68952  1 ext3
mbcache                10148  1 ext3
sd_mod                 21760  4
sata_promise           10244  0
ata_piix                8228  6
libata                 40676  2 sata_promise,ata_piix
scsi_mod              125412  5 sbp2,sr_mod,sd_mod,sata_promise,libata
unix                   30576  698
fan                     4204  0
thermal                13232  0
processor              18272  1 thermal
font                    8576  0
vesafb                  6784  0
cfbcopyarea             3936  1 vesafb
cfbimgblt               3296  1 vesafb
cfbfillrect             3840  1 vesafb
[/FONT]
 
and [FONT=Courier New]lspci -v[/FONT] :
[FONT=Courier New]
0000:03:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dfe0
        Capabilities: <available only to root>
[/FONT]

I think that is because the SB can be only used by root. Well, can I change it?

Thanks a lot in advance.

M

---

### Post by BobFolkerts on 2005-02-15
I think you need to type "sudo lspci -v".  The permission issue deals with who ran the command, I don't think that this is a permission issue with using the sound card.

---

### Post by mmortier on 2005-02-16
OK, you're right!!
Well, It is curious...

Any other idea?

THx

MM

---

