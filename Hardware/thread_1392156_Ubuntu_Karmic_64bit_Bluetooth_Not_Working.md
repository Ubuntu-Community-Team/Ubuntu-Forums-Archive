---
title: "Ubuntu Karmic 64bit Bluetooth Not Working"
date: 2010-01-27
forum: Hardware
---

### Post by idyle on 2010-01-27
Hi everyone!

Been TRYING to get my bluetooth working on my Asus X83V but /etc/init.d/bluetooth start gives me no output, and it appears the bluetooth module isn't loaded!?

```
tyler@tyler-desktop:~$ sudo modprobe bluetooth
[sudo] password for tyler: 
FATAL: Module bluetooth not found.
```

```

tyler@tyler-desktop:~$ lsmod
Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetflt            100300  0 
vboxnetadp             93292  0 
vboxdrv              1708524  1 vboxnetflt
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 13088  0 
arc4                    2144  2 
snd                    77096  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ecb                     3296  2 
iwlagn                124832  0 
iwlcore               133600  1 iwlagn
raw1394                29096  0 
soundcore               9088  1 snd
lp                     11908  0 
mac80211              210008  2 iwlagn,iwlcore
uvcvideo               65260  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
parport                40528  2 ppdev,lp
psmouse                57124  0 
nvidia              10316904  38 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
iptable_filter          3872  0 
cfg80211              109144  3 iwlagn,iwlcore,mac80211
ip_tables              21200  1 iptable_filter
asus_laptop            21092  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
x_tables               25832  1 ip_tables
v4l2_compat_ioctl32    13344  1 videodev
serio_raw               6596  0 
led_class               5256  3 iwlcore,sdhci,asus_laptop
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
vesafb                  7176  1 
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  2 raw1394,ohci1394
intel_agp              32816  0 
video                  23612  0 
output                  3680  1 video
r8169                  38884  0 
mii                     6368  1 r8169

```

I'm running the 64bit kernel:

```
tyler@tyler-desktop:~$ uname -a
Linux tyler-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
```

Everything is up to date: 

```
tyler@tyler-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

What can I do to get bluetooth working so I can sync my phone and put music on it?!

Thanks!
- Tyler

---

### Post by idyle on 2010-01-28
Bump :/

---

### Post by idyle on 2010-01-29
Last bump 'til thread death! O_O

---

### Post by captain_rob on 2010-01-31
I have the same problem with 9.10 64 bits and it irritates me, because I had no problems wihen I used 9.04. 

Installing blueman gives me only randomly the opportunity to make a connection. Besides, after installing blueman I see now on the panelthe normal bluetooth and the blueman icon. Is that normal?

---

### Post by efflandt on 2010-01-31
What makes you think there is a "bluetooth" module:

/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/bcm203x.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/bfusb.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/bluecard_cs.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/bpa10x.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/bt3c_cs.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/btsdio.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/btuart_cs.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/btusb.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/dtl1_cs.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/hci_uart.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/bluetooth/hci_vhci.ko

What does your Bluetooth device show up as in **lspci** (or **lsusb** if external)?

```
$ lsusb | grep tooth
Bus 002 Device 007: ID 22b8:0850 Motorola PCS Bluetooth Device
$ lsmod | grep bt
btusb                  14260  0
```

---

