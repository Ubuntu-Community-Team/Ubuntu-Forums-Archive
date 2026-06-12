---
title: "karmic &amp; AIPTEK 14000u Media Tablet"
date: 2009-11-05
forum: Hardware
---

### Post by lospo on 2009-11-05
Hi and good morning. 

I've got an AIPTEK mediatable that i use to draw in Gimp, and before yesterday it worrks like a charm! 
But when i installed the Karmic Koala upgrade the tablet work no more: now it have strange coordinates (it's no more like the screen) and the pressure of the pen take no effect, so i cannot draw anything.

Anyone has this trouble? Or know how to solve it?

Thanks!

---

### Post by lospo on 2009-11-05
oh! That's the output of xorg (why a keyb???):

(II) config/hal: Adding input device WALTOP International Corp. Media Tablet
(**) WALTOP International Corp. Media Tablet: always reports core events
(**) WALTOP International Corp. Media Tablet: Device: "/dev/input/event4"
(II) WALTOP International Corp. Media Tablet: Found 9 mouse buttons
(II) WALTOP International Corp. Media Tablet: Found x and y relative axes
(II) WALTOP International Corp. Media Tablet: Found scroll wheel(s)
(II) WALTOP International Corp. Media Tablet: Found x and y absolute axes
(II) WALTOP International Corp. Media Tablet: Found absolute touchpad
(II) WALTOP International Corp. Media Tablet: Found keys
(II) WALTOP International Corp. Media Tablet: Configuring as touchpad
(II) WALTOP International Corp. Media Tablet: Configuring as keyboard
(**) WALTOP International Corp. Media Tablet: YAxisMapping: buttons 4 and 5
(**) WALTOP International Corp. Media Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "WALTOP International Corp. Media Tablet" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "it"
(WW) WALTOP International Corp. Media Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Media Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Media Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Media Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Media Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Media Tablet: initialized for absolute axes.

---

### Post by Favux on 2009-11-05
Hi lospo,

You have a Waltop tablet rebranded by Aiptek.  We just got the Waltop tablets working in Karmic yesterday.

For the .fdi we are using see post #8 on this [thread]("http://ubuntuforums.org/showthread.php?t=1261407").

To get it to work you need to compile linuxwacom 0.8.4-3 and also use a modified wcmUSB.c.  The wcmUSB.c has been "patched" to support the Waltop tablets.

See post #92 for the modified wcmUSB.c [here]("http://ubuntuforums.org/showthread.php?t=1261407&page=10").

See posts #95 & 96 for instructions on how to compile 0.8.4-3.

---

### Post by lospo on 2009-11-05
oh my god... i'm not so prepared to do this...
Be patient, but i need a little more help: where i have to place the fdi file?

Should i compile a new module? The tablet works, only the "click" of the pen isn't working... maybe is only a conf problem?

Isn't strange that it works in Jaunty and it doen't work in Karmic? I cannot understand... THANKS!

> **Favux said:**
> Hi lospo,

You have a Waltop tablet rebranded by Aiptek.  We just got the Waltop tablets working in Karmic yesterday.

For the .fdi we are using see post #8 on this [thread]("http://ubuntuforums.org/showthread.php?t=1261407").

To get it to work you need to compile linuxwacom 0.8.4-3 and also use a modified wcmUSB.c.  The wcmUSB.c has been "patched" to support the Waltop tablets.

See post #92 for the modified wcmUSB.c [here]("http://ubuntuforums.org/showthread.php?t=1261407&page=10").

See posts #95 & 96 for instructions on how to compile 0.8.4-3.

---

### Post by Favux on 2009-11-05
Hi lospo,

In Jaunty the Ubuntu dev.s had a Waltop section in the 10-wacom.fdi and must have patched something in the 0.8.2-2 linuxwacom that came default in Jaunty.  We think it was the wcmUSB.c.  For some reason they didn't do that for Karmic.

Compiling the first time seems difficult but it really isn't.  Just read through it a few times and take notes until you have it straight in your head.

-In Karmic the .fdi has been renamed to 10-linuxwacom.fdi. So to back up the "default" Karmic .fdi:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi /home/yourusername/Desktop/10-linuxwacom.bak

```
Where "yourusername" is the user name you are using. Check that the "10-linuxwacom.bak" is now on your Desktop and has the correct contents by right clicking on it and 'Open as a "text file"'. You can move it to wherever you want in Nautilus (Places) later. Close it.
-Now open the current 10-linuxwacom.fdi as root in gedit with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
Delete the entire contents (its safe, you've verified your backup). Now copy and paste the entire contents of the downloaded modified wacom.fdi (you can right click on it and open it in another text editor) save and close.
-Reboot.

---

### Post by lospo on 2009-11-06
No, no way, i'm only at the same point: coordinates are bad (i can use only 50% of my tablet) and i still have no pointing with the pen.

That's my lsmod output:
```

lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
vboxnetadp             93292  0 
vboxnetflt            100300  0 
vboxdrv              1708492  1 vboxnetflt
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
usblp                  15136  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
snd_hda_codec_realtek   277860  1 
mt352                   7812  1 
arc4                    2144  2 
saa7134_alsa           14560  1 
ecb                     3296  2 
saa7134_dvb            26860  0 
videobuf_dvb            8452  1 saa7134_dvb
dvb_core              104528  1 videobuf_dvb
snd_hda_intel          31880  2 
mt20xx                 13480  1 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
tea5767                 7492  0 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
tda9887                11780  1 
snd_pcm                93160  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
tda8290                15748  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
tuner                  24520  2 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
rt61pci                23556  0 
crc_itu_t               2336  1 rt61pci
rt2x00pci               9216  1 rt61pci
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              34624  2 rt61pci,rt2x00pci
saa7134               178356  2 saa7134_alsa,saa7134_dvb
snd_timer              26992  2 snd_pcm,snd_seq
led_class               5256  1 rt2x00lib
ir_common              52740  1 saa7134
input_polldev           4720  1 rt2x00lib
mac80211              210104  2 rt2x00pci,rt2x00lib
v4l2_common            21024  2 tuner,saa7134
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               43360  3 tuner,saa7134,v4l2_common
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
snd                    77096  19 snd_hda_codec_realtek,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              109144  2 rt2x00lib,mac80211
videobuf_dma_sg        14436  3 saa7134_alsa,saa7134_dvb,saa7134
amd64_edac_mod         26688  0 
videobuf_core          21188  3 videobuf_dvb,saa7134,videobuf_dma_sg
soundcore               9088  1 snd
psmouse                57124  0 
iptable_filter          3872  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
tveeprom               14884  1 saa7134
serio_raw               6596  0 
eeprom_93cx6            2528  1 rt61pci
joydev                 13088  0 
i2c_nforce2             8168  0 
ppdev                   8232  0 
btusb                  14260  2 
edac_core              48876  1 amd64_edac_mod
k8temp                  5504  0 
ip_tables              21200  1 iptable_filter
nvidia              10316904  36 
parport_pc             37352  1 
lp                     11908  0 
x_tables               25832  1 ip_tables
parport                40528  3 ppdev,parport_pc,lp
usbhid                 43968  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
lospo@bobogrigio:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
vboxnetadp             93292  0 
vboxnetflt            100300  0 
vboxdrv              1708492  1 vboxnetflt
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
usblp                  15136  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
snd_hda_codec_realtek   277860  1 
mt352                   7812  1 
arc4                    2144  2 
saa7134_alsa           14560  1 
ecb                     3296  2 
saa7134_dvb            26860  0 
videobuf_dvb            8452  1 saa7134_dvb
dvb_core              104528  1 videobuf_dvb
snd_hda_intel          31880  2 
mt20xx                 13480  1 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
tea5767                 7492  0 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
tda9887                11780  1 
snd_pcm                93160  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
tda8290                15748  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
tuner                  24520  2 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
rt61pci                23556  0 
crc_itu_t               2336  1 rt61pci
rt2x00pci               9216  1 rt61pci
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              34624  2 rt61pci,rt2x00pci
saa7134               178356  2 saa7134_alsa,saa7134_dvb
snd_timer              26992  2 snd_pcm,snd_seq
led_class               5256  1 rt2x00lib
ir_common              52740  1 saa7134
input_polldev           4720  1 rt2x00lib
mac80211              210104  2 rt2x00pci,rt2x00lib
v4l2_common            21024  2 tuner,saa7134
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               43360  3 tuner,saa7134,v4l2_common
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
snd                    77096  19 snd_hda_codec_realtek,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              109144  2 rt2x00lib,mac80211
videobuf_dma_sg        14436  3 saa7134_alsa,saa7134_dvb,saa7134
amd64_edac_mod         26688  0 
videobuf_core          21188  3 videobuf_dvb,saa7134,videobuf_dma_sg
soundcore               9088  1 snd
psmouse                57124  0 
iptable_filter          3872  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
tveeprom               14884  1 saa7134
serio_raw               6596  0 
eeprom_93cx6            2528  1 rt61pci
joydev                 13088  0 
i2c_nforce2             8168  0 
ppdev                   8232  0 
btusb                  14260  2 
edac_core              48876  1 amd64_edac_mod
k8temp                  5504  0 
ip_tables              21200  1 iptable_filter
nvidia              10316904  36 
parport_pc             37352  1 
lp                     11908  0 
x_tables               25832  1 ip_tables
parport                40528  3 ppdev,parport_pc,lp
usbhid                 43968  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45

```

and i think that something goes wrong...

---

### Post by Favux on 2009-11-06
Hi lospo,

From what you said I can't tell what you have done.

The lsmod does not show wacom.  The wacom would be the wacom.ko, which is the usb kernel driver/module for linuxwacom.  So the linuxwacom drivers can't be talking to your tablet.  A mouse .fdi and driver or evdev is probably running your tablet.  Entering "xinput --list" in a terminal would probably help tell us.

If you did compile linuxwacom with the modified wcmUSB.c then the wacom.ko module isn't auto-loading.  To fix that add "wacom" (without the quotes) to the end of the file 'modules' in "/etc/".  So:
```
gksudo gedit /etc/modules
```

---

### Post by lospo on 2009-11-06
Ok, i understand: my new lsmod:(after edit modules file and a reboot)
```

Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
vboxnetadp             93292  0 
vboxnetflt            100300  0 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
saa7134_alsa           14560  1 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
vboxdrv              1708492  1 vboxnetflt
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_edac_mod         26688  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
mt352                   7812  1 
arc4                    2144  2 
saa7134_dvb            26860  0 
videobuf_dvb            8452  1 saa7134_dvb
dvb_core              104528  1 videobuf_dvb
ecb                     3296  2 
edac_core              48876  1 amd64_edac_mod
btusb                  14260  2 
mt20xx                 13480  1 
tea5767                 7492  0 
tda9887                11780  1 
tda8290                15748  0 
tuner                  24520  2 
rt61pci                23556  0 
crc_itu_t               2336  1 rt61pci
rt2x00pci               9216  1 rt61pci
rt2x00lib              34624  2 rt61pci,rt2x00pci
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210104  2 rt2x00pci,rt2x00lib
saa7134               178356  2 saa7134_alsa,saa7134_dvb
cfg80211              109144  2 rt2x00lib,mac80211
iptable_filter          3872  0 
wacom                  25608  0 
ir_common              52740  1 saa7134
lp                     11908  0 
usblp                  15136  0 
ppdev                   8232  0 
eeprom_93cx6            2528  1 rt61pci
k8temp                  5504  0 
ip_tables              21200  1 iptable_filter
v4l2_common            21024  2 tuner,saa7134
joydev                 13088  0 
psmouse                57124  0 
parport_pc             37352  1 
serio_raw               6596  0 
i2c_nforce2             8168  0 
videodev               43360  3 tuner,saa7134,v4l2_common
soundcore               9088  1 snd
parport                40528  3 lp,ppdev,parport_pc
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
videobuf_dma_sg        14436  3 saa7134_alsa,saa7134_dvb,saa7134
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
x_tables               25832  1 ip_tables
videobuf_core          21188  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               14884  1 saa7134
nvidia              10316904  46 
usbhid                 43968  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45


```
 
and the xinput --list
```
"Virtual core pointer"	id=0	[XPointer]
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
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImPS/2 Generic Wheel Mouse"	id=2	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
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
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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
"WALTOP International Corp. Media Tablet"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 13
	Num_axes is 20
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 16383
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 16383
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 8 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 9 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 10 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 11 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 12 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 13 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 14 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 15 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 16 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 17 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 18 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 19 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Num_axes is 4
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 255
		Resolution is 10000

```

the xorg.0.log could be useful?
```
(II) config/hal: Adding input device WALTOP International Corp. Media Tablet
(**) WALTOP International Corp. Media Tablet: always reports core events
(**) WALTOP International Corp. Media Tablet: Device: "/dev/input/event4"
(II) WALTOP International Corp. Media Tablet: Found 9 mouse buttons
(II) WALTOP International Corp. Media Tablet: Found x and y relative axes
(II) WALTOP International Corp. Media Tablet: Found scroll wheel(s)
(II) WALTOP International Corp. Media Tablet: Found x and y absolute axes
(II) WALTOP International Corp. Media Tablet: Found absolute touchpad
(II) WALTOP International Corp. Media Tablet: Found keys
(II) WALTOP International Corp. Media Tablet: Configuring as touchpad
(II) WALTOP International Corp. Media Tablet: Configuring as keyboard
(**) WALTOP International Corp. Media Tablet: YAxisMapping: buttons 4 and 5
(**) WALTOP International Corp. Media Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "WALTOP International Corp. Media Tablet" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "it"
(WW) WALTOP International Corp. Media Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Media Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Media Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Media Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Media Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Media Tablet: initialized for absolute axes.

```

or the syslog:
```
Nov  7 00:50:48 bobogrigio kernel: [11920.970618] usb 2-6: new full speed USB device using ohci_hcd and address 6
Nov  7 00:50:49 bobogrigio kernel: [11921.199393] usb 2-6: configuration #1 chosen from 1 choice
Nov  7 00:50:49 bobogrigio kernel: [11921.223403] input: WALTOP International Corp. Media Tablet as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input8
Nov  7 00:50:49 bobogrigio kernel: [11921.223608] generic-usb 0003:172F:0500.0003: input,hidraw0: USB HID v1.10 Mouse [WALTOP International Corp. Media Tablet] on usb-0000:00:02.0-6/input0
```

But i am in the same place: no pressure from the pen and coordinte wrong
Always a big thank!

---

### Post by Favux on 2009-11-06
Hi lospo,

Now wacom is in lsmod.

Xinput/Xorg.0.log shows the evdev driver has your Waltop tablet, not linuxwacom.

Did you remember to install the new wacom.fdi for Waltop?

Could you explain to me how you compiled the 0.8.4-3 linuxwacom?

---

### Post by lospo on 2009-11-07
hi favux,

now something is different: i checked the fdi file and it was the old default, i change it to the one pasted above and now... the tablet doesn't work anymore... :(

that's my fdi file wich i copied from other post
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>

```
wich is the one i copied from [http://ubuntuforums.org/showthread.php?t=1261407](http://ubuntuforums.org/showthread.php?t=1261407) (Favux_Jaunty_ Waltop tablet_test 1_10-wacom.fdi) as you said in the first posts, right?

I used this guide, as you tell me: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) patching the wcmUSB.c. 
Everything works fine, and the module was created successfully.

maybe it's useful the Xorg.o.log:
```

(II) config/hal: Adding input device stylus
(**) stylus: always reports core events
(**) stylus device is /dev/input/event4
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event4"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=16383 maxY=16383 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=16383 bottom Y=16383 resol X=1016 resol Y=1016


```


Thanks!

---

### Post by lospo on 2009-11-10
Arg!

Favux... maybe you have some other aces in your hand?

news:

```

(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-3 $
(**) stylus: always reports core events
(**) stylus device is /dev/input/event6
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event6"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=16383 maxY=16383 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=16383 bottom Y=16383 resol X=1016 resol Y=1016

```

seems everythimg ok, but nothing works for me!

---

### Post by Favux on 2009-11-10
Hi lospo,

I don't know.  It does look like it should work now.  Does it work in Windows?  Was it working and then stopped working?  Did you get a kernel update?

Maybe something else is grabbing the tablet later in Xorg.0.log.  Can you attach the whole log.  Right click on in and "Create Archive".  And the use Manage Attachments to post it.

We also may need to look at lshal.  You'd use "lshal>lshal.txt" and compress and attach it too.

---

### Post by lospo on 2009-11-10
hi

no, no kernel update.
working before karmic upgrade, then working only for pointment, not for the click.
After the compiling of personalized module with wcmUSB.c modded it completely stop working, no coordinate works, no button, no scrolls... nothing.

The strange is that it worked like a charm in Jaunty, i've buyed this because i haven't windows and it WAS supported when i decided to buy :(

Maybe the better way is to wait a kernel upgrade from ubuntu?

Attached the file log you request...

---

### Post by gdodinet on 2009-11-10
I experiment the exact same problem than Lopso. However, and that's the whole point of my post, I got it (i.e. a Trust TB 7300 tablet) working twice under Karmic (reader beware: it doesn't work at the moment) - so maybe there's still some *configuration hope*. 

I can't remember what i did the first time to make it work, nor can i remember what i did to undo it. However when it stopped working i tried to build the patched wacom drivers. Obviously that didn't work. Then i uninstalled all tablet drivers and purged all tablet configuration, including hal and udev config files, then rebooted. 

I reinstalled the aiptek driver, created the fdi file again, but not the udev rule file as the Aiptek wiki page says it is no longer required. 

Rebooted again. The tablet although registered as an XExtensionPointer (Type=Stylus, and so on) still didn't work. I realized that the aiptek module wasn't registered. modprobe aiptek, added it to /etc/modules, then restarted udev and hal, and TADA, it worked. Well, until i rebooted. 

Since then i got nothing, not even the pointer control.. So i'm a bit lost here. I did so many things without taking any notes, that i can't retrace the steps i've taken. 

As per xorg log, the tablet is correctly registered with the Aiptek driver, and xinput and lshal both tell me that the correct (correct as in: matching my readings) configuration has been applied (driver, threshold, resolution, etc.).

Edit: forgot to tell the tablet is, i guess, correctly communicating with the system: lots of garbage when i open /dev/input/event5 (or /dev/input/aiptek, if i add the udev rule) and let the stylus stroll on the tablet.

I'm not sure who can fix this: kernel provider (ubuntu team) or driver provider (aiptek comitters). 

Anyway I just wanted to report my experience with this frustrating "aiptek on karmic" issue, and i don't really expect anything, but thanks for reading this far though.

---

### Post by Favux on 2009-11-10
Hi gdodinet,

Welcome to Ubuntu Forums!

Thanks for your post.  Very helpful.  Is the module aiptek.ko?

What we've noticed on some other usb devices is another .fdi/driver will re-grab it.  Like the Synaptic .fdi or evdev.  But lospo's Xorg.0.log seems to show the Wacom driver grabbing it successfully and the lshal seems good too.  His tablet identifies in lsahl as:
```
  usb_device.product = 'Media Tablet'  (string)
  usb_device.product_id = 1280  (0x500)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'WALTOP International Corp.'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
  usb_device.version = 1.1 (1.1) (double)
```
Is the Trust TB 7300 tablet also a Waltop?

---

### Post by gdodinet on 2009-11-10
Hi Favux,

The driver is the aiptek.ko (freshly reinstalled through apt-get).

And the tablet is indeed the exact same one: 

idVendor=172f, idProduct=0500, info.product='WALTOP International Corp. Media Tablet'. Although, strangely enough, lsusb won't identify it. 
 
```

Excerpt	from lsusb

Bus 002 Device 005: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 002 Device 004: ID 172f:0500  
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard

```

But then again i can't tell if that was already the case under Jaunty or not. 

I also encountered the evdev issue making the tablet recognized as a keyboard - but this issue *auto-magically* disappeared after all the manipulations i've done. 

Maybe related or not, but i encounter the "Unable to access /devices/pci0000:..." issue reported here: [https://bugs.launchpad.net/usplash/+bug/439648](https://bugs.launchpad.net/usplash/+bug/439648). I can't help but notice that one of the two devices that trigger this message is the onboard usb sound card, the other one being the tablet. 

Just noticed a thing that may be worth investigating: /sys/bus/usb/drivers/aiptek doesn't contain the expected '*usb-slot-connector*' folder (ref: [http://aiptektablet.sourceforge.net/kernel.html](http://aiptektablet.sourceforge.net/kernel.html)). Thinking about it, it's actually no real surprise since the tablet doesn't react at all, but i'll need some time to see what i can do with this information - even nothing is an option.

---

### Post by Favux on 2009-11-10
Hi gdodinet,

But lsusb is at least giving the Vendor and Product ID's:
```
Bus 002 Device 004: ID 172f:0500 
```

Well since it is a Waltop (and not an Aiptek) you could try to use the Wacom drivers like others with the Waltop are doing.  See post #3 on this thread for the links.  We probably need to fine tune the tablet we are using in the wcmUSB.c, etc.  Maybe you can help.  We also found the Waltop driver on the Waltop site.  It seems old, but maybe you want to take a look at that too?

---

### Post by gdodinet on 2009-11-10
Favux,

I am gonna give the patched wacom driver another try. Not tonight though, because it is getting pretty late here. Thanks for your time. I'll keep you posted.

Edit: concerning the Waltop provided driver, i downloaded it a couple of days ago but didn't build it because it targets at most kernel 2.6.27 if i remember correctly.

---

### Post by lospo on 2009-11-11
Re-doing all the process but with the 8.5.3 driver from linuxwacom and the modded wcmUSB.c.

Now i have this log:

```

(II) config/hal: Adding input device WALTOP International Corp. Media Tablet
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-3 $
(EE) PreInit returned NULL for "WALTOP International Corp. Media Tablet"
(EE) config/hal: NewInputDeviceRequest failed (8)

```

what's this: [NewInputDeviceRequest failed (8)] ?

---

### Post by rohtie on 2009-11-11
I also have a trust TB-7300 tablet and I experience the same problems. 
In interpid, it didn't work. In jaunty it worked. In karmic, it wont work...

---

### Post by Favux on 2009-11-11
Hi lospo,

Starting with the linuxwacom 0.8.5 series they added another layer of checking ID's (tool ID's?).  It's a "static structure" in, I think, wcmCommon.c.  So 0.8.4-3 may be the end of the road for using the Wacom drivers for Waltop.  Unless someone does some coding beyond the simple hack we've done.

Basically it seems to be setting up tools for each tablet.  It's disabled my eraser.  Gimp now thinks the stylus tip and eraser are the same, at least on 0.8.5-1.  It looks like they've skipped 0.8.5-2.  I hope 0.8.5-3 fixes my eraser problem.

In other words 0.8.4-3 is a lot better for what you want to do and the Karmic version is 0.8.4-1 anyway.


Hi rohtie,

Hopefully you and gdodinet can figure it out using the .fdi and "patch" on the other thread.

Good luck!

---

### Post by gdodinet on 2009-11-11
Yes, hopefully we can figure this out. Actually i followed the same path than Lopso and tried to build 0.8.5. 

However I think i then left some things uncleaned because wacom module (0.8.4 after reinstallation) can't be found anymore - although i can insmod it by providing the full path. That's all for today, i'll continue this at the end of the week.

---

### Post by aruizhom on 2009-11-11
Hi, Everybody!

I have an Trust Tb-7300, and It doesn't work on Ubuntu Karmic, too. I booted my PC using a 9.04 Live CD, and It worked Well!

Then I tried to change the 10linuxwacom.fdi, editing and adding the text I saw [here]("http://www.sewje.co.uk/blog/?p=12"). The Xorg did not load! I had to recover the last fdi using the Live CD. Then I tried to use the one Favux recommended [here]("http://ubuntuforums.org/showthread.php?t=1261407"), and I din't load Ubuntu, too. I tried another one mixing information: now, I'm using Ubuntu 9.10 again, but my 10-linuxwacom.fdi is marked with an "X" in Nautilus (?). I think something goes wrong
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

I tried to use the instruction "lshal>lshal.txt", but I didn't work. The message on the Terminal window was: "Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready."

"xsetwacom list" din't do nothing...

Sorry, but my Linux level is very low.I'm trying to understand everything you said in your replies, and I have a messy inside my head! 

I apologize for the inconvenience, Are there someone who could help me?

I included all the files I know can be helpful

Thak you so much!

---

### Post by aruizhom on 2009-11-11
Hi!

I 've changed 10.linuxwacom.fdi again, with the deafult values, and I've obtained the lshal file. I'll send you the new log files

Ah! I didn't explain before  that I can use the tablet pen to move the pointer around the screen, but the buttons don't work. (They worked on 9.04...)

Thanks!

---

### Post by Favux on 2009-11-11
Hi aruizhom,

Welcome to Ubuntu Forums!

If you use the .fdi I posted that you found you also need to compile linuxwacom 0.8.3-5 using the "patched" wcmUSB.c.  The links are in post #3 of this thread.

The problem is it may not work for everyone and we're trying to figure out why.  Maybe we need to make some changes to wcmUSB.c, say another tablet type?

What buttons aren't working?  Your stylus buttons?

---

### Post by aruizhom on 2009-11-11
Hi, Favux! Thank you for your time! Tomorrow 'll try to compile that file in Linux (for the very first time!). Now It's late, and I have no time...

About the stylus buttons... Please, excuse me, cos I don't have any experience in Tablet PCs, I don't understand you. Pen has two buttons, like the mouse, and I think they should work like the mouse's. At least one of them works like right button on ubuntu 9.04 : I used It to click on Desktop Icons to open files, programs.... In Karmic none of them works. Only I can move the pointer on the screen. When I run The GImp I can't paint either...

---

### Post by gdodinet on 2009-11-12
Ok, so I've installed the linuxwacom-0.8.4-3 again. Went smoothly except for the part where I decided to grab the source tarball fresh from sourceforge again and forgot to replace wcmUSB.c. Of course X wouldn't start.. 

That said, does it work now? Not quite (not at all actually). As reported before I even have no pointer control with the linuxwacom driver. In fact, and that's troubling me, the tablet does not seem to communicate with the system. 

```

$cat /dev/input/event5
(stays blank when i scratch the tablet)

```

So i may have done something i shouldn't have. This time, however i took some notes. I'll paste the commands i used as is in (code)(/code) blocks, followed by some observations and/or remarks.

**Step 0)** Install linuxwacom driver

