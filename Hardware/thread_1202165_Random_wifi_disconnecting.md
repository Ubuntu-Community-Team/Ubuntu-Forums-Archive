---
title: "Random wifi disconnecting"
date: 2009-07-01
forum: Hardware
---

### Post by 2LSS on 2009-07-01
For starters I'm using a sony vaio vgn-fz140e with hardy and kernel 2.6.24-24-generic 
My internet connection keeps randomly dropping, one minute I'm surfing the web th next minute firefox cant load the page.
I still have a full connection to my router but no internet. At first I thought it was a problem with the router but the computer next to me is running xp and it does not have this problem.
Usually I can fix it by reconnecting to my router or disable then enable my networking.
From what I can tell from google my driver is up to date
Here is my card
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

and my lsmod,
Module                  Size  Used by
ipv6                  267908  10 
af_packet              23812  4 
i915                   32512  2 
drm                    82452  3 i915
bluetooth              61028  0 
binfmt_misc            12808  1 
sonypi                 23192  0 
acpi_cpufreq           10796  2 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
parport                37832  1 lp
snd_hda_intel         346136  4 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
iwl4965               185092  0 
iwlcore               153668  1 iwl4965
snd_seq_oss            35584  0 
lbm_iwl_mac80211      242292  2 iwl4965,iwlcore
rfkill                  8596  2 iwlcore
led_class               6020  1 iwlcore
uvcvideo               60936  0 
snd_seq_midi            9376  0 
compat_ioctl32          2304  1 uvcvideo
snd_rawmidi            25760  1 snd_seq_midi
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
lbm_iwl_cfg80211       33248  3 iwl4965,iwlcore,lbm_iwl_mac80211
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sky2                   47620  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               8576  0 
sony_laptop            35292  0 
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
serio_raw               7940  0 
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19856  0 
output                  4736  1 video
intel_agp              25492  1 
psmouse                40336  0 
iTCO_wdt               13092  0 
ac                      6916  0 
pcspkr                  4224  0 
evdev                  13056  10 
button                  9232  0 
battery                14212  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
ata_piix               19588  0 
ata_generic             8324  0 
sd_mod                 30720  6 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_acpi               8320  0 
ahci                   28548  5 
ohci1394               33584  0 
libata                159600  4 ata_piix,ata_generic,pata_acpi,ahci
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   50708  7 
vesafb                  8964  1 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit

Here is a syslog of when my internet quit working. In disabled/enabled my networking a couple of times to get it to work
[http://pastebin.com/m12b11370](http://pastebin.com/m12b11370)

Can somebody please point me in the right direction

---

### Post by hifimusic on 2010-02-03
I have the same problem with my Vaio FZ140e (ie the wifi disconnecting randomly) 

In my case the problem seems to be with the wifi hard switch on the front of the laptop which needs to be pushed around to get it to work every once in a while.

---

### Post by Enigmapond on 2010-02-03
I had the same problem. I fixed it by installing wigd as a network manager. It seems to work better for me plus the icon is better..:)

Cheers!

---

