---
title: "quickcam: YAWT (yet another webcam thread)"
date: 2008-08-11
forum: General Help
---

### Post by tlacuache on 2008-08-11
I'm trying to get a logitech webcam working, model V-UK11, in 8.04.

Here's my system info:

```
Linux tlacuache-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

dmesg when plugging in camera:
```
[ 2662.281383] usb 1-8: new full speed USB device using ohci_hcd and address 3
[ 2662.493823] usb 1-8: configuration #1 chosen from 1 choice
[ 2662.671545] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[ 2662.671552] quickcam: Kernel:2.6.24-19-generic bus:1 class:FF subclass:FF vendor:046D product:0850
[ 2662.712703] quickcam: Sensor VV6410 detected
[ 2662.718729] quickcam: Registered device: /dev/video1
[ 2662.718761] usbcore: registered new interface driver quickcam
[ 2662.797984] usbcore: registered new interface driver snd-usb-audio
```

lsmod after plugging in camera:
```
Module                  Size  Used by
snd_usb_audio          83936  1 
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
quickcam               73636  0 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
vboxdrv                77632  0 
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
lmpcm_usb               7168  0 
usblp                  15872  0 
nvidia               7825536  34 
agpgart                34760  1 nvidia
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
bt878                  11832  0 
snd_seq_oss            35584  0 
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
snd_seq_midi            9376  0 
bttv                  175860  1 bt878
analog                 13600  0 
ir_common              36100  1 bttv
snd_rawmidi            25760  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
evdev                  13056  3 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7300  1 bttv
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
gameport               16008  1 analog
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videobuf_dma_sg        14980  1 bttv
videobuf_core          18820  2 bttv,videobuf_dma_sg
btcx_risc               5896  1 bttv
tveeprom               16656  1 bttv
videodev               29440  2 quickcam,bttv
v4l2_common            18304  2 bttv,videodev
v4l1_compat            15492  2 bttv,videodev
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  24 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34452  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_nforce2             7680  0 
k8temp                  6656  0 
pcspkr                  4224  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  5 nvidia,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
pata_acpi               8320  0 
ata_generic             8324  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
floppy                 59588  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
sata_nv                27528  0 
pata_amd               14212  3 
forcedeth              51980  0 
libata                159344  4 pata_acpi,ata_generic,sata_nv,pata_amd
ehci_hcd               37900  0 
ohci_hcd               25348  0 
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
usbcore               146028  11 snd_usb_audio,snd_usb_lib,quickcam,lmpcm_usb,usblp,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  3 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```

lsusb for device:
```
Bus 001 Device 003: ID 046d:0850 Logitech, Inc. QuickCam Web
```

results from qcset (read about it on google, thought I'd run it to see if it gives me any useful info:
```
$ qcset /dev/video1 -i

Name          : Logitech QuickCam USB
Type          : capture subcapture 
Channels      : 1
Audio devices : 0
Maxsize       : 356,292
Minsize       : 32,32

Overlay coords: 0,0
Capture size  : 356,292
Chromakey     : 0
Flags         : 

Channel       : 0
Name          : Camera
Tuners        : 0
Flags         : 
Type          : camera
Norm          : 47087

