---
title: "Leadtek Winfast 2000XP Expert have video but no tv"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by biohazardousguy on 2007-07-20
Hi guys,
I have an rather silly problem. 
My Leadtek Winfast 2000XP Expert card does not wants to show any tv. It works perfectly with the composite1 in tvtime, but when I switch to tv i have a blue screen and no signal message.
Im running edgy.

lsmod shows

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
button                  8720  0 
sbs                    15652  0 
ac                      6020  0 
asus_acpi              17308  0 
i2c_ec                  5888  1 sbs
battery                10756  0 
backlight               7040  1 asus_acpi
container               5248  0 
dock                   10268  0 
video                  16388  0 
af_packet              23816  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14208  2 
fat                    53916  1 vfat
w83627hf               26256  0 
hwmon_vid               4224  1 w83627hf
i2c_isa                 6272  1 w83627hf
eeprom                  8336  0 
lp                     12452  0 
fuse                   46612  3 
snd_mpu401              9256  0 
snd_via82xx            29208  1 
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  2 snd_mpu401,snd_via82xx
tuner                  61864  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
cx8800                 35212  0 
cx88xx                 67364  1 cx8800
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ir_common              31236  1 cx88xx
via_ircc               27540  0 
irda                  201276  1 via_ircc
crc_ccitt               3072  1 irda
i2c_algo_bit            8712  1 cx88xx
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
analog                 12832  0 
i2c_viapro             10132  0 
serio_raw               7940  0 
video_buf              26116  2 cx8800,cx88xx
tveeprom               15888  1 cx88xx
compat_ioctl32          2304  1 cx8800
btcx_risc               5896  2 cx8800,cx88xx
snd                    54020  14 snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gameport               16520  2 snd_via82xx,analog
i2c_core               22784  9 i2c_ec,w83627hf,i2c_isa,eeprom,tuner,cx88xx,i2c_algo_bit,i2c_viapro,tveeprom
psmouse                38920  0 
videodev               28160  2 cx8800,cx88xx
v4l2_common            25216  3 tuner,cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev
via_agp                11264  1 
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 drm,via_agp
soundcore               8672  1 snd
ipv6                  268704  14 
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  8 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
usbhid                 26592  0 
hid                    27392  1 usbhid
via82cxxx              10372  0 [permanent]
floppy                 59524  0 
ehci_hcd               34188  0 
via_rhine              25608  0 
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  3 via_rhine,8139too,8139cp
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

If i do

mm@slave:~$ dmesg | grep cx88
[   21.456000] CORE cx88[0]: subsystem: 107d:6611, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[   21.608000] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=38, eeprom[0]=0x01
[   21.608000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input5
[   21.608000] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 20, latency: 32, mmio: 0xe2000000
[   21.656000] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   21.660000] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   21.672000] cx88[0]/0: registered device video0 [v4l2]
[   21.672000] cx88[0]/0: registered device vbi0
[   21.672000] cx88[0]/0: registered device radio0

So the tuner is not bt878 based, it has a different chipset i think.

I did some research and found that the tuner should work 
[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/) but with card=5 tuner=43.

Now, how should I force this options? I believe that the tuner is the problem, as it is not the right one.

I tried all that passed through my linux nob mind, like:
sudo modprobe cx8800 card=5 tuner=43
modprobe cx88xx card=5 tuner=43
sudo modprobe tuner  tuner=43
sudo modprobe bttv card=5 tuner=43
Nothing seems to work.
Please help

---

### Post by biohazardousguy on 2007-07-21
No idea anyone?

---

### Post by biohazardousguy on 2007-07-22
Is this the wrong section to ask?

---

### Post by nimrod_abing on 2007-07-22
Just the other day I was looking at buying one of these (exact same brand and model) myself. Good thing I did not rush to buy one. If you do manage to get it working eventually, please post your results here.

As for this being the wrong section to ask this kind of question, I would have posted it here since it says Hardware & Laptops and this is a hardware issue. Though I think Multimedia & Video would also be appropriate.

Maybe you should try to open two terminal windows. On one terminal window, run:

```
tail -f /var/log/messages
```Then you use the other terminal window to execute your modprobe commands. This should allow you to see what is going on when you run modprobe. It wouldn't hurt to add the verbose option to modprobe either.

---

### Post by beefbowel on 2007-11-11
anyone?

i have the same card and would like some help.  i actually spent three days trying to look for an answer.  :confused:

---

