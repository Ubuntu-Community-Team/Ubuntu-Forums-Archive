---
title: "hp tx2640er and ubuntu 9.04 x86_64"
date: 2009-05-12
forum: Hardware
---

### Post by ASDu on 2009-05-12
I'm new user of Ubuntu. 
I have such problems:
1) when ubuntu boots it prints errors with ata and missing modules.dep
2) Remote Control not working
3) Buttons not working:
           - Prefs
           - DVD
           - Rotate
           - Quickstart running rhytmbox (i don't know what it have to do)
4) touchscreen is working but there some troubles:
           - can't calibrate stylus (wacomcpl don't see any wacom devices)
           - eraser on stylus not working
           - bottom button on stylus in gimp moving image (i don't know what it have to do)
           - if i rotate screen with xrandr+xsetwacom like [there]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm") it prints me an error with my missing TabletPCStylus device (i think this because i can't set his xorg.conf which makes my laptop hung on booting)
5) cardreader not working
5) when system starts i used to reinput minijacks of my garniture else my sound plays through laptop's speakers
6) when i close laptop it will be good if it goes to hibernate or shut down at least

p.s. sorry for my english

```
asdu@asdu-note:~$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
``````

asdu@asdu-note:~$ sudo lsusb
Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Favux on 2009-05-12
Hi ASDu,

Welcome to Ubuntu!

Did you install the ATI proprietary driver in System>Administration>Hardware Drivers?

There will be a lot of information here.  Just read through things carefully and take it slow.  Be patient.  You will get most things working.

For general information search the Forum with "tx2*".  A useful thread is here:  [http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2*)

Jaunty no longer uses xorg.conf for Wacom.  It uses the HAL/.fdi method.  We have just figured out how to get Wacom working go here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Read Jaunty Users near the top and go to gali98's HOW TO on page 11.

Also on the first HOW TO is a link to the Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  It also has information on getting two of the four bezel buttons working.

Ask questions if you get stuck.  Good luck!

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

Welcome to Ubuntu!

Did you install the ATI proprietary driver in System>Administration>Hardware Drivers?

There will be a lot of information here.  Just read through things carefully and take it slow.  Be patient.  You will get most things working.

For general information search the Forum with "tx2*".  A useful thread is here:  [http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2*)

Jaunty no longer uses xorg.conf for Wacom.  It uses the HAL/.fdi method.  We have just figured out how to get Wacom working go here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Read Jaunty Users near the top and go to gali98's HOW TO on page 11.

Also on the first HOW TO is a link to the Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  It also has information on getting two of the four bezel buttons working.

Ask questions if you get stuck.  Good luck!
Thank you for you advices.

I installed latest proprietary driver from ati site...

I tried gali98's HOW TO but i can't find how to:
1) still not working eraser
2) still don't know how to configure my touch, eraser and stylus by fdi file (what mean bottomX bottomY and other)
3) when i used command wacomcpl i see only "touch" and i don't know how to calibrate it. When i tried to save "screen mapping" it gave me an error:
```
X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set touch value for 'Screen_No'
X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set touch value for 'Screen_No'
    while executing
"exec xsetwacom set $device $option $value"
    (procedure "updateXinitrc" line 24)
    invoked from within
"updateXinitrc $device Screen_No $sn"
    (procedure "updateSet" line 17)
    invoked from within
"updateSet"
    invoked from within
