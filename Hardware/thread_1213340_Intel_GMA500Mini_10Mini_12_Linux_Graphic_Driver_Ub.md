---
title: "Intel GMA500/Mini 10/Mini 12 Linux Graphic Driver Ubuntu PPA archive"
date: 2009-07-14
forum: Hardware
---

### Post by cloudjy on 2009-07-14
Hi

I've seen many people have complains about cannot find Intel GMA500 Linux Graphic Driver or the Driver Source is outdated. It looks like they are available for Jaunty and Intrepid from Ubuntu PPA Archive site. ( [https://launchpad.net/~ubuntu-mobile/+archive/ppa](https://launchpad.net/~ubuntu-mobile/+archive/ppa) )

It looks like you will need all these packages:

# psb-kernel-src
# libdrm
# libva
# psb-firmware
# xorg-xserver-video-psb
# xpsb
# libgl1-mesa-dri-psb

Good luck.

---

### Post by glauco.b on 2009-07-14
it worked for me installing the poulsbo-driver-3d meta package from the ppa repository

it resolves all the needed dependencies

---

### Post by BlackFoXX on 2009-07-19
Hi glauco.b,
which kernel-version do you use?
I've tried instaling it on the MSI Wind U115, but i get a seg fault when loading the "psb"-module.
Thanks in advance.
Greetz,

BlackFoXX

