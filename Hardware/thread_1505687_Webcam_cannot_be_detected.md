---
title: "Webcam cannot be detected"
date: 2010-06-09
forum: Hardware
---

### Post by agamjain on 2010-06-09
I own an HCL MILEAP MV02 and I am running Ubuntu 10.04 Netbook Remix on it. It has got a VGA webcam. But when I use Cheese to run my webcam, it says "No device found". What should I do?:confused:

---

### Post by bashologist on 2010-06-09
I don't know, but what I would try is running cheese as root to see if it's a permission problem. Good luck.

---

### Post by agamjain on 2010-06-09
Thanks. I will try that. But can you tell me how to do that?

---

### Post by bashologist on 2010-06-09
I don't have cheese installed right now but I would imagine it's something like "sudo cheese", or "gksudo cheese", either one should work.

---

### Post by agamjain on 2010-06-09
I managed to run Cheese as root, but I am still receiving the same error.

---

### Post by bashologist on 2010-06-09
Cheese should have a dropbox somewhere for you to select the input. Do you see an empty dropbox? What's your webcam called? Is it physically attached to your laptop or is it connected with usb?

Paste this command in a code tag to give us some information.
```
lspci; lsusb; lsmod; dmesg | egrep -i "error|warn|webcam|video"
```

---

### Post by Sam Fallow on 2010-06-09
I can't get cheese to run with my webcam, but it is detected and works fine with guvcview (and possibly others).

Try that and see if it's a cheesy problem.

---

### Post by agamjain on 2010-06-09
I get the following result when I type in the code you said:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
Bus 005 Device 002: ID 14e1:6000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 05c8:0109 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 18e8:6238 Qcom 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Module                  Size  Used by
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
rfcomm                 33421  0 
sco                     7885  0 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  0 
l2cap                  30624  4 rfcomm,bnep
btusb                  10925  0 
bluetooth              49892  5 rfcomm,sco,bnep,l2cap,btusb
aes_i586                7268  94 
aes_generic            26863  1 aes_i586
xt_TCPMSS               2931  1 
xt_tcpmss               1197  1 
xt_tcpudp               2011  1 
iptable_mangle          2771  1 
ip_tables               9991  1 iptable_mangle
x_tables               14299  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                   8943  2 
pppox                   2074  1 pppoe
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  1 
snd                    54148  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt73usb                22434  0 
rsrc_nonstatic         10015  1 yenta_socket
crc_itu_t               1371  1 rt73usb
soundcore               6620  1 snd
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               3690  0 
sdhci_pci               5470  0 
rt2x00usb               9703  1 rt73usb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
sdhci                  15462  1 sdhci_pci
tifm_core               6045  1 tifm_7xx1
rt2x00lib              27509  2 rt73usb,rt2x00usb
led_class               2864  2 sdhci,rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
lp                      7028  0 
psmouse                63245  0 
joydev                  8708  0 
parport                32635  2 ppdev,lp
serio_raw               3978  0 
fbcon                  35102  73 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  282354  5 
drm_kms_helper         29297  1 i915
intel_agp              24177  2 i915
drm                   162471  6 i915,drm_kms_helper
usbhid                 36110  0 
r8169                  33980  0 
i2c_algo_bit            5028  1 i915
agpgart                31724  2 intel_agp,drm
mii                     4381  1 r8169
hid                    67032  1 usbhid
video                  17375  1 i915
output                  1871  1 video
[    0.357846] pci 0000:00:02.0: Boot video device
[    2.440623] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.440849] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[ 3553.473192] Linux video capture interface: v2.00
[ 3553.538381] uvcvideo: Found UVC 1.00 device FO13FF-68 PC-CAM (05c8:0109)
[ 3553.542476] usbcore: registered new interface driver uvcvideo
[ 3553.542484] USB Video Class driver (v0.1.0)
[ 3828.197021] uvcvideo: Found UVC 1.00 device FO13FF-68 PC-CAM (05c8:0109)
[ 3831.312767] uvcvideo: Found UVC 1.00 device FO13FF-68 PC-CAM (05c8:0109)
[17503.396787] uvcvideo: Found UVC 1.00 device FO13FF-68 PC-CAM (05c8:0109)

---

### Post by agamjain on 2010-06-09
I see a dropbox, but I am unable to select any of the options as they are all readonly at the moment. My webcam is physically attached to my system.

---

### Post by bashologist on 2010-06-09
Why didn't you put the output in a code tag?

Code tags looks like this.

```
I'M A CODE TAG, I MAKE POSTS READABLE
```