".allothers.f.ok invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 
[list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .allothers.f.ok"
    (command bound to event)
```4) when i tried to rotate stylus nothing happened. Stylus not rotated and no error output...

---

### Post by Favux on 2009-05-12
Hi ASDu,

Check in System>Administration>Synaptic Package Manager that you have the 0.8.2-2 linuxwacom packages installed.  They are xserver-xorg-input-wacom and wacom-tools.  Search "wacom".  You only copied (cp) the 0.8.3-3 wacom.ko.  Correct?

You can use the simpler .fdi above the one with the coordinates.  Once "wacomcpl" works in a terminal you can configure everything with it.  Just be sure to follow the instructions to install the .xinitrc once wacomcpl works for you.

Rotation won't work until:
```
xsetwacom list
```
returns stylus, eraser, and touch.  Then you will know the .fdi is installed correctly.

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

Check in System>Administration>Synaptic Package Manager that you have the 0.8.2-2 linuxwacom packages installed.  They are xserver-xorg-input-wacom and wacom-tools.  Search "wacom".  You only copied (cp) the 0.8.3-3 wacom.ko.  Correct?

You can use the simpler .fdi above the one with the coordinates.  Once "wacomcpl" works in a terminal you can configure everything with it.  Just be sure to follow the instructions to install the .xinitrc once wacomcpl works for you.

Rotation won't work until:
```
xsetwacom list
```returns stylus, eraser, and touch.  Then you will know the .fdi is installed correctly.

At Synaptic Package Manager i have both xserver-xorg-input-wacom and wacom-tools installed
I take his fdi file, but still don't work...
```
asdu@asdu-note:~$ xsetwacom list
SynPS/2 Synaptics TouchPad touch
```

---

### Post by Favux on 2009-05-12
Hi ASDu,

Good.

Go into (change directory into) the source code and repeat step 6) copying the 0.8.3-3 wacom.ko into place.  Reboot.  Did you reboot before?  Then use the default .fdi file right under the section 2 title.  You can skip section 3.  You can do everything there (in section 3) with wacomcpl in section 4.  For now you can also skip cyberfish's daemon (monitor_wacom.c).  Do that later when things are working.

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

Good.

Go into (change directory into) the source code and repeat step 6) copying the 0.8.3-3 wacom.ko into place.  Reboot.  Did you reboot before?  Then use the default .fdi file right under the section 2 title.  You can skip section 3.  You can do everything there (in section 3) with wacomcpl in section 4.  For now you can also skip cyberfish's daemon (monitor_wacom.c).  Do that later when things are working.

i made all this steps before...

now i:
1) i made this for 0.8.3-2 wacom.ko, 0.8.3-3 won't work for me.
2) reboot
3) copied his default .fdi file.
still not working
then what?

---

### Post by Favux on 2009-05-12
Hi ASDu,

You have a TX2500, correct?  Not a TX2z or TX2 also called smart touch or multi-touch?  Because that has a N-trig digitizer, not a Wacom digitizer.

Let us see what these commands show.
```
xsetwacom list
```
```
xinput --list
```

```
dmesg | grep [Ww]acom
```
```
lsmod
```
```
modinfo -d wacom
```

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

You have a TX2500, correct?  Not a TX2z or TX2 also called smart touch or multi-touch?  Because that has a N-trig digitizer, not a Wacom digitizer.

Let us see what these commands show.
<...>

Hello, Favux
tx2640er... on screen i see tx2000, on sticker i see tx2500 series
So... many letters above :)

```
asdu@asdu-note:~$ xsetwacom list
SynPS/2 Synaptics TouchPad touch 
``````
asdu@asdu-note:~$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"stylus"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 26202
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 16325
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"eraser"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 26202
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 16325
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Macintosh mouse button emulation"    id=6    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=7    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"touch"    id=8    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 4095
        Resolution is 397
    Axis 1 :
        Min_value is 0
        Max_value is 8010
        Resolution is 633
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Microsoft Bluetooth Notebook Mouse 5000"    id=9    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
``````
asdu@asdu-note:~$ dmesg | grep [Ww]acom
[   14.967438] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input8
[   14.994035] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9
[   15.020955] usbcore: registered new interface driver wacom
[   15.021074] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver

``````
asdu@asdu-note:~$ lsmod
Module                  Size  Used by
hidp                   25600  1 
michael_mic            10880  4 
arc4                   10240  4 
ecb                    11392  4 
binfmt_misc            18572  1 
fglrx                2376872  31 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  6 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               69512  0 
snd                    78792  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
ieee80211_crypt_tkip    17920  0 
compat_ioctl32         18304  1 uvcvideo
joydev                 20864  0 
psmouse                64028  0 
wl                   1496016  0 
cdc_wdm                19968  0 
cdc_acm                26784  0 
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
wacom                  32904  0 
pcspkr                 11136  0 
serio_raw              14468  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
cdc_ether              14336  0 
i2c_piix4              20112  0 
usbnet                 27016  1 cdc_ether
shpchp                 44572  0 
video                  29204  0 
btusb                  21784  3 
output                 11648  1 video
usbhid                 47040  0 
r8169                  46596  0 
mii                    14464  2 usbnet,r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
``````
asdu@asdu-note:~$ modinfo -d wacom
USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver

```

---

### Post by Favux on 2009-05-12
Hi ASDu,

Everything looks correct except xsetwacom list.  Since xinput is returning the correct names it should be working.  That should mean linuxwacom is working and the .fdi file is working.

The kernel module wacom is present.  Xinput is returning stylus, eraser, and touch.  The .fdi is parsing the HAL names correctly.  So wacomcpl should work and so should xsetwacom (and rotation).

So you are very, very close to getting it to work.

Did you put anything in your xorg.conf in /etc/X11/ ?  If so post your xorg.conf.

Another possibility is your wacom tools is corrupted.  You have to have the same version of the linuxwacom drivers and wacom tools (the two packages) otherwise things do not work right.  You could, in Synaptics Package Manager,  reinstall both linuxwacom packages.  You may have to recopy the 0.8.3-2 or 0.8.3-3 wacom.ko back after doing the reinstallation.

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

Everything looks correct except xsetwacom list.  Since xinput is returning the correct names it should be working.  That should mean linuxwacom is working and the .fdi file is working.

The kernel module wacom is present.  Xinput is returning stylus, eraser, and touch.  The .fdi is parsing the HAL names correctly.  So wacomcpl should work and so should xsetwacom (and rotation).

So you are very, very close to getting it to work.

Did you put anything in your xorg.conf in /etc/X11/ ?  If so post your xorg.conf.

Another possibility is your wacom tools is corrupted.  You have to have the same version of the linuxwacom drivers and wacom tools (the two packages) otherwise things do not work right.  You could, in Synaptics Package Manager,  reinstall both linuxwacom packages.  You may have to recopy the 0.8.3-2 or 0.8.3-3 wacom.ko back after doing the reinstallation.

Hi Favux,
```

*_xorg.conf:_*
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

I reinstalled both xserver-xorg-input-wacom and wacom-tools in Synaptic Package Manager. Then copied 0.8.3-2 wacom.ko module again.

what to do next?

[SIZE=1][COLOR=Silver]*Thank you for so rapid helping. I hope i'm not too bored you :)*[/COLOR][/SIZE]

---

### Post by Favux on 2009-05-12
Hi ASDu,

I do not know where this is coming from:
```
SynPS/2 Synaptics TouchPad touch
```
I was hoping it was from the xorg.conf.  It is as if the Synaptics Touchpad .fdi is interfering.  This used to happen in the xorg.conf in Hardy.  We had to rename Synaptics TouchPad to Synaptics Pad so xinput did not confuse touch with TouchPad.  But I have not seen this since.

Everything seems to be working except xsetwacom (and so wacomcpl and rotation).  Hmmm.  I can not think of anything sensible to try right now.  You could try martinjochimsen's fix in post #3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  But your kernel driver not "sticking" doesn't seem to be the problem.

Maybe it is something simple but I do not see it right now.  Maybe take a break and think about it?  You could reread the HOW TO and see if you can come up with something.

---

### Post by ASDu on 2009-05-12
> **Favux said:**
> Hi ASDu,

I do not know where this is coming from:
```
SynPS/2 Synaptics TouchPad touch
```I was hoping it was from the xorg.conf.  It is as if the Synaptics Touchpad .fdi is interfering.  This used to happen in the xorg.conf in Hardy.  We had to rename Synaptics TouchPad to Synaptics Pad so xinput did not confuse touch with TouchPad.  But I have not seen this since.

Everything seems to be working except xsetwacom (and so wacomcpl and rotation).  Hmmm.  I can not think of anything sensible to try right now.  You could try martinjochimsen's fix in post #3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  But your kernel driver not "sticking" doesn't seem to be the problem.

Maybe it is something simple but I do not see it right now.  Maybe take a break and think about it?  You could reread the HOW TO and see if you can come up with something.

Hello Favux,
Thank you for helping, i'll try to watch your links, google and other topics here. I also will be waiting for your response.

---

### Post by Favux on 2009-05-13
Hi ASDu,

Gali98 was nice enough to look at your thread for us.  He thinks your problem is similar or the same as heteroerectus' problem.  He recommends you try what he recommended to heteroerectus:  [http://ubuntuforums.org/showpost.php?p=7256695&postcount=270](http://ubuntuforums.org/showpost.php?p=7256695&postcount=270)

If that fails I wonder if we should look at your "/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi" and "/usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi".  Maybe something is garbled in them.

---

### Post by ASDu on 2009-05-13
> **Favux said:**
> Hi ASDu,

Gali98 was nice enough to look at your thread for us.  He thinks your problem is similar or the same as heteroerectus' problem.  He recommends you try what he recommended to heteroerectus:  [http://ubuntuforums.org/showpost.php?p=7256695&postcount=270](http://ubuntuforums.org/showpost.php?p=7256695&postcount=270)

If that fails I wonder if we should look at your "/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi" and "/usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi".  Maybe something is garbled in them.
seems to be OK.

```
asdu@asdu-note:~$ xsetwacom list
stylus           stylus    
eraser           eraser    
touch            touch
```Now i'm trying your manual of rotation but a find another problem:
> To further integrate screen rotation into your TX2000 you can do a key binding to the “Q” key (the blue led icon on the lower right hand edge of the screen below the blue led “DVD” icon). Unfortunately ***HAL breaks key binding for single-key key bindings***.  So you'll need to go to xorg.conf in the /etc/X11 directory.  Open a terminal and enter:
     Code:
         sudo gedit /etc/X11/xorg.conf 
You'll notice that the keyboard section has been commented out with “#”s by Intrepid during install due to the switch to HALbut i haven't any keyboard section in my xorg.conf...

Quickplay(which opens rhytmbox) on xev:
```
KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 30, synthetic NO, window 0x6800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x6800001,
    mode NotifyUngrab, detail NotifyAncestor
```Other 3 buttons give no response...

Also:
1) i can't find how to make my eraser erasing and don't know what bottom button have to do=)
2) I can't understand how to set up my Remote Control...
3) hibernate crushing ubuntu