/etc/hal/fdi/policy/10-linuxwacom.fdi is the exact same one Favux posted (without any modification)

```

$ rm /usr/share/hal/fdi/policy/20thirdpaty/10-linuxwacom.fdi
$ echo wacom >> /etc/modules

```

=> Perhaps linuxwacom fdi file *needs* to reside in 20thirdparty? 

**Step 1)** First reboot

Observations: no pointer control. 
- no pointer control
- tablet registered as an XExtensionKeyboard ("stylus"	id=2	[XExtensionKeyboard])
- tablet seems to be correctly registered with HAL (see system info below)
- xorg log seems to indicate that the wacom driver had been successfuly loaded (see system info below)

```

$ lsmod | grep wacom
$
$ modprobe wacom
FATAL: module wacom not found
$ grep wacom /etc/modules
wacom
$ 
$ depmod -a
$ grep wacom /lib/modules/2.6.31-14-generic/modules.dep
kernel/drivers/input/tablet/wacom.ko:
kernel/drivers/input/touchscreen/wacom_w8001.ko:
kernel/drivers/hid/hid-wacom.ko:
$ reboot

```

=> Weird thing here is that i don't remember X complained about missing module wacom. Anyway i guess this indicates something went wrong with the install. Continuing from this state anyway.

**Step 2)** Second reboot 

