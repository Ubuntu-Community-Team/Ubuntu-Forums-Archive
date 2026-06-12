---
title: "how do I stop a Logitech Dual Action Gamepad from being used like a mouse?"
date: 2010-05-24
forum: Hardware
---

### Post by gotsanity on 2010-05-24
Just like the title says: My gamepad (Logitech Dual Action) is working however it is acting as a mouse pointer on my system.

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 012: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 003 Device 009: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 008: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 007: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:3831 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

xorg.conf
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection
gotsanity@renraku:~/Downloads/src$ cat /etc/X11/xorg.conf 
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

and lsmod
```
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2151  4 
xt_state                1490  7 
rfcomm                 38965  0 
ip6table_filter         2887  1 
ip6_tables             19618  1 ip6table_filter
sco                     9302  0 
bridge                 53152  0 
stp                     2171  1 bridge
snd_hda_codec_atihdmi     3023  1 
bnep                   11591  0 
l2cap                  35030  4 rfcomm,bnep
nf_nat_irc              1577  0 
snd_hda_codec_idt      61418  1 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_hda_intel          25645  4 
arc4                    1473  2 
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
nf_nat                 19501  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12980  9 nf_nat
snd_seq_oss            31219  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_hwdep               6924  1 snd_hda_codec
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_pcm_oss            41394  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_mixer_oss          16299  1 snd_pcm_oss
ath9k                  76155  0 
nf_conntrack           73934  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
uinput                  8456  0 
iptable_filter          2791  1 
ath9k_common            3071  1 ath9k
snd_pcm                87850  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fglrx                2353422  29 
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62403  0 
shpchp                 33679  0 
videodev               40486  1 uvcvideo
snd                    70978  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
ip_tables              18390  1 iptable_filter
mac80211              243373  2 ath9k,ath9k_common
ath9k_hw              239668  2 ath9k,ath9k_common
ath                    10345  2 ath9k,ath9k_hw
psmouse                64608  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
btusb                  12969  0 
k8temp                  3912  0 
v4l1_compat            15495  2 uvcvideo,videodev
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    12020  1 videodev
i2c_piix4               9639  0 
joydev                 11072  1 
serio_raw               4918  0 
cfg80211              152987  4 ath9k,ath9k_common,mac80211,ath
hp_accel               12168  0 
x_tables               22429  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
bluetooth              58623  5 rfcomm,sco,bnep,l2cap,btusb
lis3lv02d               7583  1 hp_accel
input_polldev           3106  1 lis3lv02d
lp                      9336  0 
parport                37160  2 ppdev,lp
led_class               3732  2 ath9k,hp_accel
usbhid                 40988  0 
hid                    83376  1 usbhid
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvesafb                24962  1 
video                  20623  0 
output                  2503  1 video
ahci                   37646  2 
r8169                  39554  0 
mii                     5237  1 r8169

```

---

### Post by gotsanity on 2010-05-24
solved my own problem

just perform the following:
```
sudo apt-get remove xserver-xorg-input-joystick
```

then reboot!

---

