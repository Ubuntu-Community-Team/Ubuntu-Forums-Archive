---
title: "No sound - ATIIXP"
date: 2004-11-05
forum: Hardware &amp; Laptops
---

### Post by maxpower on 2004-11-05
I have a Compaw Presario R3000 which has a ATI IXP sound card.  This card works flawlessly in Fedora but not so well in Ubuntu.  Right after install alsa did not find any cards.  No problem, I set pci=noacpi in grub just as in Fedora and after a reboot alsa found my card.  I installed totem-xine and gstreamer-mad.  When I try WAVs or MP3s in Rhythmbox I get one repeated sound until I forcefully kill Rhythmbox. Xmms plays music without problems.  Totem does the same as rhythmbox.  Xine does not even try to play music.  Also, the first time gnome loaded the startup sound got stuck and repeated and gnome never loaded.  I killed esd from a shell and gnome loaded.  I thin turned esd off in gconf.  Any help would be greatly appreciated.

lspci
[code]
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5833 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.2 System peripheral: Texas Instruments: Unknown device 8201 (rev 01)
0000:02:07.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
[code]

lsmod
[code]
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  4
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
ehci_hcd               27780  0
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
ohci1394               32004  0
snd_atiixp             19880  3
snd_ac97_codec         59268  1 snd_atiixp
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_atiixp,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc         11144  2 snd_atiixp,snd_pcm
joydev                  9536  0
usbhid                 28864  0
ohci_hcd               19460  0
usbcore               104292  5 ehci_hcd,usbhid,ohci_hcd
pci_hotplug            30640  0
ati_agp                 8332  1
agpgart                31784  1 ati_agp
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  3
atiixp                  8472  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   25904  668
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
[code]

mAx

---

### Post by im_ka on 2004-11-06
if xmms plays sound and rhythmbox/totem doesn't, the problem must be gstreamer (it's used by rhythmbox/totem).

run
```
gstreamer-properties
```
to set it.

i have oss with alsasrc as input

have a look at options/preferences in xmms and see how oss is set there. that should work in gstreamer as well.
e.g: i have my sound on /dev/dsp1, therefore my output in gstreamer-properties is user defined and
```
osssink device=/dev/dsp1
```

hth

---

### Post by maxpower on 2004-11-08
[QUOTE=im_ka]if xmms plays sound and rhythmbox/totem doesn't, the problem must be gstreamer (it's used by rhythmbox/totem).

run
```
gstreamer-properties
```
to set it.

i have oss with alsasrc as input

have a look at options/preferences in xmms and see how oss is set there. that should work in gstreamer as well.
e.g: i have my sound on /dev/dsp1, therefore my output in gstreamer-properties is user defined and
```
osssink device=/dev/dsp1
```

hth[/QUOTE]
 I tried what you suggested with no luck.  I did some playing around and this is what I have got so far. XMMS and BMP work fine. Rhythmbox, Totem-Xine, Totem-Gstreamer, Xine, and madplay all will play the first clip of audio repeatedly and then freeze until I forcefully kill the app.  I have read online that the 2.6.8 kernel has some problems with this sound card but I find it quite strange that XMMS works quite well.

mAx

---

### Post by mcapozzi on 2004-11-12
Having similar issue, no sound through GNOME.

I've Googled, I've searched the forum, all to no avail.

I've tried the pci=noacpi trick, no dice.

lsmod contains the following:

