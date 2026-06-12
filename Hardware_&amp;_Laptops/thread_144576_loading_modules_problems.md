---
title: "loading modules problems"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by kosac on 2006-03-14
Hello, 

I installed ubuntu 5.10 in a Toshiba Satellite M30-742. However it takes too much time loading modules when booting (and it jumps to console mode).

Can anyone help me...

I have the following modules:

Module                  Size  Used by
arc4                    1792  1 
ieee80211_crypt_wep     4928  1 
binfmt_misc            11496  1 
rfcomm                 38460  0 
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
ipv6                  251232  8 
speedstep_centrino      7636  1 
cpufreq_userspace       4316  1 
cpufreq_stats           5252  0 
freq_table              4388  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1696  0 
cpufreq_ondemand        6044  0 
cpufreq_conservative     6948  0 
pcmcia                 26568  2 
video                  15748  0 
toshiba_acpi           10716  0 
tc1100_wmi              6692  0 
sony_acpi               5324  0 
pcc_acpi               11104  0 
hotkey                  9284  0 
dev_acpi               11108  0 
i2c_acpi_ec             5472  0 
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0 
battery                 9348  0 
container               4384  0 
ac                      4708  0 
af_packet              21768  2 
rtc                    12344  0 
pcspkr                  3396  0 
yenta_socket           25292  1 
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
ipw2200               103880  0 
firmware_class          9952  1 ipw2200
ieee80211              29380  1 ipw2200
ieee80211_crypt         5604  3 ieee80211_crypt_wep,ipw2200,ieee80211
ohci1394               34356  0 
snd_intel8x0           33248  1 
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0 
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
tpm_atmel               5536  0 
tpm_nsc                 6656  0 
tpm                     9888  2 tpm_atmel,tpm_nsc
pci_hotplug            27508  0 
intel_agp              23164  1 
dm_mod                 57692  1 
joydev                  9984  0 
tsdev                   7776  0 
snd_seq_dummy           3620  0 
snd_seq_oss            33600  0 
snd_seq_midi            9088  0 
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
evdev                   9664  1 
nvidia               3710980  12 
agpgart                34792  2 intel_agp,nvidia
sr_mod                 17028  0 
sbp2                   22952  0 
scsi_mod              135688  2 sr_mod,sbp2
ieee1394              100792  2 ohci1394,sbp2
psmouse                30116  0 
mousedev               11616  1 
parport_pc             35236  1 
lp                     12292  0 
parport                35912  2 parport_pc,lp
md                     45584  0 
ext3                  136264  1 
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0 
processor              22812  2 speedstep_centrino,thermal
fan                     4484  0 
usbhid                 35264  0 
e100                   34976  0 
mii                     5696  1 e100
ehci_hcd               34248  0 
uhci_hcd               31184  0 
usbcore               118044  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 41572  0 
cdrom                  39616  2 sr_mod,ide_cd
ide_disk               18464  3 
ide_generic             1376  0 
piix                   10372  1 
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  730 
capability              4712  0 
commoncap               6816  1 capability
vesafb                  7992  1 
vgastate                9664  0 
softcursor              2272  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
cfbcopyarea             4608  1 vesafb
fbcon                  38496  72 
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon


Thanks,

kosac

---

### Post by sdb2028 on 2006-03-14
Try this thread:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=speed](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed)

---

### Post by kosac on 2006-03-14
well, i've tried that optimization, but it still freezes in the early beginning.

it says Loading Modules... in the ubuntu starting screen.
then it jumps to console mode an continues saying "Loading Modules". After some waiting it starts moving.

the 2 previous ubuntu realeases had the same problem in my laptop. :cry:

---

