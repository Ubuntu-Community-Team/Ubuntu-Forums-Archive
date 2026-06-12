---
title: "nouveau graphics driver freeze"
date: 2018-07-09
forum: Hardware
---

### Post by st.w on 2018-07-09
Hi,

I've installed a fresh copy of Ubuntu 18.04 using the default  GNOME desktop and drivers.

graphics hardware: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)

Unfortunately it runs very unstable on my hardware and I encounter many graphics issues. The worst (and most annoying) of them is an occasional desktop freeze. In that I can still move the mouse pointer, but cannot interact the the GUI. Switching to a console using Ctrl+Alt+F3 works, but it might take quite long. I've found the following error message in /var/log/kern.log

```
Jul  9 19:32:38 ubuntu kernel: [   56.999238] BUG: unable to handle kernel NULL pointer dereference at 0000000000000040
Jul  9 19:32:38 ubuntu kernel: [   56.999399] IP: nouveau_mem_host+0x47/0x1b0 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999407] PGD 0 P4D 0 
Jul  9 19:32:38 ubuntu kernel: [   56.999415] Oops: 0000 [#1] SMP PTI
Jul  9 19:32:38 ubuntu kernel: [   56.999423] Modules linked in: usblp tda1004x saa7134_dvb saa7134_alsa videobuf2_dvb dvb_core tda827x arc4 tda8290 snd_hda_codec_realtek snd_hda_codec_generic tuner snd_hda_intel rt2800usb snd_hda_codec rt2x00usb snd_hda_core snd_hwdep rt2800lib coretemp snd_pcm saa7134 rt2x00lib tveeprom snd_seq_midi snd_seq_midi_event v4l2_common kvm_intel videobuf2_dma_sg videobuf2_memops videobuf2_v4l2 videobuf2_core videodev mac80211 input_leds snd_rawmidi rc_medion_x10_or2x ati_remote kvm media rc_core irqbypass snd_seq cfg80211 snd_seq_device serio_raw snd_timer snd soundcore lpc_ich shpchp mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid uas usb_storage nouveau mxm_wmi wmi video i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt firewire_ohci
Jul  9 19:32:38 ubuntu kernel: [   56.999528]  ahci firewire_core psmouse libahci fb_sys_fops crc_itu_t e1000e drm ptp pps_core
Jul  9 19:32:38 ubuntu kernel: [   56.999549] CPU: 3 PID: 1233 Comm: gnome-shell Not tainted 4.15.0-24-generic #26-Ubuntu
Jul  9 19:32:38 ubuntu kernel: [   56.999556] Hardware name: MEDIONPC MS-7502/MS-7502, BIOS 6.00 PG 01/13/2010
Jul  9 19:32:38 ubuntu kernel: [   56.999607] RIP: 0010:nouveau_mem_host+0x47/0x1b0 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999614] RSP: 0018:ffffa7b14292f7a0 EFLAGS: 00010246
Jul  9 19:32:38 ubuntu kernel: [   56.999621] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffffa7b14292f918
Jul  9 19:32:38 ubuntu kernel: [   56.999628] RDX: ffff977de7db3500 RSI: ffff977ddf638000 RDI: ffffa7b14292f918
Jul  9 19:32:38 ubuntu kernel: [   56.999635] RBP: ffffa7b14292f7f0 R08: 0000000000027080 R09: ffffffffc03726ef
Jul  9 19:32:38 ubuntu kernel: [   56.999642] R10: ffffe9cc8679b8c0 R11: 00000000000003b8 R12: ffff977ddf638f80
Jul  9 19:32:38 ubuntu kernel: [   56.999648] R13: ffff977ddf638f80 R14: ffff977ddd8ae518 R15: ffffa7b14292f918
Jul  9 19:32:38 ubuntu kernel: [   56.999656] FS:  00007f834f6a0ac0(0000) GS:ffff977defd80000(0000) knlGS:0000000000000000
Jul  9 19:32:38 ubuntu kernel: [   56.999664] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul  9 19:32:38 ubuntu kernel: [   56.999670] CR2: 0000000000000040 CR3: 00000001a0272000 CR4: 00000000000006e0
Jul  9 19:32:38 ubuntu kernel: [   56.999677] Call Trace:
Jul  9 19:32:38 ubuntu kernel: [   56.999723]  nv50_sgdma_bind+0x1d/0x30 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999743]  ttm_tt_bind+0x44/0x60 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999752]  ttm_bo_handle_move_mem+0x589/0x5c0 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999762]  ? ttm_bo_mem_space+0x39d/0x470 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999771]  ttm_bo_evict+0x13d/0x340 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999781]  ttm_mem_evict_first+0x159/0x1b0 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999790]  ttm_bo_mem_space+0x312/0x470 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999800]  ttm_bo_validate+0xd4/0x160 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999809]  ttm_bo_init_reserved+0x393/0x430 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999818]  ttm_bo_init+0x2d/0x90 [ttm]
Jul  9 19:32:38 ubuntu kernel: [   56.999859]  ? nouveau_bo_invalidate_caches+0x10/0x10 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999900]  nouveau_bo_new+0x40c/0x580 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999940]  ? nouveau_bo_invalidate_caches+0x10/0x10 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   56.999982]  nouveau_gem_new+0x60/0x130 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   57.000023]  nouveau_gem_ioctl_new+0x59/0xe0 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   57.000571]  ? nouveau_gem_new+0x130/0x130 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   57.001112]  drm_ioctl_kernel+0x5f/0xb0 [drm]
Jul  9 19:32:38 ubuntu kernel: [   57.001589]  drm_ioctl+0x31b/0x3d0 [drm]
Jul  9 19:32:38 ubuntu kernel: [   57.002118]  ? nouveau_gem_new+0x130/0x130 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   57.002619]  ? update_load_avg+0x57f/0x6e0
Jul  9 19:32:38 ubuntu kernel: [   57.003112]  ? __cgroup_account_cputime+0x28/0x30
Jul  9 19:32:38 ubuntu kernel: [   57.003577]  ? update_curr+0x10f/0x1d0
Jul  9 19:32:38 ubuntu kernel: [   57.004069]  nouveau_drm_ioctl+0x72/0xc0 [nouveau]
Jul  9 19:32:38 ubuntu kernel: [   57.004551]  do_vfs_ioctl+0xa8/0x630
Jul  9 19:32:38 ubuntu kernel: [   57.005049]  ? __schedule+0x299/0x8a0
Jul  9 19:32:38 ubuntu kernel: [   57.005507]  SyS_ioctl+0x79/0x90
Jul  9 19:32:38 ubuntu kernel: [   57.005961]  do_syscall_64+0x73/0x130
Jul  9 19:32:38 ubuntu kernel: [   57.006399]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
Jul  9 19:32:38 ubuntu kernel: [   57.006830] RIP: 0033:0x7f834c7615d7
Jul  9 19:32:38 ubuntu kernel: [   57.007254] RSP: 002b:00007ffd51c28078 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
Jul  9 19:32:38 ubuntu kernel: [   57.007726] RAX: ffffffffffffffda RBX: 00005579221d88f0 RCX: 00007f834c7615d7
Jul  9 19:32:38 ubuntu kernel: [   57.008204] RDX: 00007ffd51c280d0 RSI: 00000000c0306480 RDI: 000000000000000c
Jul  9 19:32:38 ubuntu kernel: [   57.008670] RBP: 00007ffd51c280d0 R08: 0000000000000000 R09: 00007f834ca36c40
Jul  9 19:32:38 ubuntu kernel: [   57.009141] R10: 0000000000000007 R11: 0000000000000246 R12: 00000000c0306480
Jul  9 19:32:38 ubuntu kernel: [   57.009613] R13: 000000000000000c R14: 000055792319bb28 R15: 00005579204962d0
Jul  9 19:32:38 ubuntu kernel: [   57.010065] Code: 65 48 8b 04 25 28 00 00 00 48 89 45 d0 31 c0 49 8b 5d 00 48 c7 45 b8 00 00 00 00 48 c7 45 c0 00 00 00 00 48 c7 45 c8 00 00 00 00 <48> 8b 7b 40 48 8d 83 f8 00 00 00 44 0f b6 73 39 48 89 45 b0 4c 
Jul  9 19:32:38 ubuntu kernel: [   57.011170] RIP: nouveau_mem_host+0x47/0x1b0 [nouveau] RSP: ffffa7b14292f7a0
Jul  9 19:32:38 ubuntu kernel: [   57.011645] CR2: 0000000000000040
Jul  9 19:32:38 ubuntu kernel: [   57.015156] ---[ end trace ca369eb237b2e3ad ]---
```

I'd be glad for any help to solve the issue - Thank You!

BR, stw

---

### Post by Autodave on 2018-07-09
According to Nvidia's site, the 340.xxx should be the one that you need.  That driver is in the repositories. You can get and install it from there. Do NOT d-l it from the Nvidia site!

---

### Post by st.w on 2018-07-10
Thank You for Your response. I already tried that driver (installed via the "Software & Updates" - "Additional Drivers" GUI, as recommended by Ubuntu), but unfortunately it doesn't seem to support Wayland at all and neither could I set the custom mode-setting for my monitor to get it working in X11.
Wayland support is required because I'm using the machine for application development targeting Wayland. So I most likely can't use the NVidia driver, but will have to use nouveau.

---

### Post by Yellow Pasque on 2018-07-11
This is the closest I could find: [https://bugs.freedesktop.org/show_bug.cgi?id=105687](https://bugs.freedesktop.org/show_bug.cgi?id=105687)

The upshot is that you should try the latest kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17.5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17.5/)

---