Observations:
- tablet still registered as an XEtensionKeyboard
- still no pointer control

**System info**
System info after both steps 

```

$ xinput --list
...
"stylus"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
...

```

=> "stylus" seems right here since we override info.product in linuxwacom.fdi

```

$ more /var/log/Xorg.0.log
...
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-3 $
(**) stylus: always reports core events
(**) stylus device is /dev/input/event5
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event5"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=16383 maxY=16383 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=16383 bottom Y=16383 resol X=1016 resol Y=1016
(II) config/hal: Adding input device Dell Dell USB Keyboard
...

```

=> Tablet seems correctly registered. No one else seems to reclaim /dev/input/event5:

```

$ grep /dev/input/event5 /var/log/Xorg.0.log
(**) stylus device is /dev/input/event5
(**) Option "Device" "/dev/input/event5"
$

```

```

$ lshal 
...
udi = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard', 'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
...

```

=> That keyboard stuff troubles me. We'll get into that later.

```

$ ls -l /dev/input/by-path
total 0
...
lrwxrwxrwx 1 root root 9 2009-11-12 01:17 pci-0000:00:02.0-usb-0:4:1.0-event -> ../event5
...

```

=> seems ok. tablet (usb-2-4:1.0) writes to event5 (supposedly)

```

$ wacdump /dev/input/event5
...

```