EDIT: 
backtrace of the SegFault:
```
Linux agpgart interface v0.103
[drm] Initialized drm 1.1.0 20060810
psb 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
psb 0000:00:02.0: setting latency timer to 64
[drm] psb - 5.0.1.0046
[drm:psb_do_init] *ERROR* Debug is 0x00000000
psb 0000:00:02.0: firmware: requesting msvdx_fw.bin
[drm] SGX core id = 0x01130000
[drm] SGX core rev major = 0x01, minor = 0x02
[drm] SGX core rev maintenance = 0x01, designer = 0x00
[drm] intel_lvds_init: OpRegion has the VBT address
[drm] intel_lvds_init: The bdb->signature is BIOS_DATA_BLOCK ƒ, the bdb_off is 48
[drm] intel_lvds_init: BLC Data in BIOS VBT tables: datasize=0 paneltype=7 ^I^I^I^I^I^I^I^Itype=0x00 pol=0x01 freq=0x00c8 minlevel=0x00    ^I^I^I^I^I^I^I^Ii2caddr=0x58 cmd=0xaa 
[drm] intel_lvds_init: the CoreClock is 200
[drm] intel_lvds_init: sku_value is 0x00800000
[drm] intel_lvds_init: sku_bMaxResEnableInt is 0
integrated sync not supported
BUG: unable to handle kernel NULL pointer dereference at 00000000
IP: [<f8059389>] drm_mode_probed_add+0x9/0x20 [drm]
*pde = 00000000 
Oops: 0002 [#1] SMP 
last sysfs file: /sys/devices/pci0000:00/0000:00:02.0/firmware/0000:00:02.0/loading
Dumping ftrace buffer:
   (ftrace buffer empty)
Modules linked in: psb(+) drm agpgart i2c_algo_bit usbhid binfmt_misc ppdev bridge stp bnep input_polldev joydev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi psmouse serio_raw pcspkr snd_rawmidi snd_seq_midi_event snd_seq i2c_isch snd_timer snd_seq_device rt2860sta snd soundcore snd_page_alloc video output fbcon tileblit font bitblit softcursor

Pid: 3446, comm: modprobe Not tainted (2.6.28-13-generic #45-Ubuntu) U115
EIP: 0060:[<f8059389>] EFLAGS: 00010202 CPU: 1
EIP is at drm_mode_probed_add+0x9/0x20 [drm]
EAX: f5f96200 EBX: 00000001 ECX: f5e9f540 EDX: 00000000
ESI: f5f61c12 EDI: f5c2a000 EBP: f5e89b20 ESP: f5e89b20
 DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Process modprobe (pid: 3446, ti=f5e88000 task=f5f49920 task.ti=f5e88000)
Stack:
 f5e89b64 f805c771 f805c196 f5f37c08 c8e36a80 f5f37c08 f5f96200 f5f61c00
 00000000 00000000 f5c2a000 00000000 00000001 f5f61c12 f5f61c00 f5f96200
 f5c2a000 f5e89b84 f80b9ba9 f80c9a64 f80c983e f5c2f000 f6fa8800 f7cc8594
Call Trace:
 [<f805c771>] ? drm_add_edid_modes+0x1f1/0x220 [drm]
 [<f805c196>] ? drm_ddc_read+0x96/0x1f0 [drm]
 [<f80b9ba9>] ? intel_lvds_get_modes+0x39/0xf0 [psb]
 [<f80ba453>] ? intel_lvds_init+0x1a3/0x6c0 [psb]
 [<c02c6d4d>] ? idr_pre_get+0x3d/0x70
 [<f80baba5>] ? intel_modeset_init+0x1d5/0x3e0 [psb]
 [<f80551dc>] ? drm_bo_init_mm+0x7c/0x150 [drm]
 [<f80ad205>] ? psb_driver_load+0x6e5/0x890 [psb]
 [<f8051fd7>] ? drm_ht_create+0x97/0xc0 [drm]
 [<f8051fd7>] ? drm_ht_create+0x97/0xc0 [drm]
 [<f804e830>] ? drm_get_dev+0x330/0x5d0 [drm]
 [<c020c685>] ? sysfs_do_create_link+0xa5/0x120
 [<c02dbe3e>] ? pci_match_device+0xbe/0xd0
 [<f80ac6ad>] ? probe+0xd/0x10 [psb]
 [<c02dc60e>] ? pci_device_probe+0x5e/0x80
 [<c034f214>] ? really_probe+0x54/0x180
 [<c02dbe3e>] ? pci_match_device+0xbe/0xd0
 [<c034f37e>] ? driver_probe_device+0x3e/0x50
 [<c034f419>] ? __driver_attach+0x89/0x90
 [<c034eb53>] ? bus_for_each_dev+0x53/0x80
 [<c02dc550>] ? pci_device_remove+0x0/0x40
 [<c034f0d9>] ? driver_attach+0x19/0x20
 [<c034f390>] ? __driver_attach+0x0/0x90
 [<c034e527>] ? bus_add_driver+0x1c7/0x240
 [<c02dc550>] ? pci_device_remove+0x0/0x40
 [<c034f5b9>] ? driver_register+0x69/0x140
 [<c02dc86a>] ? __pci_register_driver+0x4a/0x90
 [<f804a4e0>] ? drm_init+0x190/0x1d0 [drm]
 [<c01cfec2>] ? ifind+0x92/0xa0
 [<f7c94000>] ? psb_init+0x0/0x1e [psb]
 [<f7c9401c>] ? psb_init+0x1c/0x1e [psb]
 [<c010111e>] ? _stext+0x2e/0x170
 [<c020c0b5>] ? sysfs_addrm_finish+0x15/0xf0
 [<c020b883>] ? sysfs_add_one+0x13/0x50
 [<c020b8ff>] ? sysfs_addrm_start+0x3f/0xa0
 [<c01a90ac>] ? __vunmap+0x9c/0xe0
 [<c01a90ac>] ? __vunmap+0x9c/0xe0
 [<c01a9141>] ? vfree+0x21/0x30
 [<c0163f5a>] ? load_module+0x103a/0x1040
 [<c0163fe8>] ? sys_init_module+0x88/0x1b0
 [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
 [<c04f0000>] ? quirk_isa_dma_hangs+0x39/0x46
Code: 00 00 5b 5e 5f 5d c3 8d 76 00 8b 4b 6c ba 03 00 00 00 89 d8 ff 51 04 8b 53 04 eb 85 8d b6 00 00 00 00 8b 48 34 55 89 e5 89 51 04 <89> 0a 8d 48 34 89 4a 04 89 50 34 5d c3 8d 76 00 8d bc 27 00 00 
EIP: [<f8059389>] drm_mode_probed_add+0x9/0x20 [drm] SS:ESP 0068:f5e89b20
---[ end trace 2cfefe727a38e8f1 ]---
```