Does "mplayer tv://" do anything?

---

### Post by maestrobwh1 on 2010-06-09
Although cheese detected mine, it did not work properly... then I found guvcview, and it does.  Might want to try to install that.  It is in the lucid repos.

---

### Post by agamjain on 2010-06-10
I restarted my system after typing the previous commands. And now it seems to be working fine. I will tell you if I face any problems in the future. Thanks a lot for your help. It really made my day.
P. S. Can you tell me how to write that code tag thing?

---

### Post by zebraneo on 2010-11-03
I have the same problem and here are my results

me@me-laptop:~$ lspci; lsusb; lsmod; dmesg | egrep -i "error|warn|webcam|video"
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 006 Device 004: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 046d:0802 Logitech, Inc. Webcam C200
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Module                  Size  Used by
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
isofs                  30022  0 
udf                    79366  0 
crc_itu_t               1383  1 udf
michael_mic             1744  4 
arc4                    1165  2 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  1 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
joydev                  8735  0 
snd_usb_audio          86704  3 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep               5040  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
i915                  291004  3 
snd_seq_midi_event      6047  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2852  0 
drm                   168054  4 i915,drm_kms_helper
wl                   1959533  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
snd                    49006  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
lib80211                5058  2 lib80211_crypt_tkip,wl
psmouse                59033  0 
soundcore                880  1 snd
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  0 
ahci                   19013  0 
libahci                21667  3 ahci
sky2                   45127  0 
[    0.508762] pci 0000:00:02.0: Boot video device
[   27.176950] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   28.305169] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   28.305235] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   28.305319] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   38.472456] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[14832.524764] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[14837.233729] video LNXVIDEO:01: Restoring backlight state
[14839.109839] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[22695.554920] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[22700.586173] video LNXVIDEO:01: Restoring backlight state
[22703.000440] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[47050.097731] Linux video capture interface: v2.00
[47050.331933] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
[47050.347770] usbcore: registered new interface driver uvcvideo
[47050.347773] USB Video Class driver (v0.1.0)
[47081.800695] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
[55560.855608] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[55565.262422] PM: resume of drv:uvcvideo dev:2-3:1.0 complete after 107.316 msecs
[55565.262429] PM: resume of drv:uvcvideo dev:2-3:1.1 complete after 107.303 msecs
[55566.611614] video LNXVIDEO:01: Restoring backlight state
[55570.075727] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[57193.946879] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
me@me-laptop:~$

---

### Post by zebraneo on 2010-11-03
I am having the same problem here are my results
What do I so I see myself in the test of skype but I can't choose a webcam it doesn't let me, it's like skype can't detect my webcam what do I do 
Thanks you


me@me-laptop:~$ lspci; lsusb; lsmod; dmesg | egrep -i "error|warn|webcam|video"
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 006 Device 004: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 046d:0802 Logitech, Inc. Webcam C200
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Module                  Size  Used by
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
isofs                  30022  0 
udf                    79366  0 
crc_itu_t               1383  1 udf
michael_mic             1744  4 
arc4                    1165  2 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  1 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
joydev                  8735  0 
snd_usb_audio          86704  3 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep               5040  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
i915                  291004  3 
snd_seq_midi_event      6047  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2852  0 
drm                   168054  4 i915,drm_kms_helper
wl                   1959533  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
snd                    49006  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
lib80211                5058  2 lib80211_crypt_tkip,wl
psmouse                59033  0 
soundcore                880  1 snd
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  0 
ahci                   19013  0 
libahci                21667  3 ahci
sky2                   45127  0 
[    0.508762] pci 0000:00:02.0: Boot video device
[   27.176950] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   28.305169] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   28.305235] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   28.305319] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   38.472456] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[14832.524764] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[14837.233729] video LNXVIDEO:01: Restoring backlight state
[14839.109839] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[22695.554920] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[22700.586173] video LNXVIDEO:01: Restoring backlight state
[22703.000440] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[47050.097731] Linux video capture interface: v2.00
[47050.331933] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
[47050.347770] usbcore: registered new interface driver uvcvideo
[47050.347773] USB Video Class driver (v0.1.0)
[47081.800695] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
[55560.855608] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[55565.262422] PM: resume of drv:uvcvideo dev:2-3:1.0 complete after 107.316 msecs
[55565.262429] PM: resume of drv:uvcvideo dev:2-3:1.1 complete after 107.303 msecs
[55566.611614] video LNXVIDEO:01: Restoring backlight state
[55570.075727] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[57193.946879] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
me@me-laptop:~$

---

