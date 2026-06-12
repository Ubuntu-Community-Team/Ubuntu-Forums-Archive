---
title: "Touchpad right click stopped working monday evening"
date: 2019-11-05
forum: Hardware
---

### Post by Jan_Johansson on 2019-11-05
I have Peach OSI Xubuntu 16.04 LTS 4.4.0-166-generic 64bit


 A few days ago the right click Touchpad mouse button, on my Lenovo Thinkpad  X300, worked fine - since monday evening it has not worked at all.


 Luckily both Touchpoint buttons and external mouse works. 

I booted my  USB with multi tools including Peach OSI 14.04 LTS 32bit to see if  problem persists and it does, so either firmware of the buttons got  corrupted, or the right mouse button suddently died.

This happened directly after receiving updates.

Can someone look at this and tell what to try next, before I have to think about HW replacement?

 
Tried so far:

user@machine:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick           	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (17ef:4807)                  	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=16	[slave  keyboard (3)]


              
                 [TABLE]
                [TR]
           [TD]             
[/TD]
[TD="class: bug-comment-index"][/TD]
[/TR]
[/TABLE]

user@machine:~$ xinput --list-props 14
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
 Device Enabled (136):	1
 Coordinate Transformation Matrix (138):	1.000000, 0.000000, 0.000000,  0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
 Device Accel Profile (265):	1
 Device Accel Constant Deceleration (266):	2.500000
 Device Accel Adaptive Deceleration (267):	1.000000
 Device Accel Velocity Scaling (268):	12.500000
 Synaptics Edges (290):	153, 870, 115, 652
 Synaptics Finger (291):	12, 15, 0
 Synaptics Tap Time (292):	180
 Synaptics Tap Move (293):	56
 Synaptics Tap Durations (294):	180, 100, 100
 Synaptics ClickPad (295):	0
 Synaptics Middle Button Timeout (296):	75
 Synaptics Two-Finger Pressure (297):	141
 Synaptics Two-Finger Width (298):	7
 Synaptics Scrolling Distance (299):	25, 25
 Synaptics Edge Scrolling (300):	1, 0, 0
 Synaptics Two-Finger Scrolling (301):	0, 0
 Synaptics Move Speed (302):	1.000000, 1.750000, 0.156495, 0.000000
 Synaptics Off (303):	0
 Synaptics Locked Drags (304):	0
 Synaptics Locked Drags Timeout (305):	5000
 Synaptics Tap Action (306):	2, 3, 0, 0, 0, 0, 0
 Synaptics Click Action (307):	1, 1, 0
 Synaptics Circular Scrolling (308):	0
 Synaptics Circular Scrolling Distance (309):	0.100000
 Synaptics Circular Scrolling Trigger (310):	0
 Synaptics Circular Pad (311):	0
 Synaptics Palm Detection (312):	0
 Synaptics Palm Dimensions (313):	10, 100
 Synaptics Coasting Speed (314):	20.000000, 50.000000
 Synaptics Pressure Motion (315):	15, 80
 Synaptics Pressure Motion Factor (316):	1.000000, 1.000000
 Synaptics Resolution Detect (317):	1
 Synaptics Grab Event Device (318):	0
 Synaptics Gestures (319):	1
 Synaptics Capabilities (320):	1, 1, 1, 0, 0, 1, 0
 Synaptics Pad Resolution (321):	1, 1
 Synaptics Area (322):	0, 0, 0, 0
 Synaptics Noise Cancellation (323):	6, 6
 Device Product ID (256):	2, 8
 Device Node (257):	"/dev/input/event6"

 