=> Wacdump version: 0.8.2. All keys but CLS are set to 'unknown'; CLS is set to 'USB'. All values are set to 0, ranges are correctly retrieved though; keys are not mapped.

```

$ wacomcpl list

```

=> 'stylus' appears in the list. However the configuration panel cannot be loaded (Error is: "can't read 'isLCD(1280)': no such element in array" - in "updateDevice" line 24). About wacomcpl, there's something i'm missing here: the list is empty if i don't override the 'info.product' value. Perhaps it's the way the linuxwacom driver and wacom tools suite are meant to work but it seems weird to me (is it really hardcoded?).


```

$ grep stylus /var/log/messages
Nov 12 20:28:08 GUB kernel: [    2.998110] input: WALTOP International Corp. Media Tablet as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input5
Nov 12 20:28:08 GUB kernel: [    2.998194] generic-usb 0003:172F:0500.0003: input,hidraw2: USB HID v1.10 Mouse [WALTOP International Corp. Media Tablet] on usb-0000:00:02.0-4/input0

```

=> I may be wrong, but this doesn't seem right to me. Shouldn't be wacom driver referenced at this point? 


Concerning the keyboard thingie, i tried removing 'debian-setup-keyboard' from the callbacks list, and all 'key*' values from the capabilities list. 

```

...
<remove key="info.callouts.add" type="strlist">debian-setup-keyboard</remove>
<remove key="info.capabilities" type="strlist">input.keyboard</remove>
...

```

As you can guess that didn't change the tablet misbehavior. I eventually reverted back to a fdi file similar to the one i had under Jaunty (with the aiptek driver), but this didn't change anything neither. 

I'm not sure if this kind of feedback is helpful, but in any case i had to report what i tried. 

So i can only see a couple of options here: (i) wait for a working Aiptek driver (which used to work almost out of the box under Jaunty), (ii) boot against a kernel 2.6.28 although i don't know if this won't have other possible side-effects, nor if this might even work.

Favux, if you wanna me to try a few things i'd gladly be your guinea pig for a time before giving up and eventually falling back to one of the aforementioned options.


Regards

---

### Post by Favux on 2009-11-12
Hi gdodinet,

Thanks, lot's of good stuff.

If the wacom.ko still isn't auto-loading after the depmod -a just add "wacom" (without the quotes) to the modules file at the end:
```
gksudo gedit /etc/modules
```
and reboot.

Wacdump won't work after Xserver starts because wacom_drv.so grabs the input and won't let wacdump see it.  Try "xidump stylus".

I haven't seen any evidence that there's a Waltop mouse like the Wacom mouse (puck).  So we should probably remove the "cursor" stuff from the .fdi.

Also does the Waltop stylus have an eraser?

---

### Post by gdodinet on 2009-11-12
Favux,

xidump is more pleasant, but unfortunately there's nothing i can use. For info here's the output:

```

InputDevice: stylus    Valuators: Absolute
             x-axis    y-axis   pressure   x-tilt    y-tilt     wheel
     data:
      min:  +00000    +00000    +00000    -00064    -00064    +00000
      max:  +16383    +16383    +01023    +00063    +00063    +01023
      res:  +01016    +01016    +00001    +00001    +00001    +00001

```

Concerning the module, after i ran depmod it auto-loads. The weird part however (which might indicate some installation issues on my side) is that i added it to /etc/modules before the first reboot (as per the second snippet in my previous post).

Last, concerning the device type, there is indeed no mouse (as in: real mouse like with my old graphire 2), there is no eraser neither (at least for the TB-7300 model) and, i think, no pad. I tried to remove all three wacom types declaration, but this doesn't change anyhting.

Here's my current fdi file: 

```

$ more /etc/hal/fdi/policy/10-linuxwacom.fdi 
<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>

	<merge key="info.product" type="string">stylus</merge>

        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>

        <remove key="info.callouts.add" type="strlist">debian-setup-keyboard</remove>
        <remove key="info.capabilities" type="strlist">input.keyboard</remove>
        <remove key="info.capabilities" type="strlist">input.keypad</remove>
        <remove key="info.capabilities" type="strlist">input.keys</remove>

	<merge key="input.x11_options.Button2" type="string">2</merge>
	<merge key="input.x11_options.Button3" type="string">3</merge>	
	<merge key="input.x11_options.Threshold" type="string">5</merge>
	<merge key="input.x11_options.zMin" type="string">0</merge>
	<merge key="input.x11_options.zMax" type="string">1023</merge>
	<merge key="input.x11_options.USB" type="string">On</merge>
	<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
	<merge key="input.x11_options.Mode" type="string">absolute</merge>

    </match>
  </device>
</deviceinfo>

``` 

The options may not be quite right (for instance, zMin vs. minZ?), but then again the observed behaviour is the same when using the fdi you posted. And it seemed to me (while reading xorg log) that the driver was able to discover the correct values (and that is definitively a positive sign). Please also note that deleting the *<remove ...* elements do not change anything.

Edit- Actually i just realize that it must be futile to add those "<remove" elements. They merely point a mis-detection issue. I mean hal adds this 'debian-setup-keyboard' callback because it thinks the device might act as a keyboard (thus the XExtensionKeyboard), right?

---

### Post by Favux on 2009-11-12
Hi gdodinet,

Sorry, should have cleared that up.  Seeing [XExtensionKeyboard] in "xinput --list" is a quick way I use to verify the linuxwacom drivers have grabbed the tablet.  So that's expected/desired behavior.  No buttons on the tablet (pad)?

---

### Post by gdodinet on 2009-11-12
Oh, sure, there are! 34 programmable buttons (K1 to K34) plus 5 buttons at the top to control various things such as zoom, ratio, etc. 

Truth is i never used them, i do not even use the two buttons on the pen. Actually i find those pen buttons rather annoying, as i tend to inadvertently push them. 

Anyway the XExtensionKeyboard type misleads me since i used to see the tablet as an XExtensionPointer. So one less thing to worry about.