---

### Post by Favux on 2009-05-14
Hi ASDu,

Great!  You got it working!  Nice job.  Did you do it by following gali98's suggestion?

To get eraser working follow post #8 on the Rotation thread.  In Xournal the stylus button is the eraser.

Have you installed CellWriter?

To get the stylus button type "wacomcpl" in a terminal and click on stylus and then click on tool buttons and then make button 2 right.  Also see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Read the paragraph above the Keycode Addendum.  Follow the keycode addendum to get 2 of the 4 buttons working.

Then bind the rotation script to the Q (quick launch) button.  Assume Jaunty fixed the problem with HAL and the keyboard.

---

### Post by ASDu on 2009-05-14
> **Favux said:**
> Hi ASDu,

Great!  You got it working!  Nice job.  Did you do it by following gali98's suggestion?

To get eraser working follow post #8 on the Rotation thread.  In Xournal the stylus button is the eraser.

Have you installed CellWriter?

To get the stylus button type "wacomcpl" in a terminal and click on stylus and then click on tool buttons and then make button 2 right.  Also see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Read the paragraph above the Keycode Addendum.  Follow the keycode addendum to get 2 of the 4 buttons working.

Then bind the rotation script to the Q (quick launch) button.  Assume Jaunty fixed the problem with HAL and the keyboard.
Thank you for great help.
Yes, his suggestion makes my stylus working. I found how to set up wacom with your links.