user@machine:~$ xinput --list-props 15
Device 'AlpsPS/2 ALPS DualPoint Stick':
 Device Enabled (136):	1
 Coordinate Transformation Matrix (138):	1.000000, 0.000000, 0.000000,  0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
 Device Accel Profile (265):	0
 Device Accel Constant Deceleration (266):	1.000000
 Device Accel Adaptive Deceleration (267):	1.000000
 Device Accel Velocity Scaling (268):	10.000000
 Device Product ID (256):	2, 8
 Device Node (257):	"/dev/input/event5"
 Evdev Axis Inversion (269):	0, 0
 Evdev Axes Swap (271):	0
 Axis Labels (272):	"Rel X" (146), "Rel Y" (147)
 Button Labels (273):	"Button Left" (139), "Button Middle" (140),  "Button Right" (141), "Button Wheel Up" (142), "Button Wheel Down"  (143), "Button Horiz Wheel Left" (144), "Button Horiz Wheel Right" (145)
 Evdev Scrolling Distance (274):	0, 0, 0
 Evdev Middle Button Emulation (275):	1
 Evdev Middle Button Timeout (276):	50
 Evdev Third Button Emulation (277):	0
 Evdev Third Button Emulation Timeout (278):	1000
 Evdev Third Button Emulation Button (279):	3
 Evdev Third Button Emulation Threshold (280):	20
 Evdev Wheel Emulation (281):	1
 Evdev Wheel Emulation Axes (282):	6, 7, 4, 5
 Evdev Wheel Emulation Inertia (283):	10
 Evdev Wheel Emulation Timeout (284):	200
 Evdev Wheel Emulation Button (285):	2
 Evdev Drag Lock Buttons (286):	0


              
        
         [TABLE]
                [TR]
           [TD]             
[/TD]
[TD="class: bug-comment-index"][/TD]
[/TR]
[/TABLE]

user@machine:~$ grep -i touchpad /var/log/Xorg.0.log
[    15.043] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event6)
[    15.043] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.043] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    15.043] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    15.045] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    15.045] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    15.116] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    15.116] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    15.116] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    15.168] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 14)
[    15.168] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    15.168] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    15.168] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    15.168] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    15.168] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    15.169] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    15.169] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    15.169] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    15.170] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[    15.170] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

 
user@machine:~$ lsmod
Module                  Size  Used by
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   184320  0
xfs                   974848  0
libcrc32c              16384  1 xfs
rfcomm                 69632  14
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
arc4                   16384  2
coretemp               16384  0
kvm_intel             176128  0
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    77824  1 snd_hda_codec_analog
kvm                   552960  1 kvm_intel
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
iwl4965               114688  0
videobuf2_memops       16384  1 videobuf2_vmalloc
irqbypass              16384  1 kvm
videobuf2_v4l2         28672  1 uvcvideo
iwlegacy              102400  1 iwl4965
snd_seq_midi           16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
snd_seq_midi_event     16384  1 snd_seq_midi
mac80211              737280  2 iwl4965,iwlegacy
serio_raw              16384  0
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_intel          40960  3
snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog
thinkpad_acpi          94208  0
nvram                  16384  1 thinkpad_acpi
snd_hda_core           77824  4 snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog
snd_hwdep              16384  1 snd_hda_codec
lpc_ich                24576  0
cfg80211              565248  3 iwl4965,iwlegacy,mac80211
joydev                 20480  0
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
btusb                  45056  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             512000  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel
input_leds             16384  0
shpchp                 36864  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
ecdh_generic           24576  1 bluetooth
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  17 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_hda_codec_analog
soundcore              16384  1 snd
mac_hid                16384  0
binfmt_misc            20480  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
btrfs                 999424  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
i915                 1236992  5
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
psmouse               131072  0
ahci                   40960  2
syscopyarea            16384  1 drm_kms_helper
libahci                32768  1 ahci
pata_acpi              16384  0
sysfillrect            16384  1 drm_kms_helper
e1000e                241664  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
fjes                   28672  0
video                  40960  2 i915,thinkpad_acpi

---

### Post by Autodave on 2019-11-06
I would boot the machine from a 16.04 or 18.04 install medium and use the "Try ?buntu" option.  Does the button work then?  If not, I would say that you have a HW problem.

---

### Post by Jan_Johansson on 2019-11-06
Thank you for the response, the reason or booting from 14.04 LTS 32bit is that if anything were affecting the 64bit 16.04 it would nt not affect this one - and the problem did persist - Since there has been alot of problems regarding mouse,touchpad,trackpad,clickpad since new kernel of 16.04 and 18.04  came out, my suspicion were that something could have affected the firmware for the touchpad buttons - or it could be hardware.

Searching this forum there are alot of repports of right click stop working, but no solution - I don't accept workarounds as solution.

If firmware, then it would follow though using different distro, whether windows or linux - because in the chip of the mouse - right? 

If HW then I need to change the buttons - that not going to be fun(took long time to find and long time to do on my R500, because you have to be extra careful) - but before I rule HW, I need to be sure its not one of the updates that cause this.

Jan

---

