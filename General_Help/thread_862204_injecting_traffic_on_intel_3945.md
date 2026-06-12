---
title: "injecting traffic on intel 3945"
date: 2008-07-17
forum: General Help
---

### Post by malanco on 2008-07-17
hi guys, im trying to make my intel 3945 wifi card to inject traffic and make a wep crack in my own network , im following this guide:

[http://aircrack-ng.org/doku.php?id=ipw3945](http://aircrack-ng.org/doku.php?id=ipw3945)

when i get to the point where i have to remove my ipw3945 driver with this command:

sudo modprobe -r ipw3945

i get this message in the console:

sh: /sbin/ipw3945d-2.6.24-19-generic: not found
FATAL: Module ipw3945 not found.
FATAL: Error running remove command for ipw3945

any help will be appreciated !! :( thanks!

---

### Post by malanco on 2008-07-17
bump

---

### Post by prshah on 2008-07-17
> **malanco said:**
> 
 make my intel 3945 wifi card to inject traffic 
sudo modprobe -r ipw3945

sh: /sbin/ipw3945d-2.6.24-19-generic: not found
FATAL: Module ipw3945 not found.
FATAL: Error running remove command for ipw3945


Well according to this, you're not using the ipw3945 module; have you setup your wifi card using ndiswrapper instead, by any chance? If you have any doubts, post your ```
lsmod
```

---

### Post by malanco on 2008-07-17
hi prshah, it seems that im using iwl3945 driver, heres my lsmod

Module                  Size  Used by
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945
ipwraw                124824  0 
snd_rtctimer            4640  1 
vmnet                  43964  15 
vmblock                16544  3 
vmmon                 945164  8 
binfmt_misc            12808  1 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185500  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ipv6                  267780  16 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
sbs                    15112  0 
dock                   11280  0 
container               5632  0 
sbshc                   7680  1 sbs
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
af_packet              23812  4 
evdev                  13056  8 
serio_raw               7940  0 
psmouse                40336  0 
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
uvcvideo               58116  0 
arc4                    2944  2 
compat_ioctl32          2304  1 uvcvideo
ecb                     4480  2 
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
wmi_acer                9644  0 
ac                      6916  0 
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
battery                14212  0 
snd                    56996  19 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  2 iptable_nat
nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  0 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  2 iptable_nat,ip_tables
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
pata_acpi               8320  0 
r8169                  32900  0 
ata_generic             8324  0 
ahci                   28420  2 
libata                159344  4 ata_piix,pata_acpi,ata_generic,ahci
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   50580  3 
vesafb                  8964  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
agustin@agustin-laptop:~$ 

when i turn down the iwl3945 with modprobe -r iwl3945 it works but , i dont get the wifi0 and rtap0 :(

---

### Post by mexlinux on 2008-07-17
```
modprobe -r iwl3945
```
is to remove the current module, before you can use wifi0 and rtap0 you must first load the new module with:
```
sudo modprobe ipwraw
```

---