---

### Post by djtm on 2009-07-28
Hey,

I've got exactly the same problem with my MSI U110. I've tried many things already, including all module parameters I think. And nothing helped. Still on a crappy VGA X right now... If anyone finds a cure please let me know. I thought once I've got the driver it'd be alright...

---

### Post by BlackFoXX on 2009-07-28
I'm going to have a look on the Source, but I'm a little busy atm.
:(

---

### Post by acidrock on 2009-07-29
Hey thanks for the heads up..going to try that on my dell mini 10 right away.

---

### Post by acidrock on 2009-07-29
1024x576 is working


thanks

---

### Post by PreviousN on 2009-07-30
Do you get random freezes? If so, please tell before I (and others) waste hours on this just to be disappointed. 

KTHX!

---

### Post by acidrock on 2009-07-31
yes i did get some of those 

thats why i came back! i was thinking this happens only with firefox but now im sure its random

any one experiencing the same?

---

### Post by Brianlight on 2009-08-01
Yes I'm also getting these random lockups with mouse movement on both 2D & 3D... using standard vesa drivers under Jaunty until the random lockups get solved.. it's the only way my Acer 751h netbook is usable.. atm..

---

### Post by acidrock on 2009-08-01
i just edited xorg.conf like it shows on this [thread]("http://ubuntuforums.org/showthread.php?t=1213416")
and lets see what happens

---

### Post by mikewhatever on 2009-08-01
Do you mind posting the output of glxgears, just want to check if there is any FPS bump.

---

### Post by acidrock on 2009-08-02
glx output

1606 frames in 5.0 seconds = 321.196 FPS
1410 frames in 5.0 seconds = 281.960 FPS
1556 frames in 5.0 seconds = 311.133 FPS
1262 frames in 5.0 seconds = 252.261 FPS
1327 frames in 5.0 seconds = 265.355 FPS
1382 frames in 5.0 seconds = 276.372 FPS
1670 frames in 5.0 seconds = 333.832 FPS
1141 frames in 5.0 seconds = 228.139 FPS
1127 frames in 5.0 seconds = 225.254 FPS

---

### Post by mikewhatever on 2009-08-03
That's quite good thanks. Try the following for full screen (substitute your own resolution if needed):

glxgears -geometry 1024x576

---

### Post by acidrock on 2009-08-03
ok here it is

511 frames in 5.0 seconds = 102.143 FPS
560 frames in 5.0 seconds = 111.909 FPS
643 frames in 5.0 seconds = 128.595 FPS
584 frames in 5.0 seconds = 116.690 FPS
512 frames in 5.0 seconds = 102.387 FPS
584 frames in 5.0 seconds = 116.683 FPS
610 frames in 5.0 seconds = 121.966 FPS
519 frames in 5.0 seconds = 103.713 FPS

---

### Post by slooksterpsv on 2009-10-05
This worked for my acer aspire one. I have the ao751h I had to install the drm module (the kernel psb-kernel-source). Its faster than vista and hulu works great and flash is flawless so far if netflix worked itd be bye bye vista

---

### Post by djtm on 2010-06-27
> **BlackFoXX said:**
> 
I've tried instaling it on the MSI Wind U115, but i get a seg fault when loading the "psb"-module.

I case you don't know yet: Here's a hot fix for the problem: [http://linux-tipps.blogspot.com/2009/12/x-video-finally-works-linux-on-msi-wind.html](http://linux-tipps.blogspot.com/2009/12/x-video-finally-works-linux-on-msi-wind.html)

---

### Post by BlackFoXX on 2010-06-27
Thanks. I found it already. Sorry. I should have posted it.
In the Ubuntu-Wiki there is a Repository with the fixed driver. This works for me: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

The only problem is the wireless now. It's kind of buggy since i installed the new driver.

Greetz

---