made Key Code Addendum
in xev i see that Quicklaunch is XF86AudioMedia(pushed it with alt, else it prints nothing interesting and losing focus), made your rotating script working for this button... 
Other 3 buttons have no response in xev... and i don't know how to setup them...

---

### Post by Favux on 2009-05-14
Hi ASDu,

You're welcome.  I'm happy you are getting your tablet set up.

The signal for the rotation and brightness key may be in the HP-WMI kernel module.  See near the bottom of Rotation where I talk about the swivel hinge.  We haven't figured out how to get them to work.

I bet the Q key is present somewhere.  When the Xserver changed from 1.4 in Hardy to 1.5 in Intrepid we lost the 2 working buttons because the key mapping changed.  That's why we came up with:
```
	sudo update-rc.d -f hotkey-setup remove
	sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
```
The same thing has probably happened in the change to Xsever 1.6 in Jaunty.  I talk to Irfy about finding buttons on this thread:  [http://ubuntuforums.org/showthread.php?t=1103674](http://ubuntuforums.org/showthread.php?t=1103674)  Irfy links to the new wiki he made on post #8.  If you find the answer let me know.  If I get a chance I'll ask gali98 if he knows.

---

### Post by ASDu on 2009-05-14
> **Favux said:**
> Hi ASDu,

You're welcome.  I'm happy you are getting your tablet set up.

The signal for the rotation and brightness key may be in the HP-WMI kernel module.  See near the bottom of Rotation where I talk about the swivel hinge.  We haven't figured out how to get them to work.

I bet the Q key is present somewhere.  When the Xserver changed from 1.4 in Hardy to 1.5 in Intrepid we lost the 2 working buttons because the key mapping changed.  That's why we came up with:
```
    sudo update-rc.d -f hotkey-setup remove
    sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
```The same thing has probably happened in the change to Xsever 1.6 in Jaunty.  I talk to Irfy about finding buttons on this thread:  [http://ubuntuforums.org/showthread.php?t=1103674](http://ubuntuforums.org/showthread.php?t=1103674)  Irfy links to the new wiki he made on post #8.  If you find the answer let me know.  If I get a chance I'll ask gali98 if he knows.
in his wiki:
 > Run acpi_listen in a terminal and press that key again. If there is no output, that is not an ACPI key and this guide cannot help you. 
but no key return output...

---

### Post by Favux on 2009-05-14
Hi ASDu,

You'll have to make a launcher.  If you put it in the title bar or a dock you only have to single click it.  I actually have both.  I use them at least as often as I do my Q button.  Cairo Dock 2 came out 2 days ago and it is nice eye candy.

---

### Post by ASDu on 2009-05-14
> **Favux said:**
> Hi ASDu,

You'll have to make a launcher.  If you put it in the title bar or a dock you only have to single click it.  I actually have both.  I use them at least as often as I do my Q button.  Cairo Dock 2 came out 2 days ago and it is nice eye candy.
Hello Favux,
make launcher for... what?
I've already made rotating by Quicklaunch button...

p.s. docks... maybe... but not now :) Before that i want my laptop fully working

---

### Post by ASDu on 2009-05-14
Hello from Mr.Trouble
I catch another problem... 

I installed savage2 but it won't start... on savage forum i found that it's probably because opengl driver is mesa not ati... after i find answer that anvyng will help me. I installed it and then installed ati driver... then... after reboot my ubuntu won't start Xsession and hung with artefacts on the screen...
envyng --uninstall-all not helped me... so i tried to wipe xorg.conf... still not working

i don't know how to solve my trouble... I hope you'll help me...

---

### Post by Favux on 2009-05-14
Hi ASDu,

Ouch!  Just when we got the tablet working.

I'd uninstall Savage2 and the reinstall the ATI driver.

Try this link:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)  And post on the Multimedia and Video forum.  Somebody on Mutimedia probably knows what to do.

