---
title: "Video problem"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ^graff_epsilon on 2009-04-24
Upon running either mplayer or totem and then opening either an alt-f2 run window, or any other program, the screen spits out a bunch of blue and black lines and then tosses me out of my login and into the GDM prompt. Additionally, if I close the video it works again (I can open other programs) yet if I switch to a tty terminal it spits out that same screwy screen except on the alt-f8 "video terminal". Any suggstions? X61 Tablet, whichever intel chip that gives. Here's the output of an lsmod:

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
ipv6                  263972  10 
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
vmnet                  48580  13 
ppdev                  15620  0 
parport_pc             39204  0 
vmblock                21156  3 
vmci                   58964  0 
vmmon                  78064  0 
container              11520  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
sbp2                   29324  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
arc4                    9984  2 
snd_rawmidi            29824  1 snd_seq_midi
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
iwlagn                 99588  0 
pcmcia                 43052  0 
iwlcore                92740  1 iwlagn
thinkpad_acpi          66176  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rfkill                 17176  3 iwlcore,thinkpad_acpi
sdhci_pci              15360  0 
mac80211              216820  2 iwlagn,iwlcore
yenta_socket           31756  1 
sdhci                  23940  1 sdhci_pci
snd                    63268  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         19072  1 yenta_socket
intel_agp              33724  1 
serio_raw              13444  0 
led_class              12164  2 iwlcore,thinkpad_acpi
iTCO_wdt               18596  0 
cfg80211               32392  3 iwlagn,iwlcore,mac80211
pcspkr                 10624  0 
agpgart                42184  3 drm,intel_agp
soundcore              15328  1 snd
video                  25104  0 
mmc_core               58268  1 sdhci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                45200  0 
nvram                  16524  1 thinkpad_acpi
evdev                  17696  13 
output                 11008  1 video
bay                    12160  0 
battery                18436  0 
ac                     12292  0 
button                 14224  0 
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ata_piix               24580  3 
ohci1394               37936  0 
libata                177312  3 pata_acpi,ata_generic,ata_piix
scsi_mod              155212  4 sbp2,sd_mod,sg,libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  3 ehci_hcd,uhci_hcd
e1000e                112680  0 
dock                   16656  2 bay,libata
thermal                23708  0 
processor              42156  3 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by ^graff_epsilon on 2009-04-24
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

This may work, am testing now.

---

### Post by ^graff_epsilon on 2009-04-24
Works, except it disabled the right click functionality of the stylus.

---

