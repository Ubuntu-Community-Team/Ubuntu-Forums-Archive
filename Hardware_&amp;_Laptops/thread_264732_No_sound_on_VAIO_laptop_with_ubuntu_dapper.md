---
title: "No sound on VAIO laptop with ubuntu dapper"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by irsic on 2006-09-25
Everything works quite well on ubuntu dapper, except I can't get any sound. No sound at start, nor when I want to lisetn to CD or anything.
I am running ubuntu on laptop VAIO VGN-B3VP. I have a an Intel 82801DB-ICH4 sound card that works ok on Mandriva Linux 2006.
I surfed on the net a bit, not much I admit, but none of the solutions I found actually worked for me.
when I type in console:

aplay -l
I get:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1

it seems ok for me so far.
I have checked Multimedi Systems selector and both i/o are set to ALSA.
I also checked alsamixer and everything seems fine. Though I don't have alsaconf but that shouldn't be the problem right?
Also checed dmesg, /var/log/messages and /var/log/syslog but in none I can't find anything about any audio device or sound device or activity. Under /dev/ I have snd.
here's my complete lsmod if it helps:

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
sonypi                 23084  0
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265728  6
nls_utf8                2176  2
ntfs                  103536  2
dm_mod                 58936  1
af_packet              22920  4
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
pcmcia                 40508  0
joydev                 10048  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
e100                   40580  0
mii                     5888  1 e100
ipw2200               107308  0
usbhid                 39904  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
tsdev                   8000  0
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
hw_random               5652  0
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36100  0
rtc                    13492  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
serio_raw               7300  0
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272 1 fbcon
softcursor              2304  1 bitblit

I found this especially interesting:

snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd

everything seems ok.
the funny thing is also when I try:

lspci | fgrep 'audio'
i got
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

which seems fine too.
I really don't know what could be the problem so can anyone give me a tip?
tnx

---

### Post by Kateikyoushi on 2006-09-25
Did you try it with a headphone ?

---

### Post by irsic on 2006-09-25
No. never use headphones on my computer.
But in the mean time I found what's wrong
How stupid of me I haven't noticed it yet. All I had to do was to mute External Amplifier in alsamixer.
tnx anyway

---

### Post by Kateikyoushi on 2006-09-25
I had no sound after install as well and it was because of the default alsamixer settings.
I just wanted to know whether you get sound on the jack out because then the soundcard works just your alsamixer settings are borked.
Glad you made it.

---

### Post by irsic on 2006-09-25
My soundcard works fine. It was just my alsamixer controls wrong.I fixed that now...
it works fine on my headphones now. it shouldn't worked before for as I said, external amplifier wasn't muted.

---

### Post by grandmaster on 2006-10-24
> **irsic said:**
> No. never use headphones on my computer.
But in the mean time I found what's wrong
How stupid of me I haven't noticed it yet. All I had to do was to mute External Amplifier in alsamixer.
tnx anyway

Arrrrgggh two hours i was faffing around until i read this post.
The external amp is hidden in dapper 

 good man!!!!

---

### Post by mmpsych on 2007-02-18
> **grandmaster said:**
> Arrrrgggh two hours i was faffing around until i read this post.
The external amp is hidden in dapper 

 good man!!!!
I have a VAIO VGN-FS315B and have never been able to get any sound out of it, despite my UBUNTU appearing to recognise the HDA Intel card and Realtek ALC260 chip correctly. I hope it's the same problem, but I can't for the life of me find the infamous "External Amplifier" ANYWHERE. The only channels that my ASLA mixer (alsamixergui) has are Headphones, PCM, Front, Front Mic, Line, CD, Mic, PC Speaker, Mono, Capture, Capture 1, Input Source and Input Source 1. Right-clicking has no effect anywhere. I also tried KMix, with no success either. I'm going mad !

:-( Michael.

---

