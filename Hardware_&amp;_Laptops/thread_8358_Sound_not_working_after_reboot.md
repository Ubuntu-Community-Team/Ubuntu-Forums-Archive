---
title: "Sound not working after reboot"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by cyb on 2004-12-16
Hi all! :D
I installed Ubuntu today, and everything worked fine. Sound played, I mounted my NTFS partitions, I installed Acrobat Reader and MP3 and video support, nVidia drivers... and then I rebooted my computer.
I now can hear the little drum when the login screen comes up, but after logging in, there's no more sound! None at all, nowhere!
I've been told to put my lspci and lsmod output here too, so here goes:
```
erik@ubuntu:~ $ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```

```
erik@ubuntu:~ $ lsmod
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
snd_via82xx            26660  2
snd_ac97_codec         59268  1 snd_via82xx
snd_mpu401_uart         7296  1 snd_via82xx
via_ircc               20368  0
irda                  167360  1 via_ircc
crc_ccitt               2432  1 irda
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
snd_bt87x              13640  0
bt878                  11184  0
tuner                  18448  0
tda9887                12036  0
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tda9887,bttv,i2c_algo_bit
videodev                9856  1 bttv
tsdev                   7168  0
joydev                  9536  0
usbhid                 28864  0
ehci_hcd               27780  0
snd_usb_audio          65120  0
snd_rawmidi            23232  2 snd_mpu401_uart,snd_usb_audio
snd_seq_device          7944  1 snd_rawmidi
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  4 snd_via82xx,snd_bt87x,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11144  3 snd_via82xx,snd_bt87x,snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  15 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_bt87x,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
audio                  42240  2
soundcore               9824  5 bttv,snd,audio
hci_usb                12928  0
bluetooth              44036  1 hci_usb
uhci_hcd               29328  0
usbcore               104292  8 usbhid,ehci_hcd,snd_usb_audio,audio,hci_usb,uhci_hcd
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  1 via_agp
analog                 10784  0
gameport                4736  2 snd_via82xx,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               6016  2
ntfs                   88660  2
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
evdev                   9088  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
ide_disk               16768  5
ide_core              125272  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  710
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```

I hope you can help me! :D

---

### Post by vontez on 2004-12-16
What happens when you try:
$ sudo alsamixer

This should bring up the alsa volume control, and make sure none of these are muted.

It looks like your sound modules are loading ok, which is a good thing.

---

### Post by cyb on 2004-12-16
It brings up a mixer... some bars were muted, but I don't think they were really important (3D control, line in, microphone, pc speaker...). I unmuted them anyway, but still, no sound. 

Also, when I use XMMS to play a song, it seems to continuously fast forward! Very strange, the bars on the oscilloscope (or whatever it is) do move, but it is like fastforwarding. And still, no sound :(

[edit]When I move the 3D depth bar in alsamixer, I hear a crackling sound, too.

---

### Post by vontez on 2004-12-16
When you are in alsamixer, what does it list in the top left corner for the card?

Perhaps alsa is using your modem sound module?

---

### Post by cyb on 2004-12-17
```

Card: VIA 8233A 
Chip: Realtek ALC101 
Item: Master 
```

---

### Post by cyb on 2004-12-17
When I start the GDM configuring program (Computer --> System Configuration --> Login Screen Setup), and test the sound there, (Accesibility --> Test sound), it works! But it still doesn't work in normal programs or normal session or Gnome! :(

---

### Post by cyb on 2004-12-17
Hell yeah, I fixed it! Woohoo!
What I did is press Alt + F2, start gstreamer-properties, and as audio output, select ALSA! It was configured to output to OSS, and apparently that was wrong  :o 

Thanks for the help anyway! :D

---

