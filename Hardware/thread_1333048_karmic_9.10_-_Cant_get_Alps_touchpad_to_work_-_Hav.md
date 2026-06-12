---
title: "karmic 9.10 - Cant get Alps touchpad to work - Have tried many things"
date: 2009-11-21
forum: Hardware
---

### Post by marcopl on 2009-11-21
Guys,

i have a compaq presario c40 laptop with an alps touchpad. i just cant get the touchpad to work???

- it works with pclinux
- didnt work in kubuntu - tried many things...

- then switched to ubuntu karmic 9.10
- tried many things such as;

-- creating fdi files ( frm site [http://www.bhagwad.com/blog/2009/technology/configure-alps-synaptics-touchpad-in-ubuntu-904-jaunty-jackalope.html](http://www.bhagwad.com/blog/2009/technology/configure-alps-synaptics-touchpad-in-ubuntu-904-jaunty-jackalope.html) )
-- editing grub to add kernel options i8042.nomux
-- editing /etc/modules to load psmouse i8042.nomux=1

Pls pls pls pls help.  :icon_frown::frown:

---

### Post by kruzztee on 2009-11-21
Same here... tried so many things since Jaunty...
Can you share me what notebook did you use? I use Indonesia's Zyrex Bee...
The touchpad detected as Alps in Windows.

Did ubuntu abandon us?:confused::confused:

---

### Post by marcopl on 2009-11-22
> **kruzztee said:**
> Same here... tried so many things since Jaunty...
Can you share me what notebook did you use? I use Indonesia's Zyrex Bee...
The touchpad detected as Alps in Windows.

Did ubuntu abandon us?:confused::confused:

a compaq presario c40 laptop

---

### Post by marcopl on 2009-11-22
apparently, i have the i8042 controller as shown by lshal;

~$ sudo lshal | grep i8042
  info.linux.driver = 'i8042 aux'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input9/event9'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input10/event10'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input5/event5'  (string)

---

### Post by marcopl on 2009-11-22
lshal also shows my touchpad as an alps touchpad;

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.EmulateMidButtonTime = '75'  (string)
  input.x11_options.TouchpadOff = '0'  (string)
  input.x11_options.xCenterDenominator = '1'  (string)
  input.x11_options.xCenterNumerator = '1'  (string)
  input.x11_options.xEdgeDenominator = '1'  (string)
  input.x11_options.xEdgeNumerator = '1'  (string)
  input.x11_options.xJump = '16'  (string)
  input.x11_options.xPadMax = '840'  (string)
  input.x11_options.xPadMin = '130'  (string)
  input.x11_options.yCenterDenominator = '1'  (string)
  input.x11_options.yCenterNumerator = '1'  (string)
  input.x11_options.yEdgeDenominator = '1'  (string)
  input.x11_options.yEdgeNumerator = '1'  (string)
  input.x11_options.yJump = '16'  (string)
  input.x11_options.yPadMax = '640'  (string)
  input.x11_options.yPadMin = '130'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input10/event10'  (string)

---

### Post by marcopl on 2009-11-22
lshal does list the 'synaptics' as the driver but thru 'lsmod' i cant see any 'synaptics' driver.

lsmod output shown below;

techiee@compaq-laptop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
joydev                 10272  0 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
uvcvideo               59080  0 
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lirc_ene0100            8096  0 
snd                    59204  21 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
soundcore               7264  1 snd
lirc_dev               10804  1 lirc_ene0100
iptable_filter          3100  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
v4l1_compat            14496  2 uvcvideo,videodev
ip_tables              11692  1 iptable_filter
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  1 sdhci
psmouse                56180  0 
lib80211_crypt_tkip     8636  0 
serio_raw               5280  0 
x_tables               16544  1 ip_tables
wl                   1272936  0 
jmb38x_ms               9600  0 
memstick               10072  1 jmb38x_ms
lp                      8964  0 
btusb                  11856  2 
lib80211                6432  2 lib80211_crypt_tkip,wl
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by marcopl on 2009-11-24
so i have to get synaptics driver loaded automatically?hmm..


also i noticed this thread abt  people with touchpad problems...
[http://ubuntuforums.org/showthread.php?t=1098767](http://ubuntuforums.org/showthread.php?t=1098767)

---

### Post by marcopl on 2009-11-24
~$ locate synaptic

/lib/modules/2.6.31-14-generic/kernel/drivers/input/mouse/synaptics_i2c.ko
/usr/lib/xorg/modules/input/synaptics_drv.so
/usr/sbin/synaptic

and;

:/usr/lib/xorg/modules/input$ ls -l
total 264
-rw-r--r-- 1 root root  36488 2009-10-26 18:13 evdev_drv.so
-rw-r--r-- 1 root root  48308 2009-04-30 05:09 mouse_drv.so
-rw-r--r-- 1 root root  50908 2009-06-18 04:35 synaptics_drv.so
-rw-r--r-- 1 root root  18284 2009-10-26 18:29 vmmouse_drv.so
-rw-r--r-- 1 root root 100712 2009-10-15 07:05 wacom_drv.so

and apparently to load modules upon boot , u append an entry to the /etc/modules file....so should i append synaptic or synaptic_drv.so? or synaptics_i2c.ko?

hmm... going with synaptics-i2c as its a kernel module

---

### Post by marcopl on 2009-11-24
ok. i got the module loaded with the steps above but still no touchpad...

~$ sudo lsmod

Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
usbhid                 38208  0 
uvcvideo               59080  0 
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
synaptics_i2c           6280  0 
sdhci_pci               7100  0 
psmouse                56500  0 

but nothing seems to be using synaptics_i2c

---

