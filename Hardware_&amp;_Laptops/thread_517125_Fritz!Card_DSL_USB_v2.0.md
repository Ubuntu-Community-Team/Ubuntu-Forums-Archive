---
title: "Fritz!Card DSL USB v2.0"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by picard0815 on 2007-08-04
Hi all.

First of all: I'm trying to get this pice of hardware (combined ISDN and DSL modem) to work for some weeks now. I searched a lot of forums and tried any tip t found using google. No success yet.
So i hope anyone can help me.

I installed Ubuntu Feisty with Kernel 2.6.20-16-generic, the packages avm-fritz-firmware-2.6.20-16 linux-restricted-modules-2.6.20-generic capiutils and some more i don't remember now.

This is the output of dmesg when i plug the Fritz!Card into an usb port:
[ 2371.391109] usb 2-3: new full speed USB device using ohci_hcd and address 4
[ 2371.653022] usb 2-3: configuration #1 chosen from 2 choices
[ 2371.658997] kcapi: Controller [001]: fcdslusb2-0004 attached
[ 2371.659004] kcapi: Controller [002]: fcdslusb2-0004 attached

lsusb gives me:
Bus 002 Device 004: ID 057c:3600 AVM GmbH 

So i uncommented the following line in /etc/isdn/capi.conf:
fcdslusb2      fds2base.frm    DSS1    -       -       -       -

So looks good to me up to here. But if i try to start /usr/sbin/capiinit my pc crashed an the only thing i can do is hit the reset button.

I tried downloading the driver from [www.avm.de](www.avm.de) and compile it myself. No change - still crashes on capiinit.

So what can i do now? Any tips?

---

### Post by picard0815 on 2007-08-07
Ok. Some more info i got by trying to install on a amd64 platform.
It's debian but doesn't work either.

Any suggestions?

On connecting the usb cable /var/log/messages contains
Aug  7 14:39:31 schleuse kernel: fcdslusb2: AVM FRITZ!Card DSL USB v2.0 driver, revision 0.4.5
Aug  7 14:39:31 schleuse kernel: fcdslusb2: (fcdslusb2 built on Apr 24 2007 at 18:08:41)
Aug  7 14:39:31 schleuse kernel: fcdslusb2: -- 64 bit CAPI driver --
Aug  7 14:39:31 schleuse kernel: fcdslusb2: Loading...
Aug  7 14:39:31 schleuse kernel: kcapi: Controller 1: fcdslusb2-0002 attached
Aug  7 14:39:31 schleuse kernel: kcapi: Controller 2: fcdslusb2-0002 attached
Aug  7 14:39:31 schleuse kernel: usbcore: registered new driver fcdslusb2
Aug  7 14:39:31 schleuse kernel: fcdslusb2: Loaded.

