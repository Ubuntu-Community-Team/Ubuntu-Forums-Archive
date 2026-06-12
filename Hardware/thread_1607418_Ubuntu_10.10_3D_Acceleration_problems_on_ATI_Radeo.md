---
title: "Ubuntu 10.10 3D Acceleration problems on ATI Radeon 8500LE"
date: 2010-10-27
forum: Hardware
---

### Post by AyaneMatrix on 2010-10-27
I hate having to possibly bring up an already solved problem, but I could not find a decent working solution in the forums.

For the most part, I'm having problems with my ATI Radeon 8500LE 128MB video card under Ubuntu 10.10 using Gnome for the front end. What's odd is that there is some general slowdown when compared to 9.04, but also 3D acceleration seems to be a bit weird for me as well. If I start glxgears, everything seems to work and the framerate is capped at my monitor's refresh rate (75Hz); but, let me open something like Blender and try to rotate the camera around and the entire system hardlocks and is unresponsive to any sort of keyboard commands, necessitating a forced power down.

Checking the logs (kern.log specifically), the only thing I can generally find that seem to point in any general direction is the following when another OGL app is run:
Oct 27 17:23:37 mycomputer kernel: [83586.678932] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 1
Oct 27 17:23:37 mycomputer kernel: [83586.678940] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

Again, Blender and it's subsequent lockup does not generate any anything in the logs.

So, does anyone have any ideas on where to proceed in finding a fix or should I file a bug report and wait for Ubuntu to fix the problem?:confused:

---

### Post by AyaneMatrix on 2010-10-28
Adding to my troubles, I think I figured out some of why there's so much slowdown when trying to view webpages.

Watching the task manager in XFCE, I noticed that the flash plugin, firefox and an X session were maximizing my CPU. See attached image for details.

Is there any chance that the ati drivers (ppa and stock) are at fault here or is Flash and Firefox somehow at odds with X?:confused:

---

### Post by AyaneMatrix on 2010-11-02
Got something a little more interesting to report. After trying to use Blender again, then rotating the mouse a bit, again it crashed X and blanked out the screen. Though, on the other hand, it seemed to have forced my account to logout; I could hear the login screen prompt sound. Going back to check the log, I found the following:

```
Nov  2 00:33:54 my-computer kernel: [173009.532020] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
Nov  2 00:33:54 my-computer kernel: [173009.532028] ------------[ cut here ]------------
Nov  2 00:33:54 my-computer kernel: [173009.532072] WARNING: at /home/kernel-ppa/COD/linux/drivers/gpu/drm/radeon/radeon_fence.c:235 radeon_fence_wait+0x249/0x2b0 [radeon]()
Nov  2 00:33:54 my-computer kernel: [173009.532076] Hardware name: 83114DU
Nov  2 00:33:54 my-computer kernel: [173009.532079] GPU lockup (waiting for 0x002A807D last fence id 0x002A807B)
Nov  2 00:33:54 my-computer kernel: [173009.532082] Modules linked in: binfmt_misc snd_ens1371 gameport snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon ttm drm_kms_helper snd joydev drm soundcore snd_page_alloc usbhid hid ppdev parport_pc i2c_algo_bit psmouse kbtab lp parport serio_raw intel_agp shpchp agpgart usb_storage e100 floppy mii
Nov  2 00:33:54 my-computer kernel: [173009.532123] Pid: 9706, comm: Xorg Not tainted 2.6.36-020636rc7-generic #201010070908
Nov  2 00:33:54 my-computer kernel: [173009.532127] Call Trace:
Nov  2 00:33:54 my-computer kernel: [173009.532150]  [<f0b0b899>] ? radeon_fence_wait+0x249/0x2b0 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532160]  [<c014e4d1>] warn_slowpath_common+0x81/0xa0
Nov  2 00:33:54 my-computer kernel: [173009.532181]  [<f0b0b899>] ? radeon_fence_wait+0x249/0x2b0 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532187]  [<c014e593>] warn_slowpath_fmt+0x33/0x40
Nov  2 00:33:54 my-computer kernel: [173009.532208]  [<f0b0b899>] radeon_fence_wait+0x249/0x2b0 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532216]  [<c016b270>] ? autoremove_wake_function+0x0/0x40
Nov  2 00:33:54 my-computer kernel: [173009.532237]  [<f0b0c430>] ? radeon_sync_obj_wait+0x0/0x20 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532258]  [<f0b0c441>] radeon_sync_obj_wait+0x11/0x20 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532270]  [<f091e050>] ttm_bo_wait+0xe0/0x180 [ttm]
Nov  2 00:33:54 my-computer kernel: [173009.532295]  [<f0b21955>] radeon_gem_wait_idle_ioctl+0x85/0x110 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532316]  [<f09ac6c0>] drm_ioctl+0x2d0/0x430 [drm]
Nov  2 00:33:54 my-computer kernel: [173009.532341]  [<f0b218d0>] ? radeon_gem_wait_idle_ioctl+0x0/0x110 [radeon]
Nov  2 00:33:54 my-computer kernel: [173009.532347]  [<c010a354>] ? restore_i387_fxsave+0x84/0x90
Nov  2 00:33:54 my-computer kernel: [173009.532364]  [<f09ac3f0>] ? drm_ioctl+0x0/0x430 [drm]
Nov  2 00:33:54 my-computer kernel: [173009.532369]  [<c022d0db>] vfs_ioctl+0x3b/0x50
Nov  2 00:33:54 my-computer kernel: [173009.532374]  [<c022dc74>] do_vfs_ioctl+0x64/0x1c0
Nov  2 00:33:54 my-computer kernel: [173009.532380]  [<c030b635>] ? security_file_ioctl+0x15/0x20
Nov  2 00:33:54 my-computer kernel: [173009.532384]  [<c022de27>] sys_ioctl+0x57/0x70
Nov  2 00:33:54 my-computer kernel: [173009.532390]  [<c0102cdf>] sysenter_do_call+0x12/0x28
Nov  2 00:33:54 my-computer kernel: [173009.532394] ---[ end trace a62c84519b9d3197 ]---
Nov  2 00:33:54 my-computer kernel: [173009.689247] radeon: wait for empty RBBM fifo failed ! Bad things might happen.
Nov  2 00:33:54 my-computer kernel: [173009.846200] Failed to wait GUI idle while programming pipes. Bad things might happen.
Nov  2 00:33:54 my-computer kernel: [173009.847206] radeon 0000:01:00.0: (r100_asic_reset:2082) RBBM_STATUS=0x8101C100
Nov  2 00:33:54 my-computer kernel: [173010.348267] radeon 0000:01:00.0: (r100_asic_reset:2103) RBBM_STATUS=0x80310140
Nov  2 00:33:54 my-computer kernel: [173010.845332] radeon 0000:01:00.0: (r100_asic_reset:2111) RBBM_STATUS=0x80300140
Nov  2 00:33:54 my-computer kernel: [173010.845357] radeon 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00383, writing 0x2b00387)
Nov  2 00:33:54 my-computer kernel: [173010.845370] radeon 0000:01:00.0: failed to reset GPU
Nov  2 00:33:54 my-computer kernel: [173010.845375] radeon 0000:01:00.0: GPU reset failed
Nov  2 00:33:54 my-computer kernel: [173010.845807] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:33:54 my-computer kernel: [173010.845812] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:56 my-computer kernel: [173012.615289] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:33:56 my-computer kernel: [173012.615298] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:56 my-computer kernel: [173012.861693] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:33:56 my-computer kernel: [173012.861701] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:56 my-computer kernel: [173012.864424] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:33:56 my-computer kernel: [173012.864432] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.180165] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:33:58 my-computer kernel: [173015.180173] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.272283] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:33:58 my-computer kernel: [173015.272291] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.272743] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:33:58 my-computer kernel: [173015.272749] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.273219] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:33:58 my-computer kernel: [173015.273225] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.290543] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:33:58 my-computer kernel: [173015.290552] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.290989] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:33:58 my-computer kernel: [173015.290996] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.291397] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:33:58 my-computer kernel: [173015.291404] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.300305] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:33:58 my-computer kernel: [173015.300314] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.300788] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:33:58 my-computer kernel: [173015.300795] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.301203] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:33:58 my-computer kernel: [173015.301208] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.301607] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:33:58 my-computer kernel: [173015.301612] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.340335] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:33:58 my-computer kernel: [173015.340343] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.340816] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:33:58 my-computer kernel: [173015.340822] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.341225] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:33:58 my-computer kernel: [173015.341231] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.341637] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:33:58 my-computer kernel: [173015.341643] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.356295] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:33:58 my-computer kernel: [173015.356303] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.356778] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:33:58 my-computer kernel: [173015.356784] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.357189] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:33:58 my-computer kernel: [173015.357195] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.357592] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:33:58 my-computer kernel: [173015.357598] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.386321] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:33:58 my-computer kernel: [173015.386329] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.386804] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:33:58 my-computer kernel: [173015.386811] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.387220] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:33:58 my-computer kernel: [173015.387226] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.387624] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:33:58 my-computer kernel: [173015.387629] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.389160] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:33:58 my-computer kernel: [173015.389167] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.389639] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:33:58 my-computer kernel: [173015.389645] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.390052] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:33:58 my-computer kernel: [173015.390057] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.390455] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:33:58 my-computer kernel: [173015.390461] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.390878] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:33:58 my-computer kernel: [173015.390883] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.391290] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:33:58 my-computer kernel: [173015.391295] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.391692] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:33:58 my-computer kernel: [173015.391697] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.408456] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:33:58 my-computer kernel: [173015.408465] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.408934] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:33:58 my-computer kernel: [173015.408940] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.457930] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:33:58 my-computer kernel: [173015.457938] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.458407] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:33:58 my-computer kernel: [173015.458412] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.458858] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:33:58 my-computer kernel: [173015.458863] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:58 my-computer kernel: [173015.459292] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:33:58 my-computer kernel: [173015.459297] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.469153] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:33:59 my-computer kernel: [173015.469162] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.469620] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:33:59 my-computer kernel: [173015.469627] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.470028] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:33:59 my-computer kernel: [173015.470034] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.470457] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:33:59 my-computer kernel: [173015.470463] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.470879] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:33:59 my-computer kernel: [173015.470884] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173015.471282] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:33:59 my-computer kernel: [173015.471287] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173016.281460] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:33:59 my-computer kernel: [173016.281469] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173016.345007] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:33:59 my-computer kernel: [173016.345015] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:33:59 my-computer kernel: [173016.347066] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:33:59 my-computer kernel: [173016.347073] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:00 my-computer kernel: [173016.787123] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:34:00 my-computer kernel: [173016.787132] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:00 my-computer kernel: [173016.797255] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:34:00 my-computer kernel: [173016.797263] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:00 my-computer kernel: [173017.139815] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:34:00 my-computer kernel: [173017.139826] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:00 my-computer kernel: [173017.145250] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:34:00 my-computer kernel: [173017.145258] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173017.477508] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:34:01 my-computer kernel: [173017.477518] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173017.489172] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:34:01 my-computer kernel: [173017.489180] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173017.872142] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:34:01 my-computer kernel: [173017.872152] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173017.879025] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:34:01 my-computer kernel: [173017.879034] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173018.318270] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:34:01 my-computer kernel: [173018.318280] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:01 my-computer kernel: [173018.440736] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:34:01 my-computer kernel: [173018.440745] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173018.771925] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:34:02 my-computer kernel: [173018.771936] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173018.777912] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:34:02 my-computer kernel: [173018.777920] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.144827] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:34:02 my-computer kernel: [173019.144836] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.145981] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:34:02 my-computer kernel: [173019.145988] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.151601] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:34:02 my-computer kernel: [173019.151609] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.151695] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:34:02 my-computer kernel: [173019.151700] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.156483] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:34:02 my-computer kernel: [173019.156492] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.158639] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:34:02 my-computer kernel: [173019.158646] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.160971] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:34:02 my-computer kernel: [173019.160979] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.161964] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:34:02 my-computer kernel: [173019.161970] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.170031] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:34:02 my-computer kernel: [173019.170040] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.170473] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:34:02 my-computer kernel: [173019.170479] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.208481] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:34:02 my-computer kernel: [173019.208490] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.311699] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:34:02 my-computer kernel: [173019.311707] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.313413] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:34:02 my-computer kernel: [173019.313422] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.335931] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:34:02 my-computer kernel: [173019.335940] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.336091] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:34:02 my-computer kernel: [173019.336096] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.338099] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:34:02 my-computer kernel: [173019.338107] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.339940] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:34:02 my-computer kernel: [173019.339948] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:02 my-computer kernel: [173019.343090] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:34:02 my-computer kernel: [173019.343098] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.525478] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:34:03 my-computer kernel: [173019.525487] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.534426] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:34:03 my-computer kernel: [173019.534434] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.545474] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:34:03 my-computer kernel: [173019.545484] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.552750] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Nov  2 00:34:03 my-computer kernel: [173019.552759] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.554455] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(10).
Nov  2 00:34:03 my-computer kernel: [173019.554463] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.557628] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(11).
Nov  2 00:34:03 my-computer kernel: [173019.557637] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.560991] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(12).
Nov  2 00:34:03 my-computer kernel: [173019.561000] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.571404] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(13).
Nov  2 00:34:03 my-computer kernel: [173019.571413] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.575515] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(14).
Nov  2 00:34:03 my-computer kernel: [173019.575523] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.581866] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(15).
Nov  2 00:34:03 my-computer kernel: [173019.581875] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.590633] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(0).
Nov  2 00:34:03 my-computer kernel: [173019.590644] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.712849] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(1).
Nov  2 00:34:03 my-computer kernel: [173019.712857] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.716789] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(2).
Nov  2 00:34:03 my-computer kernel: [173019.716797] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.718891] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(3).
Nov  2 00:34:03 my-computer kernel: [173019.718900] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.786389] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
Nov  2 00:34:03 my-computer kernel: [173019.786397] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:03 my-computer kernel: [173019.794584] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
Nov  2 00:34:03 my-computer kernel: [173019.794592] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:11 my-computer kernel: [173027.771318] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Nov  2 00:34:11 my-computer kernel: [173027.771326] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:13 my-computer kernel: [173029.770406] SysRq : Keyboard mode set to system default
Nov  2 00:34:14 my-computer kernel: [173030.915920] SysRq : Terminate All Tasks
Nov  2 00:34:14 my-computer kernel: [173030.948425] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Nov  2 00:34:14 my-computer kernel: [173030.948434] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Nov  2 00:34:14 my-computer kernel: [173030.951552] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(8).
Nov  2 00:34:14 my-computer kernel: [173030.951560] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
```

What's interesting is that if I use something like Minecraft (after updating Java), I can get a low and steady frame-rate.

I guess I should also point out that this problem shows up in the official X/radeon drivers as it does with the X-edgers ones.

---