Thanks for the info. 

If that may be of use, there are also 2 wheels on the tablet (top-right and top-left, with both yet another button at the center) - I do not use them neither..

---

### Post by Favux on 2009-11-12
Hi gdodinet,

Right.  XExtensionPointer means a mouse/touchpad .fdi/driver has it.  The Aiptek driver also shows XExtensionPointer.

The 5 buttons sound like a "pad" as do the 2 wheels (equivalent to Wacom sliders?).  Question is do they emulate a Wacom pad closely enough for us to fool the linuxwacom drivers into supporting/implementing them?  I'm pretty sure the linuxwacom drivers won't support the 34 programmable buttons.

Do some of the Waltop styli have an eraser?  We should probably leave that in the .fdi for now.

---

### Post by gdodinet on 2009-11-12
Favux, 

I quickly searched what the wacom sliders were and i think they are similar to the waltop wheels. I also think (without any evidence because i've never read the tablet manual) that the zoom and scroll buttons at the top of the tablet might control the behavior of the wheels. The programmable buttons however are virtual buttons, triggered by the pen - they're supposed to be used to pick up tools in a paint software, for instance.

That said, i will uninstall the wacom driver this week-end and redo a clean install. I'm pretty sure i did something wrong. The how-to is supposed to work, this is even reported elsewhere ([link](http://blog.mazesloup.fr/index.php/post/2009/10/25/Karmic%2C-Hal-et-Tablet-Medion-SOLVED-!)). Sure the tablet model referenced in the previous link is not the same, but the vendor is. So if this still doesn't work at least we will have an additional clue - perhaps meaning the TB-7300 is not quite supported, and that one more trick (yet to find) is needed.

Edit- Forgot to answer you about the eraser: the waltop stylus has no eraser: only one side of the stylus is used, as there's no active area at the end of the pen.

Thanks again for your time.

---

### Post by gdodinet on 2009-11-13
Just tried to reinstall from a fresh tree (0.8.4-1 grabbed through apt-get). Doesn't work better. 

Before reinstalling i uninstalled the 0.8.4-3 and rebooted. I got the pointer control back (alongside with the known "stylus grabs focus" issue). While recompiling i realized that i messed up when doing the very first install from source: i copied the hid-ids header file to /usr/src/linux-headers-2.6.31-14/drivers/hid/. I don't think this would cause any harm, would it?, but i thought it might worth mentionning. 

After reinstallation, things weren't better. I then modified the hid-ids.h and added waltop entries (hell, why not since it doesn't work already). You can guess it didn't go better. Also i wonder why the how-to didn't mention to copy the hid-wacom.ko to /lib/modules/2.6.31-14-generic/kernel/drivers/hid/hid-wacom.ko. Is that unnecessary, or even potentially harmful? I had a version from mid october. I replaced it with the one generated during the build phase. Copied the wacom.ko again. Rebooted. Still no pointer control. 

HAL still correctly detects the tablet and correctly sets the default values. Xorg log say everyone is happy (except for me obviously), and nothing is written to /dev/input/event5 when i move the pen upon the tablet surface. Could this be the core issue?

---

### Post by gdodinet on 2009-11-13
Ok, finally got it working. If you just want to try what worked for me, you may skip to section 2.

_SECTION 1- my little story_

After some more time trying to get the linuxwacom working, i decided arbitrarily that i wouldn't make it work. At that point my attempts with both the aiptek driver and the wacom driver had failed. 

