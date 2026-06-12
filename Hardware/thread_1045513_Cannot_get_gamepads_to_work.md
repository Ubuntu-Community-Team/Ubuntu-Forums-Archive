---
title: "Cannot get gamepads to work"
date: 2009-01-20
forum: Hardware
---

### Post by Fudoublez on 2009-01-20
So, I've been using ubuntu for about two years now and have been able to manage to solve a lot of my problems by searching the fourms... This time however isn't the case.

I have tried a lot of different suggestions on getting a gamepad to work under Intrepid. I have a Red Ocatane Xplorer (USB) and a MS Sidewinder gamepad (gameport) and need help getting the to work.

For the Sidewinder- ive modprobed joydev, analog, sidewinder, and emu10k1_gp, then tried to calibrate using jscalibrator. After m-prob the analog the jscal shows erratic behavior with the buttons and the dpad shows nothing. It says it is a 4axis 4button controller.

I have a SB Live! 5.1. and lsmod is as follows:
Module                  Size  Used by
usb_storage            82752  0 
libusual               30356  1 usb_storage
af_packet              25728  0 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ipv6                  263972  12 
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
container              11520  0 
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
ac                     12292  0 
sidewinder             19328  0 
joydev                 18368  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  3 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
evdev                  17696  6 
snd_seq_oss            38528  0 
pcspkr                 10624  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
k8temp                 12416  0 
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp             10880  0 
snd                    63268  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gameport               19468  3 sidewinder,emu10k1_gp
soundcore              15328  1 snd
ndiswrapper           196380  0 
nvidia               6909268  36 
agpgart                42184  1 nvidia
button                 14224  0 
i2c_nforce2            14468  0 
i2c_core               31892  2 nvidia,i2c_nforce2
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  8 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_amd               18692  5 
sata_nv                30600  0 
pata_acpi              12160  0 
libata                178208  4 ata_generic,pata_amd,sata_nv,pata_acpi
ohci_hcd               32016  0 
ehci_hcd               43788  0 
scsi_mod              155212  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
usbcore               149360  7 usb_storage,libusual,ndiswrapper,usbhid,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  7 

 dmesg | grep "sidewinder"    brings back this:
[   31.509258] sidewinder.c: unknown joystick device detected on pci0000:04:06.1/gameport0, contact <vojtech@ucw.cz>
[   31.509265] sidewinder.c: ID packet, 18 bits. [3bfff]
[   31.509271] sidewinder.c: Data packet, 18 bits. [fbfff]



I've installed the joystick pack and can't get jstest to do much of anything but give me an error.


as for the Xplorer--  i know i need something called xpad but dont know what or where to get it



Any help would be appreciated

---