---

### Post by ASDu on 2009-05-17
> **Favux said:**
> Hi ASDu,

Ouch!  Just when we got the tablet working.

I'd uninstall Savage2 and the reinstall the ATI driver.

Try this link:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)  And post on the Multimedia and Video forum.  Somebody on Mutimedia probably knows what to do.
Hello again Favux,
I don't find better way than reinstall my ubuntu from zero...

So i made my stylus working, but another problem...
when i'm rotating screen at not "normal" angles my screen freezes and nothing except mouse work...

---

### Post by Favux on 2009-05-17
Hi ASDu,

Sorry to hear you had to reinstall.  It sounds like the ATI drivers still have a problem with Compiz.  See:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830) near the top for a little information.  So you may not be able to use Compiz until ATI's driver supports it better.  Or Compiz supports ATI?

Another way to go might be.  On post #108 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11) fr34k4d3113 came up with a script to turn Compiz off when he rotated.  I think he had Intel video.

---

### Post by ASDu on 2009-05-18
> **Favux said:**
> Hi ASDu,

Sorry to hear you had to reinstall.  It sounds like the ATI drivers still have a problem with Compiz.  See:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830) near the top for a little information.  So you may not be able to use Compiz until ATI's driver supports it better.  Or Compiz supports ATI?

Another way to go might be.  On post #108 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11) fr34k4d3113 came up with a script to turn Compiz off when he rotated.  I think he had Intel video.
Hello Favux, 
I turned off all effects and my rotation now works fine.
So now i can't get my remote control wortking... do you have any ideas or links on how-to make it working?

