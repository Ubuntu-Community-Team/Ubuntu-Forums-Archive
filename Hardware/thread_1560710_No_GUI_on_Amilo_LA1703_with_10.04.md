---
title: "No GUI on Amilo LA1703 with 10.04"
date: 2010-08-25
forum: Hardware
---

### Post by gillbert on 2010-08-25
I have just installed Ubuntu 10.04 on a Fujitsu Siemens Amilo LA1703. I had to install it from the Alternate CD, since the Live one just shows me a screen with five blinking dots and then just a black screen.
After the installation Ubuntu didn't start, but after restart I got the screen with five dots and was then thrown into the terminal, but only text based.
```
startx
```
gives me the black screen again.
I've now - after some drama - got internet working on it, and have updated and upgraded, but nothing has helped. I have also copied some VIA drivers and tried modifying xorg.conf without result.
```
lshw -C video
```
still gives me
```
*-display UNCLAIMED
     description: VGA compatible controller
     product: K8M890CE/K8N890CE [Crome 9]
     vendor: VIA Technologies, Inc.
     ...
```

Does anyone have any bright ideas on what I could try or is this a dead end?

---

### Post by clrg on 2010-08-25
I guess you need to install the proper drivers. Try

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-openchrome && init 6
```

---

### Post by gillbert on 2010-08-25
Thank you, but unfortunately it didn't help. The drivers were already installed (already tried it yesterday, but I think I read somewhere that they are already included in Ubuntu 10.04).
Any other suggestions?

---

### Post by clrg on 2010-08-25
Are they loaded? Does lsmod show them?

---

### Post by gillbert on 2010-08-25
not really sure what I am looking for, but this is the output:
```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_via      27111  1 
snd_hda_intel          21941  0 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
soundcore               6620  1 snd
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
amd64_agp               7025  1 
k8temp                  3024  0 
shpchp                 28820  0 
agpgart                31724  1 amd64_agp
psmouse                63245  0 
serio_raw               3978  0 
i2c_viapro              5573  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_via                7272  0 
sata_via                6945  3 
via_rhine              19154  0 
mii                     4381  1 via_rhine

```

---

### Post by clrg on 2010-08-25
Getting the latest drivers from [http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp) could resolve the issue. I hear the ones in the repository are not current.

---

### Post by gillbert on 2010-08-25
I tried it (did it yesterday as well):
```
/lib/vinstall$ sudo cp /media/ext/... /lib/vinstall/via/
/lib/vinstall/via$ cd via
[s]/lib/vinstall/via$ sudo chmod vinstall[/s]
/lib/vinstall/via$ sudo chmod +x vinstall
/lib/vinstall/via$ sudo ./vinstall
```
worked fine, restarted, but no change.
lsmod gives now:
```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
joydev                  8708  0 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_via      27111  1 
snd_hda_intel          21941  0 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
soundcore               6620  1 snd
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
amd64_agp               7025  1 
psmouse                63245  0 
serio_raw               3978  0 
i2c_viapro              5573  0 
k8temp                  3024  0 
shpchp                 28820  0 
agpgart                31724  1 amd64_agp
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_via                7272  0 
sata_via                6945  3 
via_rhine              19154  0 
mii                     4381  1 via_rhine

```

---

### Post by clrg on 2010-08-25
"sudo chmod vinstall" would result in an error.

---

### Post by gillbert on 2010-08-25
sorry forgot to write the "+x", but used it

---

### Post by gillbert on 2010-08-26
I've now tried different things for another day, but have run out of ideas, has anybody encountered something similar or are there any good idea out here.

Have tried the following distributions but all with the same result:
8.04.4 alternate i386
9.10 alternate i386
10.04 desktop i386
10.04.1 alternate amd64
10.04.1 desktop amd64
10.04.1 alternate i386
10.04.1 desktop i386

Would really appreciate some help.

---

### Post by gillbert on 2010-08-28
Well, I solved the problem:
I loaded a AntiX M8.5 686 live CD (which worked fine) and copied the xorg.conf to the installed ubuntu (9.10) and now everything works like a clock (resolution and everything!)

This is the new xorg.conf file:
```

Section "ServerFlags"
	Option "DontZap" "Off"
        Option "AllowMouseOpenFail" "true"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0" 
EndSection