Brightness    : 32768
Hue           : 32768
Color         : 32768
Contrast      : 32768
Whiteness     : 32768
Depth         : 24
Palette       : RGB888 packed into 24bit words.
```

So as far as I can see when I plug it in the camera and the built-in microphone are recognized and modules are loaded. However, whenever I try to use the camera (in skype, ekiga, camorama, cheese, whatever), the light on the camera blinks and the app freezes. Then dmesg gives me this:
```
[  185.322273] ohci_hcd 0000:00:02.0: leak ed f7fc70c0 (#81) state 2
[  235.824254] quickcam: Control URB error -2
[  235.826890] BUG: unable to handle kernel paging request at virtual address 7542445f
[  235.826894] printing eip: f889bd3a *pde = 00000000 
[  235.826898] Oops: 0000 [#1] SMP 
[  235.826901] Modules linked in: snd_usb_audio snd_usb_lib snd_hwdep quickcam binfmt_misc rfcomm l2cap bluetooth vboxdrv ppdev cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative container sbs sbshc dock video output battery iptable_filter ip_tables x_tables ac sbp2 lp lmpcm_usb usblp nvidia(P) agpgart snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_mpu401 snd_mpu401_uart snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi bt878 snd_seq_midi_event bttv snd_seq ir_common snd_timer snd_seq_device compat_ioctl32 i2c_algo_bit videobuf_dma_sg videobuf_core btcx_risc tveeprom videodev v4l2_common v4l1_compat snd button i2c_nforce2 k8temp parport_pc parport analog soundcore snd_page_alloc i2c_core shpchp pci_hotplug evdev gameport pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_generic usbhid hid usb_storage libusual floppy ohci1394 ieee1394 sata_nv pata_amd forcedeth libata ehci_hcd ohci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  235.826942] 
[  235.826945] Pid: 6655, comm: ekiga Tainted: P        (2.6.24-19-generic #1)
[  235.826947] EIP: 0060:[<f889bd3a>] EFLAGS: 00210202 CPU: 0
[  235.826971] EIP is at usb_hcd_unlink_urb+0xa/0x30 [usbcore]
[  235.826974] EAX: 7542442f EBX: f5fe2400 ECX: fffffffe EDX: f5fe2400
[  235.826976] ESI: f67b79c0 EDI: f5873ee0 EBP: f5f88588 ESP: f5401dd4
[  235.826978]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  235.826980] Process ekiga (pid: 6655, ti=f5400000 task=f5d61140 task.ti=f5400000)
[  235.826981] Stack: f5fe2400 f889bf1e 00000000 00001388 f5d55400 f5fc8000 f67b79c0 f5fc8000 
[  235.826986]        f67b79c0 f8d0e0a0 f5f886a4 00000008 f5fc8000 f8d10247 00000008 c0192c87 
[  235.826990]        00000000 00000000 f5873ee0 df893780 f5f88588 f67b79c0 f5fa2180 00000000 
[  235.826994] Call Trace:
[  235.827003]  [<f889bf1e>] usb_kill_urb+0x4e/0xd0 [usbcore]
[  235.827040]  [<f8d0e0a0>] qc_isoc_stop+0x30/0x100 [quickcam]
[  235.827056]  [<f8d10247>] qc_v4l_close+0x77/0xb0 [quickcam]
[  235.827065]  [<c0192c87>] __fput+0xa7/0x190
[  235.827097]  [<c018fc19>] filp_close+0x49/0x80
[  235.827112]  [<c012ea92>] put_files_struct+0x92/0xb0
[  235.827131]  [<c012fd90>] do_exit+0x180/0x860
[  235.827136]  [<c018fca2>] get_unused_fd_flags+0x52/0xd0
[  235.827154]  [<c01375cb>] recalc_sigpending+0xb/0x40
[  235.827157]  [<c0138a2b>] dequeue_signal+0x6b/0x150
[  235.827175]  [<c0130496>] do_group_exit+0x26/0x80
[  235.827186]  [<c0138f67>] get_signal_to_deliver+0x2b7/0x4a0
[  235.827189]  [<c029e1b5>] sys_sendto+0x175/0x180
[  235.827222]  [<c0103903>] do_notify_resume+0x93/0x750
[  235.827231]  [<c02aabe2>] dev_ioctl+0x292/0x500
[  235.827252]  [<c01b5e7e>] invalidate_inode_buffers+0xe/0xc0
[  235.827327]  [<c021adc0>] copy_to_user+0x30/0x60
[  235.827339]  [<c019f9f4>] sys_select+0x194/0x1c0
[  235.827380]  [<c010451e>] work_notifysig+0x13/0x25
[  235.827435]  =======================
[  235.827436] Code: 2d ca 97 c7 e9 5a fe ff ff c7 44 24 34 00 00 00 00 e9 bf fe ff ff 8d 74 26 00 8d bc 27 00 00 00 00 53 89 c3 8b 40 28 89 d1 89 da <8b> 40 30 e8 be eb ff ff 85 c0 74 02 5b c3 5b b8 8d ff ff ff 66 
[  235.827453] EIP: [<f889bd3a>] usb_hcd_unlink_urb+0xa/0x30 [usbcore] SS:ESP 0068:f5401dd4
[  235.827475] ---[ end trace 029c6dbfb32f56bc ]---
[  235.827477] Fixing recursive fault but reboot is needed!

```

Craptastic, eh? I'm still trying to google around, but I thought maybe if one of you had seen something similar and had some tips it might save me some time.

Thanks much,

-SG

---

### Post by tlacuache on 2008-08-12
Replying to my own post...

After fiddling around with it some more last night, I determined that if I unplugged ALL other USB devices from my computer, the webcam would work fine.

On a whim, I plugged the webcam into my laptop instead. Worked perfectly from the get-go, and all my other USB devices still worked fine as well. No problems whatsoever.

So... I guess the problem lies in my desktop's USB bus? I'm sort of scratching my head, since both machines are running Ubuntu 8.04.

I can't imagine there's really anything else I can do about it, but if anyone has any insight I'd love to hear it. Thanks.

-SG

---