---

### Post by Favux on 2009-05-18
Hi ASDu,

Good!  It isn't a tablet pc unless you can rotate it into a tablet.

I know I've seen threads on the remote.  I never use it so I haven't set it up yet.  Maybe on the big TX2500 thread I gave you a link to earlier?  You can search in the thread for "remote", etc..

---

### Post by ASDu on 2009-05-18
> **Favux said:**
> Hi ASDu,

Good!  It isn't a tablet pc unless you can rotate it into a tablet.

I know I've seen threads on the remote.  I never use it so I haven't set it up yet.  Maybe on the big TX2500 thread I gave you a link to earlier?  You can search in the thread for "remote", etc..
Hello Favux,
i found another issue... When my laptop is on flatbed mode (when screen on keyboard) Q-button not working at all... Don't you know how to solve this?

---

### Post by Favux on 2009-05-18
Hi ASDu,

That happened to someone else months ago.  I can't remember if we found a fix or decided if it was a hardware issue.  I'll try to remember what we did or where it was.

---

### Post by Favux on 2009-05-18
Hi ASDu,

Found it, it starts with post #53 here:  [http://ubuntuforums.org/showthread.php?p=6722495&highlight=button#post6722495](http://ubuntuforums.org/showthread.php?p=6722495&highlight=button#post6722495)  Basically all GrooveTherapy had to do was update his BIOS.  Hope it works for you too.

---

### Post by ASDu on 2009-05-18
> **Favux said:**
> Hi ASDu,

Found it, it starts with post #53 here:  [http://ubuntuforums.org/showthread.php?p=6722495&highlight=button#post6722495](http://ubuntuforums.org/showthread.php?p=6722495&highlight=button#post6722495)  Basically all GrooveTherapy had to do was update his BIOS.  Hope it works for you too.
Updating bios not helped me... I think that because he have tx2000 and i have tx2500...

So at this time i have:
1) when my laptop in tablet mode Quicklaunch button not working
2) when my system boots it plays sound through laptop speakers, i have to replug already plugged headphones to make sound playing through headphones... Also when i turn sound off - on...
3) DVD, prefs and rotate buttons on display have no response
4) Remote Control not working at all(i don't find any useful info about this issue)
5) After hibernate my system won't wake up and hungs. So i have to deny hibernation...
hmm, that's all at the moment...

---

### Post by Favux on 2009-05-18
Hi ASDu,

For the remote try post #10 by janmyszkier here:  [http://ubuntuforums.org/showthread.php?t=897241&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=897241&highlight=tx2*)

---

### Post by ASDu on 2009-05-18
> **Favux said:**
> Hi ASDu,

