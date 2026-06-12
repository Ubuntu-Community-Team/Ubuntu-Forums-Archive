---
title: "No Sound"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by Russell on 2005-07-27
Installed Ubuntu last night and i like it so far, the only problem i have is that i have absolutely no sound. I'm a complete newbie using Linux and have absolutely no idea as to how to go about fixing this problems.

All the sound equalisers/mixers etc appear to be set at the highest setting and not muted, i imagine Ubuntu does not recognise my hardware?

In the AlsaMixer it says i have a 

Card: Intel 82801BA-ICH2                                                   
 Chip: Realtek ALC200/200P rev 0  

Does anyone know where i can get the drivers and how to install these? or are there other problems?

Thanks for your time.

---

### Post by Russell on 2005-07-27
I tried the following commands in the Terminal, these are the results

lsmod

matthew@cpc5-grim2-4-0-cust244:~$ lsmod
Module                  Size  Used by
isofs                  33720  0
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
emu10k1_gp              3840  0
af_packet              20744  2
snd_emu10k1            81668  0
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd_intel8x0           29984  2
snd_ac97_codec         64608  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  10 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbnet                 25736  0
mii                     4736  1 usbnet
soundcore               9824  3 snd
snd_page_alloc          9604  3 snd_emu10k1,snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
uhci_hcd               30224  0
usbcore               107384  3 usbnet,uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
analog                 10784  0
gameport                4608  2 emu10k1_gp,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
evdev                   9088  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  807
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
matthew@cpc5-grim2-4-0-cust244:~$






 grep snd

Nothing....


lspci

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 12)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 12)
0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 12)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:01.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)


Can anyone make any sense of this????

---

### Post by Russell on 2005-07-27
Please if anyone can make any sense of this, i'd love some help

---

### Post by Curlydave on 2005-07-27
Do you have multiple audio devices, or an onboard sound chip?

---

### Post by Russell on 2005-07-27
I think it's an Intel chip which is built into the PC, it's most probably an on-board chip

---

### Post by varunus on 2005-07-27
It looks to me like you have two sound cards in your computer, an integrated intel one and a Creative Labs Sound Blaster.  Ubuntu is only detecting the intel card.

What I would recommend doing is to go into your BIOS (accomplished by pressing F1 or F12 or DEL or something when you first turn on your computer, different for each one) and disable the onboard sound.  Then, follow this howto to make your sound blaster work:
[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)

Good luck.  And make sure your speakers are connected to the sound blaster and not the integrated intel sound out.

---

### Post by Russell on 2005-07-27
I think your right, i've just looked and low and behold my speakers are plugged into my creative labs card, and not into the inbuilt one (the sockets are free) I'll try that out and report my progress.

---

### Post by Russell on 2005-07-27
just plugged the speakers into the intel chip and they work, i'll try loading the creative labs card now

---

### Post by Russell on 2005-07-27
I got it working, thanks to anyone who participated in this thread!

---