Section "InputDevice"
  Identifier "Touchpad"
  Driver "synaptics"
  Option "Device" "/dev/psaux"
  Option "Protocol" "auto-dev"
  Option "LeftEdge" "1700"
  Option "RightEdge" "5300"
  Option "TopEdge" "1700"
  Option "BottomEdge" "4200"
  Option "FingerLow" "25"
  Option "FingerHigh" "30"
  Option "MaxTapTime" "180"
  Option "MaxTapMove" "220"
  Option "VertScrollDelta" "100"
  Option "HorizScrollDelta" "0"
  Option "MinSpeed" "0.09"
  Option "MaxSpeed" "0.18"
  Option "AccelFactor" "0.0015"
  Option "SHMConfig" "on"
EndSection

Section "InputDevice"
  Driver "synaptics"
  Identifier "ALPS Touchpad"
  Option "Device" "/dev/input/mouse0"
  Option "Protocol" "event"
  Option "LeftEdge" "130"
  Option "RightEdge" "840"
  Option "TopEdge" "130"
  Option "BottomEdge" "640"
  Option "FingerLow" "7"
  Option "FingerHigh" "8"
  Option "MaxTapTime" "180"
  Option "MaxTapMove" "110"
  Option "EmulateMidButtonTime" "75"
  Option "VertScrollDelta" "20"
  Option "HorizScrollDelta" "0"
  Option "MinSpeed" "0.25"
  Option "MaxSpeed" "0.50"
  Option "AccelFactor" "0.030"
  Option "EdgeMotionMinSpeed" "200"
  Option "EdgeMotionMaxSpeed" "200"
  Option "UpDownScrolling" "1"
  Option "CircularScrolling" "1"
  Option "CircScrollDelta" "0.1"
  Option "CircScrollTrigger" "2"
  Option "SHMConfig" "on"
EndSection

Section "InputDevice"
  Identifier "Appletouch"
  Driver "synaptics"
  Option "Device" "/dev/psaux"
  Option "Protocol" "auto-dev"
  Option "LeftEdge" "100"
  Option "RightEdge" "1120"
  Option "TopEdge" "50"
  Option "BottomEdge" "310"
  Option "FingerLow" "25"
  Option "FingerHigh" "30"
  Option "MaxTapMove" "220"
  Option "TapButton1" "1"
  Option "TapButton2" "3"
  Option "TapButton3" "2"
  Option "MinSpeed" "0.79"
  Option "MaxSpeed" "0.88"
  Option "AccelFactor" "0.0015"
  Option "SHMConfig" "on"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
  Option "DPMS" "true"
  HorizSync    30-75
  VertRefresh  55-70 
EndSection

Section "Device"
  Identifier  "Card0"
  Driver "vesa"
  BoardName "unknown"

  Screen 0
 #Option "UseDisplayDevice" "dfp"
 #Option "MonitorLayout" "crt,crt"
 #BusID  "PCI:1:0:0"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
  Option "UseInternalAGPGART" "no"

  Option "XAANoOffscreenPixmaps" "true"

# savage special options, use with care
 #Option "NoUseBios"
 #Option "BusType" "PCI"
  Option "DmaMode" "None"

# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "true"
  Option "UseEDID" "true"
  Option "AddARGBGLXVisuals" "true"
  Option "RenderAccel" "true"
 #Option "AllowGLXWithComposite" "true"
EndSection

Section "Device"
  Identifier  "Card1"
  Driver "vesa"
  BoardName "unknown"

  Screen 1
 #Option "MonitorLayout" "crt,crt"
 #BusID  "PCI:1:0:0"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 8
  Modes "1280x800" "1280x768" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1280x800" "1280x768" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1280x800" "1280x768" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1280x800" "1280x768" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1280x800" "1280x768" "1024x768" "800x600"
  EndSubSection
  
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "false"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-75"
  Option "SecondMonitorVertRefresh" "55-70"
 #Option "MetaModes" "1024x768, 1024x768"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection

```

---

### Post by dE_logics on 2010-08-28
Why not just try another distro, my sincere advice -- Sabayon.

---

### Post by funky_uncle on 2012-01-11
I know it's marked [SOLVED] but it's not solved for me. I have the same laptop.

Booting Antix live CD doesn't help, I guess the xorg.conf is different since the time gillbert tried it. I have installed Ubuntu (I think) from an alternate install CD. No GUI.

So I've started up with a SystemRescue CD (no GUI there either!) now and I copied the contents of gillbert's xorg.conf and saved it as xorg.conf on a usb stick. But I can't for the life of me figure out how to mount the hard drive and the usb stick so I can replace the xorg.conf. I find a lot of examples of mount this and mount that but I don't understand how I should use the command on *this* computer (I'm a rookie as you can see). I can run Midnight Commander, if that helps.

---