I remembered there was another driver, and luckily for me i found a post stating the version 0.7.0 of the [wizardpen were "karmic-compliant"](http://digitalbluewave.blogspot.com/2009/09/wizardpen-driver-07-series-compatible.html). 

Not much too lose, i decide to give it a try. I declare the ppa repository ([https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)) and install the driver. Reboot. No tablet. Xorg log states the module failed to load (wizarpen_drv.so: WRONG CLASS ELF32). Some kind of 32/64 bits issue again? I try to build the driver from source. I Reboot.. and the tablet is working. So i reboot again! And the tablet is still there - it was 6 minutes ago, so i hope it will last - i remember that the aiptek driver was not reliable. 

Next section details the steps needed to build the version 0.7.1 of the wizardpen driver.

_SECTION 2- building the wizardpen driver_

Those instructions can be found elsewhere but i report there as well for sake of simplicity. They are adapted from [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen).


**I. Prepare the install**

**1.** *Create the directory structure*

```

$ mkdir ~/wizardpen
$ cd ~/wizardpen
```

**2.** *Add the repository information (can be found [here](https://launchpad.net/~doctormo/+archive/xorg-wizardpen))*

add the following two lines to /etc/apt/sources.list

```

deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu jaunty main
deb-src http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu jaunty main 
```

add the authentication key (edit 20091127)

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 113659DF
```

**3.** *Update the repository definition*

```

$ sudo apt-get update
```

**4.** *Get the source *

```

apt-get source xserver-xorg-input-wizardpen
```

**II. Build the driver**

**1.** *Compile*

```

$ cd xserver-xorg-input-wizardpen-0.7.1
$ ./configure --prefix=/usr
$ make
$ sudo make install
```

**2.** *Create a udev rule*

Note- the udev rule creation step may be optional, i'm not sure of that.

Create the file /etc/udev/rules.d/010_tablet.rules and add that line: 

```

KERNEL=="event*",ATTRS{idVendor}=="172f",SYMLINK+="input/tablet"
```

If you have multiple Waltop devices you may need to also add the condition ATTRS{idProduct}=="0500" (for the trust tb-7300 model).

**3.** *Create the fdi policy file*

Here's the fdi file i use (/etc/hal/fdi/policy/99-x11-wizardpen.fdi):

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="WALTOP">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```

**4.** *(optional) Restart udev and calibrate your tablet*

```

$ sudo service udev restart
$ cd ~/wizardpen/xserver-xorg-input-wizardpen-0.7.1/calibrate 
```

Follow the instructions on screen. Forget the xorg.conf instructions and save the info for later use (if any - especially tweaking the fdi policy file if you need to).

**5. *Take some precaution***

Carefully read the *"Making X start without a tablet connected"* on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) (i personally skip that step)

**6.** *Reboot*

Your tablet should be working (mine has at that time).

I hope this might be helpful.

Regards


Edit- thought i could also post my xinput info after successful installation: 

```

$ xinput --list
...
"WALTOP International Corp. Media Tablet"	id=2	[XExtensionPointer]
	Type is WizardPen Tablet
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1680
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 1050
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000
...

```

---

### Post by aruizhom on 2009-11-13
Congratulations upgodinet! U make It happens!

Unfortunately I don't get lucky following your steps. I can't configure my Trust TB-7300...

xinput returns:

xinput --list
...
"WALTOP International Corp. Media Tablet"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 13
    Num_axes is 20
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 16383
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 16383
        Resolution is 10000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 10000
    Axis 3 :
        Min_value is 0
 ...

So now my Tablet is recognized as a keyboard...

I realized that something goes wrong building the driver. I can't calibrate the table cos there are some parts they hadn't been built.

I'm sorry, I'm a beginner user and I'm wondering If you skip some clear steps I don't know yet. So, could you kindly help me?

Thank you so much!

---

### Post by Favux on 2009-11-14
Hi gdodinet,

Congratulations!  A working tablet!

A few things.

I thought the French site was a great find.  I'm surprised you didn't try modifying the wcmUSB.c like that site mentioned.  Only the one line to add the Waltop Vendor ID.  No messing with calling it some Wacom tablet and resolution etc.  I was interested if that worked.

When you copied the hid-ids.h you said you copied it to:
```
/usr/src/linux-headers-2.6.31-14/drivers/hid/
```
Did you mean?:
```
/lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```

As far as I know there isn't a hid-wacom.ko.  It's wacom.ko and it should be copied to:
```
/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
not
```
/lib/modules/2.6.31-14-generic/kernel/drivers/hid/hid-wacom.ko
```
And you should copy the newly compiled wacom.ko.

So in Karmic is there now a hid-wacom.ko?  That doesn't sound right to me.


Hi aruizhom,

Did you put in the modified (for Waltop) 10-linuxwacom.fdi?  It sounds like you did and the linuxwacom drivers are configured to your tablet.  That would give you the [XExtensionKeyboard] you are seeing in "xinput --list".  Also you are on Karmic correct?

---

### Post by gdodinet on 2009-11-14
Airuzhom,

Did you try to build the wizardpen driver or the linuxwacom driver? In the latter
case i would be of no help since i couldn't make the wacom driver work myself. However in the former case, i can try to help. Let's assume you try to install the wizardpen driver. As Favux said earlier, the fact that the tablet got registered as XExtensionKeyboard may indicate that the wacom driver reclaimed the device (you can verify that in xorg log) : 

```
$ more /var/log/Xorg.0.log
```

**1. Clean the system**

So we're gonna make sure first that linuxwacom is correctly uninstalled (note- don't forget to adapt paths and versions below):

```
$ cd linuxwacom-0.8.4-3
$ sudo apt-get install wacom-tools xserver-xorg-input-wacom
$ sudo apt-get --purge remove wacom-tools xserver-xorg-input-wacom
$ sudo make uninstall
```

We can remove aiptek driver traces the same way if we need to:

```
$ sudo apt-get install xserver-xorg-input-aiptek
$ sudo apt-get --purge remove xserver-xorg-input-aiptek
```


Now let's clean up the wizardpen installation.

```
$ cd xserver-xorg-input-wizardpen-0.7.1
$ sudo make uninstall
```

If we reboot now, the tablet should control the pointer, but pointer should get locked if we press the stylus. If that's the case, good, we can start from a clean slate.

**2. Reinstall the wizardpen driver**

Let's try to reinstall the wizardpen driver. First, let me say that i only built because i have a 64 bits system, and the prebuilt package for amd64 seemed broken. 

*If you run a 32 bits system*, you may be luckier by just installing the prebuilt package : 

```
$ sudo apt-get install xserver-xorg-input-wizardpen
```

*If you're running a 64 bits system*, you should start recompiling the driver (see my previous post). 

You say: "there are some parts they hadn't been built". I don't think i can help diagnosticate what went wrong, but in any case what error did you get?

---

### Post by gdodinet on 2009-11-14
Favux,

Concerning wcmUSB.c, you make a good point. Actually i simply assumed it was the same than the patched one we can find on this forum. But you're right: there's three modified lines in the forum one, if i remember correctly, not just one. 

The header file has been copied to /lib/modules/`uname -r`/build/drivers/hid/ - however i also find it in /usr/src/linux-headers-2.6.31-14/drivers/hid/, so a locate hid-ids.h returns the last one too (and then i copied/pasted the wrong one). Anyway without the hid file linuxwacom doesn't build, as pointed out in the how-to (i tried removing it).

As you can see below, the compile phase generates an hid-wacom.ko (alongside the wacom.ko) for the 2.6.31 kernel. I merely replaced the one i already had in /lib/modules/2.6.31-14-generic/kernel/drivers/hid/. 

```
$ locate -e wacom.ko
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.4-3/src/2.6.31/.hid-wacom.ko.cmd
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.4-3/src/2.6.31/.wacom.ko.cmd
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.4-3/src/2.6.31/hid-wacom.ko
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.4-3/src/2.6.31/wacom.ko
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.5-3/src/2.6.28/.wacom.ko.cmd
/home/gilles/Temp/linuxwacom/linuxwacom-0.8.5-3/src/2.6.28/wacom.ko
/home/gilles/Temp/linuxwacom/wacom-tools-0.8.4.1/hid-wacom.ko.BAK
/home/gilles/Temp/linuxwacom/wacom-tools-0.8.4.1/linuxwacom/src/2.6.31/.hid-wacom.ko.cmd
/home/gilles/Temp/linuxwacom/wacom-tools-0.8.4.1/linuxwacom/src/2.6.31/.wacom.ko.cmd
/home/gilles/Temp/linuxwacom/wacom-tools-0.8.4.1/linuxwacom/src/2.6.31/hid-wacom.ko
/home/gilles/Temp/linuxwacom/wacom-tools-0.8.4.1/linuxwacom/src/2.6.31/wacom.ko
...
``` 

I have followed the how-to several times. But eventually i tried different things after i realized/decided it wouldn't work for me. Overriding the hid-wacom.ko is just one of the things i did try - i mean there was already a hid-wacom.ko from october 16, so i guessed overriding it with the generated one would be harmless (and it appears it actually was, but it was not helpful either).

Regards

---

### Post by Favux on 2009-11-14
Hi gdodinet,

I asked for some help on the hid-wacom.ko because it's new to me.  We think it's for the blue tooth Wacom tablets.  If so it shouldn't have any effect on your tablet.  I could look for mesilliac's [thread]("http://ubuntuforums.org/showthread.php?t=674738") where he sets up blue tooth for the Wacom Graphire Bluetooth tablets or the [wiki]("https://help.ubuntu.com/community/WacomGraphireBluetooth") to check but I think that's probably right.

---

### Post by gdodinet on 2009-11-15
Hi Favux,

Thanks for asking around. I wasn't too worried about the new hid-wacom.ko because i haven't noticed any side-effects yet. However it's nice to hear that the chances it could cause problems are almost zero.

Regards

---

### Post by euripides on 2009-11-22
Hello guys,

I just wanted to confirm that gdodinet's instructions worked with my 14000u tablet and karmic as well!

Thank you very much,
you made my day!

- euripides

---

### Post by adrix89 on 2009-11-25
```
adrix89@adrix89-laptop:~/Desktop/linuxwacom-0.8.4-4$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-15-generic/build
checking kernel version... 2.6.31-15-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Uninit is called... yes
checking if Xorg is version 1.6 or later... yes
yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for XORG... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/2.6.28/Makefile
config.status: creating src/2.6.31/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.31
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-15-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
adrix89@adrix89-laptop:~/Desktop/linuxwacom-0.8.4-4$ sudo apt-get install libc-wrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc-wrapper
adrix89@adrix89-laptop:~/Desktop/linuxwacom-0.8.4-4$ sudo apt-get install libc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc
adrix89@adrix89-laptop:~/Desktop/linuxwacom-0.8.4-4$ make
Making all in src
make[1]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src'
Making all in .
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src'
Making all in wacomxi
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/wacomxi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/util'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/util'
Making all in xdrv
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c > .depend
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/xdrv'
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/xdrv'
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o wcmTilt2Rotation.o -Bstatic -lgcc
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/xdrv'
Making all in 2.6.31
make[2]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31'
cp -f ../2.6.27/wacom.h .
cp -f ../2.6.28/wacom_wac.h .
cp -f ../2.6.28/wacom_sys.c .
cp -f ../2.6.28/wacom_wac.c .
cp /lib/modules/2.6.31-15-generic/build/drivers/hid/hid-ids.h .
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.31-15-generic/build M=/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom_wac.o
  CC [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom_sys.o
  LD [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom.o
  CC [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/hid-wacom.o
  Building modules, stage 2.
  MODPOST 2 modules
  LD [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/hid-wacom.ko
  LD [M]  /home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[2]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src/2.6.31'
make[1]: Leaving directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4/src'
make[1]: Entering directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4'
make[1]: Nothing to be done for `all-am'.
make[1]: Leavint of allg directory `/home/adrix89/Desktop/linuxwacom-0.8.4-4'
adrix89@adrix89-laptop:~/Desktop/linuxwacom-0.8.4-4$ 

```First of all I'm new to this and have received the tablet(14000U) today
Can somebody tell me what I'm doing wrong?
It tells me there is no hid
But I have right on the generic kernels
Using karmic

---

### Post by Favux on 2009-11-25
Hi adrix89,

Welcome to Ubuntu Forums!

In Karmic the hid-ids is now longer in the kernel-headers so you need to add them manually before you compile:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
```
then copy it into place:
```
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```
Now you should be good.

---

### Post by adrix89 on 2009-11-26
Already did that step a couple of times
And even made sure is on all lib/modules/ kernel versions that I have

---

### Post by Favux on 2009-11-26
Let's look at your kernel:
```
cat /proc/version_signature
```
and
```
uname -m
```

---

### Post by adrix89 on 2009-11-26
```
adrix89@adrix89-laptop:~$ cat /proc/version_signature
Ubuntu 2.6.31-15.50-generic
adrix89@adrix89-laptop:~$ uname -m
x86_64
adrix89@adrix89-laptop:~$ 
```

---

### Post by tomankirilov on 2009-11-27
> **gdodinet said:**
> Ok, finally got it working. If you just want to try what worked for me, you may skip to section 2.

_SECTION 1- my little story_

After some more time trying to get the linuxwacom working, i decided arbitrarily that i wouldn't make it work. At that point my attempts with both the aiptek driver and the wacom driver had failed. 

I remembered there was another driver, and luckily for me i found a post stating the version 0.7.0 of the [wizardpen were "karmic-compliant"]("http://digitalbluewave.blogspot.com/2009/09/wizardpen-driver-07-series-compatible.html"). 

Not much too lose, i decide to give it a try. I declare the ppa repository ([https://launchpad.net/~doctormo/+archive/xorg-wizardpen]("https://launchpad.net/%7Edoctormo/+archive/xorg-wizardpen")) and install the driver. Reboot. No tablet. Xorg log states the module failed to load (wizarpen_drv.so: WRONG CLASS ELF32). Some kind of 32/64 bits issue again? I try to build the driver from source. I Reboot.. and the tablet is working. So i reboot again! And the tablet is still there - it was 6 minutes ago, so i hope it will last - i remember that the aiptek driver was not reliable. 

Next section details the steps needed to build the version 0.7.1 of the wizardpen driver.

_SECTION 2- building the wizardpen driver_

Those instructions can be found elsewhere but i report there as well for sake of simplicity. They are adapted from [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen).


**I. Prepare the install**

**1.** *Create the directory structure*

```

$ mkdir ~/wizardpen
$ cd ~/wizardpen
```**2.** *Add the repository information*

add the following two lines to /etc/apt/sources.list

```

deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu jaunty main
deb-src http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu jaunty main 
```**3.** *Update the repository definition*

```

$ sudo apt-get update
```**4.** *Get the source *

```

apt-get source xserver-xorg-input-wizardpen
```**II. Build the driver**

**1.** *Compile*

```

$ cd xserver-xorg-input-wizardpen-0.7.1
$ ./configure --prefix=/usr
$ make
$ sudo make install
```**2.** *Create a udev rule*

Note- the udev rule creation step may be optional, i'm not sure of that.

Create the file /etc/udev/rules.d/010_tablet.rules and add that line: 

```

KERNEL=="event*",ATTRS{idVendor}=="172f",SYMLINK+="input/tablet"
```If you have multiple Waltop devices you may need to also add the condition ATTRS{idProduct}=="0500" (for the trust tb-7300 model).

**3.** *Create the fdi policy file*

Here's the fdi file i use (/etc/hal/fdi/policy/010_tablet.rules):

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="WALTOP">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```**4.** *(optional) Restart udev and calibrate your tablet*

```

$ sudo service udev restart
$ cd ~/wizardpen/xserver-xorg-input-wizardpen-0.7.1/calibrate 
```Follow the instructions on screen. Forget the xorg.conf instructions and save the info for later use (if any - especially tweaking the fdi policy file if you need to).

**5. *Take some precaution***

Carefully read the *"Making X start without a tablet connected"* on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) (i personally skip that step)

**6.** *Reboot*

Your tablet should be working (mine has at that time).

I hope this might be helpful.

Regards


Edit- thought i could also post my xinput info after successful installation: 

```

$ xinput --list
...
"WALTOP International Corp. Media Tablet"    id=2    [XExtensionPointer]
    Type is WizardPen Tablet
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1680
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 1050
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000
...

```


i tried this but under install preparation step 3 (update) i get an error:
```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 15A579BF113659DF
```

I'm new to ubuntu and i don't know what to do. 

Cheers!

---

### Post by gdodinet on 2009-11-27
Hi Tomankirilov,

This is a warning telling you didn't install the authentication key for the repository you declared. You can add it as shown below. Before you add it, please read the "technical details" on [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen), please also read [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html) which will give you detailed explanation on ppa software installation and authentication. 

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 113659DF

```

The result (for me) is as follows:

```

gilles@GUB:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 113659DF
[sudo] password for gilles: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 113659DF
gpg: requête de la clé 113659DF du serveur hkp keyserver.ubuntu.com
gpg: clé 113659DF: « Launchpad PPA for Martin Owens » n'a pas changé
gpg: Quantité totale traitée: 1
gpg:              inchangée: 1

``` 

I hope this helps. 

Edit- I just edited the post where i detailed the steps i went through to add the authentication key stuff


Regards

---

### Post by Pentarex on 2009-11-28
Hi.... I just wanted to ask you how do you run wizard-calibrate.c and is this the whole fdi? Also why Aiptek 14000u tablet was recognized like keyboard in xinput --list is this depend of the fdi file? 10nx

---

### Post by gdodinet on 2009-11-28
Hi Pentarex,

Did you try to build the wizardpen driver ? If so, then yes, that's the whole fdi file i use. If the tablet is recognized as keyboard, then the device has probably not been registered with the wizardpen driver. 

That said, if you have the Aiptek 14000U tablet (i.e. not branded as Waltop), the fdi file might be a little different. It should probably look like :

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

```

The substring to match can be obtained  using lshal. In lshal output look for your tablet device. You should be able to get the info.product info from there. Here's an excerpt of my lshal output:

```

udi = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0_logicaldev_input'
  ...
  info.product = '**WALTOP** International Corp. Media Tablet'  (string)
  ...

```

---

### Post by adrix89 on 2009-12-01
Seems like it doesn't want to compile on karmic [http://pastebin.com/d1c7e3da7](http://pastebin.com/d1c7e3da7)
Can anybody help me? as both methods I cant seem to get them to compile

---

### Post by gdodinet on 2009-12-02
Hi Adrix, 

I may be wrong but i don't see any error in the output you provided. The message "Nothing to be done for 'all'" generally indicates that the sources have already been compiled (output files exist and they are older than their underlying sources). Are you sure you didn't compile earlier?

Aren't there any .o files generated - for instance wizardopen-calibrate.o in the xserver-xorg-input-wizardpen-0.7.1 folder? 

If output files have been generated then you just need to install the driver using "sudo make install".

Just for info, i paste below the output i get if i run "make" after a successful compilation. You can see that i get the same output as you (or so it seems).

```

gilles@GUB:~/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1$ make
make  all-recursive
make[1]: entrant dans le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1 »
Making all in src
make[2]: entrant dans le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1/src »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1/src »
Making all in man
make[2]: entrant dans le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1/man »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1/man »
make[2]: entrant dans le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1 »
make[2]: quittant le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1 »
make[1]: quittant le répertoire «
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1 »

```

---

### Post by adrix89 on 2009-12-02
Hmm I guess it did compile
Anyways mine is also recognize as an keyboard now
And i checked the lshal and its sees it as a waltop [http://pastebin.com/d4781f67f](http://pastebin.com/d4781f67f)
Not sure what i should do now

---

### Post by gdodinet on 2009-12-02
Indeed the tablet identifies itself as a waltop media tablet, however it has not been registered with the wizardpen driver : line 79 of the output you pasted says "input.x11_driver = 'evdev'  (string)", while it should be "input.x11_driver = 'wizardpen'  (string)"

You should check the xorg logs to see what is happening. Also check that your fdi file is correct.

---

### Post by adrix89 on 2009-12-02
The fdi is correct as it is copy paste from you and is Waltop
I'm not sure about xorg logs? how do I get them?

---

### Post by gdodinet on 2009-12-02
It is located at /var/log/Xorg.0.log. Here's the relevant part i have in my Xorg.0.log: 

```

(II) config/hal: Adding input device WALTOP International Corp. Media Tablet
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.7.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Option "Device" "/dev/input/event5"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) WALTOP International Corp. Media Tablet is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) WALTOP International Corp. Media Tablet: always reports core events
(II) XINPUT: Adding extended input device "WALTOP International Corp. Media Tablet" (type: WizardPen Tablet)
(II) WALTOP International Corp. Media Tablet Increment: 1

```

So here we want to see if the wizardpen module is loading (probably not), if not if an error prevented him to load, or if the tablet device is just registered with another driver.

---

### Post by adrix89 on 2009-12-02
[http://pastebin.com/d466fe1e8](http://pastebin.com/d466fe1e8)

---

### Post by gdodinet on 2009-12-02
Hi Adrix,

I cannot solve the problem for you but i can help you pinpoint the issue - however please note i have myself very little experience with system stuff. 

Now, if i read correctly the traces you posted, xorg logs seem to confirm that the tablet is registered with the evdev driver and that the wizardpen has not been loaded at all, as we guessed. So the question is why. Off the top of my head i can see two possible reasons: (i) the module has not been correctly installed, (ii) the fdi rule has not been correctly read. Let's investigate a bit further. 

(i) Is the driver installed? 

search for wizardpen_drv.so:

```
gilles@GUB:~$ locate wizardpen_drv.so
```

On my system, two entries are returned: 

```
/home/gilles/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1/src/.libs/wizardpen_drv.so
/usr/lib/xorg/modules/input/wizardpen_drv.so
```

The second line confirms us the driver is correctly installed. 

(ii) The driver is correctly installed, good. 

I don't think this could cause problems if the aiptek driver or the wacom are installed, but just to be on the safe side let's make sure those are not installed. 

```
sudo apt-get --purge remove xserver-xorg-input-wacom
sudo apt-get --purge remove xserver-xorg-input-aiptek
```

Now let's make sure the fdi file is correct. Mine is named 99-x11-wizardpen.fdi but whatever the name this should work (or so i think). I repaste the whole content here even though you say you got it right.

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
   <match key="info.product" contains="WALTOP">
     <merge key="input.x11_driver" type="string">wizardpen</merge>
     <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
   </match>
 </device>
</deviceinfo>

```

So far we've made sure that (i) the driver is correctly installed and that no other pieces of software could interfer (hopefully), (ii) the fdi config file is correct. Perhaps should we also check there's no fdi phantom rule that would interfer. Has the wacom fdi file been removed? What about the aiptek one? If there are still present, let's delete them. 

If all validation points succeeded (f.i. there driver was correctly installed, no hal configuration issues were detected), then this means the solution obviously lies elsewhere. Question is: where? I got no clue right now..

if one validation point failed, we want to try and reboot at this point. This still doesn't work? damn.. What didn't we think of? Udev rule? Most probably not, but we could give it a try (tweaking it, removing it, etc.) as this couldn't do much more harm..

---

### Post by adrix89 on 2009-12-03
Made it (I think)
Just had to make a new file in etc/hal/fdi/policy with .fdi instead of .rules and copy that .fdi in usr/share/hal/fdi/policy/ and the 20thirdparty subfolder and delete anything remotely tablety from that folders like the aipiek.fdi
```
"WALTOP International Corp. Media Tablet"    id=13    [XExtensionPointer]
    Type is WizardPen Tablet
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1440
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 900
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000

```Edit:Seems like testing in inkscape and gimp doesnt work
Maybe I have to configure it?
How do you calibrate?

---

### Post by gdodinet on 2009-12-03
Hi Adrix, 

Glad to see we're getting closer. Not sure but i don't think the calibration process is required since it just returns values to allow the user to fine-tune the configuration, and it seems your tablet has been correctly configured. However you could give it a try by executing wzardpen-calibrate from the wizardpen source directory:

```

gilles@GUB:~/Temp/wizardpen/xserver-xorg-input-wizardpen-0.7.1$ sudo wizardpen-calibrate /dev/input/event5

```

From what you pasted [here](http://pastebin.com/d466fe1e8), the device name, in your case, should be /dev/input/event16, i think.

Now concerning gimp, "it doesn't work" is not a valid symptom description. Do you mean you have no pressure sensitivity? You can't paint at all? I guess that you can use your stylus as a pointer (for instance to open documents), and that you have enabled the device in Gimp preferences (in Preferences > Input devices > Configure extended input devices, set the mode of the waltop device to "screen"), right? As for Inkscape, i got no clue, i don't use it. 

You could also try MyPaint as it supports tablets out of the box (no configuration needed) to see how it behaves.

---

### Post by adrix89 on 2009-12-03
Its fairly strange
I got it to work but only activated when i was trying to calibrate it
But trying to work in gimp inkscape my paint
I find that drawing does nothing but move the cursor so I guess no pressure
Also in gimp it says
Device not available: Permission denied in state
but there is at-least some progress
Edit:I found that by double tapping on the tablet it activates as a mouse pointer
So it seems that the problem is it isn't registering pressure

---

### Post by gdodinet on 2009-12-03
Does this mean you can't also double-click a file (for instance)? does it lock the focus for a few seconds? That's the behaviour i observed when no driver were handling the tablet.

Also, it shouldn't be necessary from what i understand, but did you add a udev rule? And do you get some garbage when you cat the device file (without running the calibration tool first)?

```

sudo cat /dev/input/event16
sudo cat /dev/input/tablet #where /dev/input/tablet matches your udev rule if you have one
```

Also worth mentionning, someone encountered a similar issue (Device not available) with the linuxwacom driver - sometime ago. See the original message  [here](http://old.nabble.com/WACOM---Bamboo-one-and-Gimp---pressure-sensitive-drawing-does-not-work---Device-not-available:-Permission-denied-tc16886490r1.html). I know it got no answers but it would be worth trying to start Gimp as root to see what happens.

---

### Post by adrix89 on 2009-12-04
It was my mistake I don't have to calibrate it
I just have to double tap it whit pen to activate
It seems to recognize it if I go in sudo with gimp
And i don't have a udev rule yet but will try to make one
Also the problem is that I have no pressure sensitivity so it works like a mouse where I have to click(first button on pen) to draw
Does the wizarpen fdi have a part where you can set pen pressure?

---

### Post by adrix89 on 2009-12-04
Question
You said > **3.** *Create the fdi policy file*

Here's the fdi file i use (/etc/hal/fdi/policy/010_tablet.rules):

     Code:
     <?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="WALTOP">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo> 
But then said you use 99-x11-wizardpen.fdi
So which is it?and what files go where
Because by itself the 010_tablet.rules don't work and recognize it as keyboard
Edit:Seems that it only recognize it if i cahnge 010_tablet.rules to 010_tablet.fdi no 99-x11-wizardpen.fdi
Also can you put your lshal where it shows which driver you have? like this [http://pastebin.com/db34870a](http://pastebin.com/db34870a)
Also how do you configure the xorg so as to change the pressure sensitivity?

---

### Post by gdodinet on 2009-12-04
Hi Adrix,

First, concerning the rules file, it is my mistake : 010_tablet.rules is the name of my udev rule, the fdi rule file is indeed named 99-x11-wizardpen.fdi, as you can see below. Sorry about that, i'll update the previous post. 

```

gilles@GUB:~$ more /etc/udev/rules.d/010_tablet.rules 
KERNEL=="event*",ATTRS{idVendor}=="172f",SYMLINK+="input/tablet"

gilles@GUB:~$ more /etc/hal/fdi/policy/99-x11-wizardpen.fdi 
<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
 <match key="info.product" contains="WALTOP">
 <merge key="input.x11_driver" type="string">wizardpen</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
 </match>
 </device>
</deviceinfo>

```

Reading [url=http://ubuntuforums.org/showpost.php?p=7279044&postcount=11
]this post[/url], it seems you can configure the sensitivity in the fdi (you don't have to touch anything in xorg.conf, all magic is handled by hal) :

[quote=practic]
Some people gained touch sensitivity by adding the following lines into the middle of the file:

<merge key="input.x11_options.topZ" type="string">5</merge>
<merge key="input.x11_options.bottomZ" type="string">511</merge>
<merge key="input.x11_options.maxZ" type="string">511</merge>
[/quote]

Also below is the relevant part of the lshal output: 

```

udi = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0'  (string)
  info.product = 'WALTOP International Corp. Media Tablet'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_500_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Media Tablet'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.xkb.layout = 'fr'  (string)
  input.xkb.model = 'dell'  (string)
  input.xkb.options = 'grp:alts_toggle,eurosign:e'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input5/event5'  (string)

```

I hope you're gonna solve your issue.

---

### Post by adrix89 on 2009-12-06
It seems until the driver issue is resolved 14000u will not work with pressure
On  a side note I managed to compile the wacom but it recognize it as a wacom keyboard

---

### Post by manovotny on 2009-12-10
Today I followed gdodinet's steps and successfully compiled wizardpen 0.7.1 and my  tablet Genius G-Pen M712 works as expected.

Great work, gdodinet!

---

### Post by adrix89 on 2009-12-14
I'm an IDDDDDIIIIOOOT
Seems like the tablet works fine(atleast in mypaint)
The problem is that I wasn't literally putting any pressure on the pen
Seems lie I'm not very used to tablets
So it works
Aiptek(/Waltop) 14000u Media tablet with wizard-pen driver works!

---

### Post by rohtie on 2009-12-18
I tried [gdodinet]("http://ubuntuforums.org/member.php?u=427326")'s way. Though the wizardpen repository seems to be down...

---

### Post by wKLV on 2010-01-02
Hi, I've got an aiptek 1000u. I tried wizardpen driver, because wacom 0.8.4 hang up my computer, and this recognized pressure, but no stylus buttons, or side keys. I've tried again wacom driver, but this time the 0.8.7.9-11, with Favux fdi and the patched wcmUSB.c. This recognizes the stylus and a eraser, but no pad or cursor. This still doesn't move the cursor, neither recognizes pressure. When I tried xiidump, it gets no signal. Any idea why?  I upload an extract of the lshal

---

### Post by RED666 on 2010-03-23
Hi I have an Aiptek14000U run on Ubuntu 9.10 Karmic 32 bits , x86 platform. I tried the solution by [gdodinet]("http://ubuntuforums.org/member.php?u=427326") in post   #[**35**]("http://ubuntuforums.org/showpost.php?p=8311575&postcount=35") and #38 (if you have 32bits Ubuntu  like me look at #38 first).

It works!! Up to a point I can't change any settings and the scroll wheels / macro keys don't work. But at least I can draw now.... great stuff.

---

### Post by lospo on 2010-05-21
Why everything is so difficoult?!?!?!

Can someone help me with this?

```

$ sudo ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
**configure: error: cannot run /bin/bash ./config.sub**


```

Ah, my ubuntubox is a fresh install

Many thanks!

---

### Post by gdodinet on 2010-06-30
Hi, Lopso! 

Late reply, just in case you still have problems - i just upgraded to Lucid. Did you upgrade to Lucid, or are you still trying to make it work under karmic? I had the exact same error trying to build from source with owen's lucid repository. However it seems there's now no need to build it from source. Just installing the binary package and tweaking the configuration seems to be enough. Let us know if you still got troubles.

---

