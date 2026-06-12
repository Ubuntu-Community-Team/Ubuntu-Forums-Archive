---
title: "Sound with Toshiba A70-S256"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by mrmcctt on 2005-08-15
I am running kubuntu and have had sound working exactly once.  I followed several threads here about the sound problem and got it working for the remainder of one session.  What I did, I cannot remember.

I have a Toshiba Satellite A70-S256 laptop.  From the detailed specs page at Toshiba, the laptop has a Realtek ALC250 codec chip.

Here is my lspci:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5831 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

Here is my lsmod 

Module                  Size  Used by
radeon                 69760  1
drm                    59412  2 radeon
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
ath_pci                55584  0
ath_rate_onoe           8840  1 ath_pci
wlan                  106588  3 ath_pci,ath_rate_onoe
ath_hal               133328  2 ath_pci
ohci1394               31876  0
snd_atiixp_modem       15908  0
snd_atiixp             18596  0
snd_ac97_codec         64608  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
tsdev                   7488  0
snd                    50276  7 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_atiixp_modem,snd_atiixp,snd_pcm
usbhid                 29376  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usbhid,ehci_hcd,ohci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
ati_agp                 8204  1
agpgart                31784  2 drm,ati_agp
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  3
atiixp                  6160  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   26164  428
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

Here is the lsmod | grep snd

snd_atiixp_modem       15908  0
snd_atiixp             18596  0
snd_ac97_codec         64608  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  7 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_atiixp_modem,snd_atiixp,snd_pcm

Here is aplay -l

**** List of PLAYBACK Hardware Devices ****
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have done a default install of  kubuntu and added very little.  (Firefox and some wallpaper)

Any ideas where to go with this?  Help is appreciated. ](*,)

I should add that I get an error stating that:

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Nosuch device)
The sound server will continue, using the null output device.

Attempting to open kmixer shows no current mixer so I cannot check volume levels.

---

### Post by Mapassy on 2005-08-16
Hi there  :) 

No worries:-)
I had same or similar prob when I was running Linspire 5. I  gave up 
and moved to UBUNTU. After installation the SOUND WAS Perfect.
I have got the same ATI IXP MC97  on my laptop (Acer 2200)
I did try to find where the problem was when I was running Linspire, and installed
KDE, plus lots of packages. I discovered that the sound is missing because of the lack of a streamer (it is connected with the default media player)
I installed a package and the streamer was removed , and the sound as well. Installing it back  and THE MUSIC came back. 
So check your packages or move to Gnome
I am also newbie but i think this will help :-) :grin:

---

### Post by mrmcctt on 2005-08-16
The frustrating thing is that the sound works every other boot.  I'm still working it.

I'll check out what you said and see what happens.

---

### Post by Mapassy on 2005-08-18
I have sorted the sound issue :grin: 

For xmms - esound plugin - PERFECT
Check the unofficial guide for Ubuntu. 
There is How to for the sound improvement.
I tried and it works :-)
Check and the sound controler, onece it was turned down, I though
it ias a sound prob (somethimes someone is blind :roll: )

Hopefully U will find the solution :-)

---

