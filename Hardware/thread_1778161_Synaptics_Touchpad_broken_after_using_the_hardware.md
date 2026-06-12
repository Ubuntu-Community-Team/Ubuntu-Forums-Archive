---
title: "Synaptics Touchpad broken after using the hardware touchpad off button"
date: 2011-06-08
forum: Hardware
---

### Post by zachlr1 on 2011-06-08
Hello,

I am trying to fix a problem with my Synaptics Touchpad on my HP dv9000 running Ubuntu 10.10.  A while ago, I accidentally pressed the hardware touchpad on/off toggle button which turned off the touchpad.  After pressing the switch again to re-enable the touchpad, the mouse pointer was acting slow and choppy.  I decided to reboot the PC in hopes of correcting the problem.  

After rebooting, the touchpad did not work at all.  After a while, I finally got it to work with limited functionality by editing the  /etc/modprobe.d/touchpad.conf file.  The pointer now moves, but the pointer speed is way off, the scrolling is not normal, tap to click is enabled, and when typing the slightest touch will click the mouse.  System > Preferences > Mouse has no Touchpad options tab, either, and Mouse settings do not seem to have an effect on the touchpad.  

After searching around for a while, I came across a  couple of different fixes to try.  I installed gpointing-device-settings, but it did not have any relevant options.  I also tried installing and using tpconfig, which presented the error "Could not open PS/2 Port [/dev/psaux]."   synclient gives the error "Couldn't find synaptics properties. No synaptics driver loaded?"  syndaemon gives the error "Unable to find a synaptics device."

$ xinput list[INDENT]&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Synaptics TouchPad                   id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]

[/INDENT]cat /proc/bus/input/devices[INDENT](excerpt)
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

[/INDENT]tried "gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true" with no errors.

Xorg log > [http://pastebin.com/hMZcwMMD](http://pastebin.com/hMZcwMMD)

lsmod[INDENT]Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
nfsd                  240992  11 
lockd                  65605  1 nfsd
nfs_acl                 2257  1 nfsd
auth_rpcgss            34001  1 nfsd
sunrpc                193178  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3449  1 nfsd
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  143 
snd_hda_codec_si3054     3440  1 
arc4                    1165  2 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  4 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
iwlagn                178948  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
iwlcore               127415  1 iwlagn
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  2 iwlagn,iwlcore
video                  18712  0 
output                  1883  1 video
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49038  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144694  3 iwlagn,iwlcore,mac80211
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
btusb                  10969  0 
mtd                    18877  2 sm_common,nand
bluetooth              50500  1 btusb
joydev                  8767  0 
psmouse                59033  0 
intel_agp              26566  0 
lp                      7342  0 
serio_raw               4022  0 
hp_wmi                  5223  0 
agpgart                32011  2 nvidia,intel_agp
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40204  1 
r8169                  36521  0 
firewire_ohci          21234  0 
sdhci_pci               6633  0 
ahci                   19198  3 
mii                     4425  1 r8169
sdhci                  15922  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
libahci                21728  1 ahci

[/INDENT]modprobe -l |grep mouse
[INDENT] kernel/drivers/usb/misc/idmouse.ko
kernel/drivers/input/mouse/appletouch.ko
kernel/drivers/input/mouse/bcm5974.ko
kernel/drivers/input/mouse/gpio_mouse.ko
kernel/drivers/input/mouse/inport.ko
kernel/drivers/input/mouse/logibm.ko
kernel/drivers/input/mouse/pc110pad.ko
kernel/drivers/input/mouse/psmouse.ko
kernel/drivers/input/mouse/sermouse.ko
kernel/drivers/input/mouse/synaptics_i2c.ko
kernel/drivers/input/mouse/vsxxxaa.ko
kernel/drivers/hid/hid-magicmouse.ko
[/INDENT] 

I'm relatively new to linux, but I get the feeling that the driver is not loaded, and/or that a generic touchpad driver is being used in place of the proper Synaptics driver.  

It took a fraction of a second to press that button, and suddenly I'm three hours into fixing this problem.  It might as well be a self destruct button, and there is a bug that needs to be fixed.  If you have any ideas, please share.  I desperately need to get this issue corrected.  Thanks!

---

### Post by zachlr1 on 2011-06-10
I found a few more commands to try and posted the results below.

grep -im 1 touchpad /var/log/kern.log[INDENT]Jun  7 13:18:11 zach-pc kernel: [370926.990923] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
[/INDENT]grep -i touchpad /var/log/Xorg.0.log[INDENT][    35.101] (II) config/udev: Adding input device ImPS/2 Synaptics TouchPad (/dev/input/event8)
[    35.101] (**) ImPS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
[    35.101] (**) ImPS/2 Synaptics TouchPad: always reports core events
[    35.101] (**) ImPS/2 Synaptics TouchPad: Device: "/dev/input/event8"
[    35.117] (II) ImPS/2 Synaptics TouchPad: Found 3 mouse buttons
[    35.117] (II) ImPS/2 Synaptics TouchPad: Found scroll wheel(s)
[    35.117] (II) ImPS/2 Synaptics TouchPad: Found relative axes
[    35.117] (II) ImPS/2 Synaptics TouchPad: Found x and y relative axes
[    35.117] (II) ImPS/2 Synaptics TouchPad: Configuring as mouse
[    35.117] (**) ImPS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    35.117] (**) ImPS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.117] (II) XINPUT: Adding extended input device "ImPS/2 Synaptics TouchPad" (type: MOUSE)
[    35.117] (II) ImPS/2 Synaptics TouchPad: initialized for relative axes.
[    35.117] (II) config/udev: Adding input device ImPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  5787.428] (II) ImPS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[ 13449.496] (II) ImPS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[ 17499.277] (II) ImPS/2 Synaptics TouchPad: Device reopened after 1 attempts.


[/INDENT]grep -iA 3 'module synaptics' /var/log/Xorg.0.log[INDENT](no output)
[/INDENT]

---

### Post by zachlr1 on 2011-06-12
I have upgraded the distribution to 11.04, but the problem persists.  Now running 11.04, and any help would be greatly appreciated.

---

