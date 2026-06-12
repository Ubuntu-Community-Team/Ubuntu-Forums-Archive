---
title: "Blurry Pixart webcam"
date: 2010-12-22
forum: Hardware
---

### Post by MSPdwalt on 2010-12-22
I have a wide-angle Pixart Webcam.  This is the first webcam that I have connected to this build of Ubuntu amd64.  It was immediately detected and identified as USB_2.0 Camera.  

I installed cheese and it displayed video immediately, but it was really blurry.  There's no manual focusing on the camera so I'm thinking it's a software issue.  I did some research and found a lot of talk about gspca/v4l.  I installed  v4l2uc and motion.  This does not appear to have had an effect.  I also checked and the gspca kernel mod isn't loaded, does that still exist? do I need it?  I tried adjusting settings in the v4l control panel and they didn't seem to have an effect.

Any advice would be greatly appreciated,

-DW  

lsusb:
```

Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 006: ID 045e:0752 Microsoft Corp. 
Bus 001 Device 005: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod

```

Module                  Size  Used by
rfcomm                 40393  7 
sco                     9649  2 
binfmt_misc             7960  1 
bridge                 53216  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  24 rfcomm,bnep
vmnet                  46952  15 
vmblock                12995  1 
vsock                  43304  0 
vmci                   60063  2 vsock
vmmon                  79433  8 
snd_hda_codec_idt      61450  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio          92747  1 
snd_pcm_oss            41394  0 
snd_usb_lib            19193  1 snd_usb_audio
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           1782  0 
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_oss            31191  0 
fbcon                  39270  71 
snd_seq_midi            5829  0 
arc4                    1473  2 
uvcvideo               62595  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
tileblit                2487  1 fbcon
videodev               40518  1 uvcvideo
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
iwlagn                122996  0 
v4l1_compat            15495  2 uvcvideo,videodev
sdhci_pci               6700  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
font                    8053  1 fbcon
iwlcore               125179  1 iwlagn
dell_wmi                2177  0 
nvidia              10832442  51 
sdhci                  17928  1 sdhci_pci
v4l2_compat_ioctl32    11892  1 videodev
btusb                  13001  4 
video                  20623  0 
snd_timer              23649  2 snd_pcm,snd_seq
bitblit                 5811  1 fbcon
usbhid                 41116  0 
softcursor              1565  1 bitblit
hid                    83472  1 usbhid
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                64576  0 
mac80211              238896  2 iwlagn,iwlcore
vga16fb                12757  1 
snd                    71251  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              148725  3 iwlagn,iwlcore,mac80211
serio_raw               4918  0 
led_class               3764  2 iwlcore,sdhci
dcdbas                  6886  0 
intel_agp              29319  0 
vgastate                9857  1 vga16fb
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
ppdev                   6375  0 
parport_pc             29958  1 
parport                37160  3 lp,ppdev,parport_pc
ohci1394               30260  0 
e1000e                136269  0 
ahci                   37870  2 
ieee1394               94771  1 ohci1394

```

---

### Post by MSPdwalt on 2011-01-10
bump

---