Module                  Size  Used by
tsdev                   7488  0
acpi                    6432  0
proc_intf               4128  0
cpufreq_powersave       1952  0
cpufreq_userspace       7072  4
freq_table              4512  1 acpi
ds                     18756  2
button                  6808  0
ac                      5036  0
battery                 9612  0
ipv6                  273956  10
af_packet              23496  2
wlan_wep                6752  1
yenta_socket           21248  0
pcmcia_core            69108  2 ds,yenta_socket
8139cp                 21792  0
8139too                27008  0
mii                     5280  2 8139cp,8139too
crc32                   4512  2 8139cp,8139too
ath_pci                57124  0
wlan                  119036  3 wlan_wep,ath_pci
ath_hal               129520  2 ath_pci
ohci1394               36004  0
snd_atiixp             22088  0
snd_ac97_codec         68772  1 snd_atiixp
snd_pcm_oss            53864  0
snd_mixer_oss          19744  1 snd_pcm_oss
snd_pcm                99552  2 snd_atiixp,snd_pcm_oss
snd_timer              26756  1 snd_pcm
snd                    57828  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10688  1 snd
snd_page_alloc         11688  2 snd_atiixp,snd_pcm
ehci_hcd               32068  0
ohci_hcd               21924  0
usbcore               119044  4 ehci_hcd,ohci_hcd
pciehp                 96908  0
shpchp                100364  0
pci_hotplug            34716  2 pciehp,shpchp
ati_agp                 8684  1
agpgart                34316  1 ati_agp
irtty_sir               9760  0
sir_dev                20092  1 irtty_sir
irda                  204480  2 irtty_sir,sir_dev
crc_ccitt               2336  1 irda
pcspkr                  3884  0
rtc                    14088  0
md                     50184  0
dm_mod                 58592  1
capability              4744  0
commoncap               7392  1 capability
evdev                   9696  0
parport_pc             35680  0
lp                     11044  0
parport                42216  2 parport_pc,lp
sbp2                   24488  0
ieee1394              110744  2 ohci1394,sbp2
ide_cd                 42180  0
mousedev               10480  1
psmouse                19976  0
sr_mod                 17316  0
scsi_mod              125412  2 sbp2,sr_mod
cdrom                  39808  2 ide_cd,sr_mod
reiserfs              245488  1
ext2                   72616  0
ext3                  126344  1
jbd                    68952  1 ext3
mbcache                10148  2 ext2,ext3
ide_generic             1632  0
ide_disk               19136  4
atiixp                  9272  1
ide_core              138896  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   30576  719
fan                     4204  0
thermal                13232  0
processor              18272  2 acpi,thermal
font                    8576  0
vesafb                  6784  0
cfbcopyarea             3936  1 vesafb
cfbimgblt               3296  1 vesafb
cfbfillrect             3840  1 vesafb

Please help...

Thanks
-Mike

---

### Post by rantamplan on 2004-11-16
Same computer as MAXPOWER same problem.
I think it must be a sound server problem. If you
enable your sound server and the events in
Prefences>sound, you will have Gnome apps sound
but mplayer,Xine, Xmms doesnt work. And the Opposite
, disabling it gnome will not work and the other apps will do.
Sorry for my english.
Thnks.
Rantamplan

---

### Post by maxpower on 2004-11-17
[QUOTE=rantamplan]Same computer as MAXPOWER same problem.
I think it must be a sound server problem. If you
enable your sound server and the events in
Prefences>sound, you will have Gnome apps sound
but mplayer,Xine, Xmms doesnt work. And the Opposite
, disabling it gnome will not work and the other apps will do.
Sorry for my english.
Thnks.
Rantamplan[/QUOTE]
 You can get mplayer and xine to work by disabling the gnome sound server?

mAx

---

### Post by rantamplan on 2004-11-17
Yes I can. Tell me what configuration do you need.
Rantamplan

---

### Post by Aegir on 2004-11-17
I'm suffering from similar problems. I have swapped from Mandrake 10.1 to Ubuntu, And I get no sound either.

Im running a Acer Extensa 2000, Which also uses an ATIIXP sound card.

When I boot I get a no sound cards error, I tried the pci=noacpi trick mentioned above, But it still doesnt detect my card.

When I do an lsmod, I dont get anything with atiixp in it in the list.

What can I do short of compiling a new kernel?

---

### Post by Rancoras on 2004-11-17
Moved: Hardware problem

---

### Post by rantamplan on 2004-11-18
Try just "noapic" instead "pci=noacpi"
Rantamplan

---