For the remote try post #10 by janmyszkier here:  [http://ubuntuforums.org/showthread.php?t=897241&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=897241&highlight=tx2*)
Hi Favux,
It's amazing... One thing i only had to do was only installing lirc and choose **“Windows Media Center Remotes ( new version Philips et al. )”**...

so i have fully working remote control

---

### Post by Favux on 2009-05-18
See, there you go! ;)

Regarding hibernation.  Is your tablet waking up from suspend (suspend to RAM) OK?  Just not from hibernate (suspend to disk)?

If so how much RAM do you have?  And how big is your swap file?

---

### Post by ASDu on 2009-05-18
> **Favux said:**
> See, there you go! ;)

Regarding hibernation.  Is your tablet waking up from suspend (suspend to RAM) OK?  Just not from hibernate (suspend to disk)?

If so how much RAM do you have?  And how big is your swap file?
My keyboard won't work after that...

i have 2Gb RAM and 3,6Gb swap

---

### Post by Favux on 2009-05-18
Hi ASDu,

OK, you are at 1.5 x RAM.  Increasing to that has helped some folks.  Since you already have that if you can't find solutions searching the forum you could try:  [http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

Edit:  Ah hah!  No keyboard?  I knew I had read about that recently.  See from post #555 forward here:  [http://ubuntuforums.org/showthread.php?p=7182098&highlight=suspend+keyboard#post7182098](http://ubuntuforums.org/showthread.php?p=7182098&highlight=suspend+keyboard#post7182098)

---

### Post by ASDu on 2009-05-19
> **Favux said:**
> Hi ASDu,

OK, you are at 1.5 x RAM.  Increasing to that has helped some folks.  Since you already have that if you can't find solutions searching the forum you could try:  [http://people.freedesktop.org/~hughsient/quirk/index.html]("http://people.freedesktop.org/%7Ehughsient/quirk/index.html")

Edit:  Ah hah!  No keyboard?  I knew I had read about that recently.  See from post #555 forward here:  [http://ubuntuforums.org/showthread.php?p=7182098&highlight=suspend+keyboard#post7182098](http://ubuntuforums.org/showthread.php?p=7182098&highlight=suspend+keyboard#post7182098)
hibernate:
```
asdu@asdu-note:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ ./quirk-checker.sh 
-e Checking your system...

CRITICAL ERROR: Using ATI binary driver. This is not supported!
```

suspend:
i followed instruction. But after wake up my keyboard switch indicator won't work as it used to (don't show usa switch(blank) and switches with alt+shift, but in prefs i have ctrl+shift)

---

### Post by Favux on 2009-05-19
Hmmm.  Did you try installing the guidance power-manager?  That seemed to work for some of them.

---

### Post by ASDu on 2009-05-19
> **Favux said:**
> Hmmm.  Did you try installing the guidance power-manager?  That seemed to work for some of them.
guidance power manager... i don't get it...  i have power manager... what i have to do?

---

### Post by Favux on 2009-05-19
Hi ASDu,

It's in Synaptics Package Manager.  Install it and if it doesn't work uninstall it and if you need to, reinstall the current power manager.

---

### Post by ASDu on 2009-05-19
> **Favux said:**
> Hi ASDu,

It's in Synaptics Package Manager.  Install it and if it doesn't work uninstall it and if you need to, reinstall the current power manager.
Hi Favux, 
It doesn't work...

---

### Post by Favux on 2009-05-19
Hi again ASDu,

Well, it was worth a shot.

---

### Post by ASDu on 2009-05-19
> **Favux said:**
> Hi again ASDu,

Well, it was worth a shot.
Hello Favux,
No ideas about sound? It's too uncomfortable when i'm turning sound on i have to replug my headphones

Also another problem... with skype. When i'm listening the music through rhytmbox if someone will call me Skype won't work(i can't pick up a call)...

---

### Post by Favux on 2009-05-20
Hi ASDu,

There's several threads on speakers and headphones.  And I think I've seen some TX2500 users discussing it.  I think they found a fix.  Maybe that was in the big TX2500 thread I gave you?  You can go into a thread and then use the search thread option to the top right.

---

