---
title: "SSD Errors in dmesg and system hangs"
date: 2012-01-17
forum: Hardware
---

### Post by handverbrennung on 2012-01-17
Hi,

i have a Thinkpad t520 with an ssd as sda and a normal hdd as sdb. Since some days the system hangs for seconds every few minutes. Music continues playing, but i cant access programs, can't click links, etc. Some of the Windows become gray shaded in unity, after some seconds i can use them again. I checked out google and this forum, tried several things like setting libdata.dma stuff at grub. But nothing helped. so here are the logs, which might help.

Dmesg
```
[  118.803917] ata1.00: exception Emask 0x40 SAct 0x0 SErr 0xd0800 action 0x6 frozen
[  118.803930] ata1.00: SError: { HostInt PHYRdyChg CommWake 10B8B }
[  118.803938] ata1.00: failed command: READ DMA
[  118.803949] ata1.00: cmd c8/00:08:08:11:81/00:00:00:00:00/e1 tag 0 dma 4096 in
[  118.803952]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[  118.803959] ata1.00: status: { DRDY }
[  118.803975] ata1.00: hard resetting link
[  119.123386] ata1.01: hard resetting link
[  120.149784] ata1.01: failed to resume link (SControl 0)
[  120.305576] ata1.00: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  120.305591] ata1.01: SATA link down (SStatus 4 SControl 0)
[  120.362075] ata1.00: configured for UDMA/133
[  120.362497] ata1.00: device reported invalid CHS sector 0
[  120.362518] ata1: EH complete
```

lsmod 
```


Module                  Size  Used by
tp_smapi               28400  0 
bnep                   18436  2 
rfcomm                 47946  8 
hdaps                  15071  1 
thinkpad_ec            14449  2 tp_smapi,hdaps
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
dm_crypt               23199  1 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_codec_conexant    62197  1 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
cdc_ncm                17399  0 
usbnet                 26212  1 cdc_ncm
snd_hda_intel          33390  2 
cdc_wdm                17545  0 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel
cdc_acm                22761  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
thinkpad_acpi          81819  0 
serio_raw              13166  0 
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
cfg80211              199630  2 iwlagn,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
nvram                  14413  1 thinkpad_acpi
tpm_tis                18546  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
nouveau               728677  0 
ttm                    76805  1 nouveau
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
i915                  567092  4 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
drm_kms_helper         42558  2 nouveau,i915
e1000e                160582  0 
drm                   236290  7 nouveau,ttm,i915,drm_kms_helper
mxm_wmi                12979  1 nouveau
i2c_algo_bit           13423  2 nouveau,i915
wmi                    19256  1 mxm_wmi
video                  19412  2 nouveau,i915

```

hdparm -v -i /dev/sda

```

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 3072 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0

 Model=OCZ-AGILITY3, FwRev=2.13, SerialNo=OCZ-OSH1JLLD929S3D4M
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/1/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/1/63, CurSects=1032129, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```

---

### Post by efflandt on 2012-01-19
You might try reseating the drive just to make sure it is not a bad connection.  Usually when I see DRDY it makes me think dirty (bad sectors), but that is unlikely for an SSD and your drive appears to be briefly losing communication entirely.

My experience with OCZ was favorable 8 years ago when I bought RAM on sale that seemed incompatible with my early Athlon64 and they sent me replacement RAM that they guaranteed would work, and it did.

The 80 GB Intel SSD that I used for Natty devel and currently use for 64-bit 11.10 has been flawless (8 sec grub to login prompt, under 2 sec from there to unity).  It takes longer to wake from suspend than to cold boot.

---

### Post by Lekensteyn on 2012-01-19
I and my brother owned both a SSD from OCZ (Vertex 2) and they both died in a similar way (unrecognized disk, at the end your system will hang before POST). I recommend you to backup your disk and do a RMA request if possible.

---

### Post by LinuxFan999 on 2012-01-19
I do not recommend solid state drives. I recommend that you replace the SSD with a mechanical hard drive with at least 1TB of disk space.

---