Doing a capiinit gives:
Aug  7 14:43:12 schleuse kernel: fcdslusb2: Using VCC/VPI/VCI = 0x1/0x1/0x20
Aug  7 14:43:12 schleuse kernel: fcdslusb2: Stack version 3.11-07
Aug  7 14:43:12 schleuse kernel: fcdslusb2: Stack version 3.11-07
Aug  7 14:43:12 schleuse kernel: NMI Watchdog detected LOCKUP on CPU 0
Aug  7 14:43:12 schleuse kernel: CPU 0 
Aug  7 14:43:12 schleuse kernel: Modules linked in: capi fcdslusb2 kernelcapi cpufreq_conservative cpufreq_stats speedstep_centrin
o freq_table nfs nfsd exportfs lockd nfs_acl sunrpc ppdev parport_pc lp parport button ac battery capifs ipv6 ext3 jbd mbcache sha
256 serpent dm_crypt dm_snapshot dm_mirror dm_mod loop snd_hda_intel snd_hda_codec dvb_ttpci lnbp21 l64781 snd_pcm_oss snd_pcm saa
7146_vv video_buf saa7146 snd_mixer_oss videodev v4l1_compat v4l2_common ves1820 stv0299 dvb_core snd_seq_dummy tda8083 sp8870 fir
mware_class snd_seq_oss stv0297 ves1x93 snd_seq_midi_event snd_seq snd_timer snd_seq_device ttpci_eeprom intel_agp snd soundcore s
nd_page_alloc psmouse i2c_i801 evdev i2c_core serio_raw pcspkr xfs raid1 md_mod ide_generic sd_mod ata_piix libata scsi_mod ehci_h
cd generic ide_core e1000 uhci_hcd thermal processor fan
Aug  7 14:43:12 schleuse kernel: Pid: 10352, comm: capiinit Tainted: P      2.6.18-4-amd64 #1
Aug  7 14:43:12 schleuse kernel: RIP: 0010:[<ffffffff8025e929>]  [<ffffffff8025e929>] .text.lock.spinlock+0x25/0x8a
Aug  7 14:43:12 schleuse kernel: RSP: 0018:ffff810051c87c70  EFLAGS: 00000086
Aug  7 14:43:12 schleuse kernel: RAX: 0000000000000282 RBX: 0000000000000800 RCX: ffffffff884e3970
Aug  7 14:43:12 schleuse kernel: RDX: ffff810051c87cb0 RSI: ffff810051c87cb8 RDI: ffff81006f4b4ccc
Aug  7 14:43:12 schleuse kernel: RBP: ffff81006f4b4cc4 R08: ffff81003b66f004 R09: 0000000000000000
Aug  7 14:43:12 schleuse kernel: R10: 0000000000000003 R11: ffff81007ead6f00 R12: ffff81006f4b4ccc
Aug  7 14:43:12 schleuse kernel: R13: ffff810051c87cb8 R14: ffff810051c87cb0 R15: 0000000000000004
Aug  7 14:43:12 schleuse kernel: FS:  00002b19638f76d0(0000) GS:ffffffff80521000(0000) knlGS:0000000000000000
Aug  7 14:43:12 schleuse kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug  7 14:43:12 schleuse kernel: CR2: 00002b19635ed000 CR3: 000000005ad71000 CR4: 00000000000006e0
Aug  7 14:43:12 schleuse kernel: Process capiinit (pid: 10352, threadinfo ffff810051c86000, task ffff81006dc91040)
Aug  7 14:43:12 schleuse kernel: Stack:  ffffffff8850724e 0000000000000800 ffffffff884e3970 ffff81003b66f004
Aug  7 14:43:12 schleuse kernel:  ffff81003b66f024 0000000000000800 ffffffff885034fb 0000000000000003
Aug  7 14:43:12 schleuse kernel:  0000000000000003 0000000000000004 0000000000000282 0000000000000800
Aug  7 14:43:12 schleuse kernel: Call Trace:
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8850724e>] :fcdslusb2:claim_urb+0x1d/0x8f
Aug  7 14:43:12 schleuse kernel:  [<ffffffff884e3970>] :fcdslusb2:Block_RxHandler+0x0/0x4d0
Aug  7 14:43:12 schleuse kernel:  [<ffffffff885034fb>] :fcdslusb2:os_usb_submit_rx+0x32/0xe9
Aug  7 14:43:12 schleuse kernel:  [<ffffffff88505761>] :fcdslusb2:OSHWRxBuffer+0x44/0x4f
Aug  7 14:43:12 schleuse kernel:  [<ffffffff884abf91>] :fcdslusb2:BLK_Start+0x91/0xd0
Aug  7 14:43:12 schleuse kernel:  [<ffffffff884acdc3>] :fcdslusb2:E1_Activate+0x13/0x20
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8849a0e6>] :fcdslusb2:CM_Activate+0x6/0x50
Aug  7 14:43:12 schleuse kernel:  [<ffffffff885045e1>] :fcdslusb2:start+0x1b4/0x21f
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8850479a>] :fcdslusb2:load_ware+0x14e/0x1aa
Aug  7 14:43:12 schleuse kernel:  [<ffffffff884893b0>] :kernelcapi:capi20_manufacturer+0x2d5/0x57c
Aug  7 14:43:12 schleuse kernel:  [<ffffffff80264926>] do_gettimeofday+0x50/0x94
Aug  7 14:43:12 schleuse kernel:  [<ffffffff802568b4>] getnstimeofday+0x10/0x28
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8021113a>] rb_insert_color+0xb2/0xda
Aug  7 14:43:12 schleuse kernel:  [<ffffffff802921cf>] enqueue_hrtimer+0x55/0x70
Aug  7 14:43:12 schleuse kernel:  [<ffffffff885738ce>] :capi:capi_ioctl+0x2c1/0x425
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8023e3e5>] do_ioctl+0x55/0x6b
Aug  7 14:43:12 schleuse kernel:  [<ffffffff8022e01b>] vfs_ioctl+0x252/0x26b
Aug  7 14:43:12 schleuse kernel:  [<ffffffff802484d4>] sys_ioctl+0x59/0x78
Aug  7 14:43:12 schleuse kernel:  [<ffffffff802584d6>] system_call+0x7e/0x83
Aug  7 14:43:12 schleuse kernel: 
Aug  7 14:43:12 schleuse kernel: 
Aug  7 14:43:12 schleuse kernel: Code: 7e f9 e9 d4 fe ff ff f3 90 83 3f 00 7e f9 e9 d3 fe ff ff f3 
Aug  7 14:43:12 schleuse kernel: console shuts up ...

---

