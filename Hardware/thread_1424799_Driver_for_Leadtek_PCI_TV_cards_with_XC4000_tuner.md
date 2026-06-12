---
title: "Driver for Leadtek PCI TV cards with XC4000 tuner"
date: 2010-03-08
forum: Hardware
---

### Post by istvanv on 2010-03-08
Hi! The following patch implements support for those Leadtek PCI TV tuner cards which use a CX2388x/XC4000 chipset. These cards are not officially supported on Linux yet, due to the XC4000 tuner chip. Examples of such cards include the WinFast DTV2000 H Plus (I have one), a version of the DTV1800 H with XC4000 tuner (there is another one that uses XC3028, and is already supported on Linux), and also versions of the TV2000 XP Global with XC4100 (these latter cards may not actually have been sold in practice, they were just added based on Windows .INF files).
  [http://www.sharemation.com/IstvanV/v4l/xc4000.html](http://www.sharemation.com/IstvanV/v4l/xc4000.html)
The patch is based on Devin Heitmueller's XC4000 driver for the Pinnacle PCTV 340e.

With the DTV2000 H Plus, the following have been tested, and seem to work well:
 - analog TV (I have access to PAL channels mainly, and a single SECAM one, so other standards like NTSC are untested; all are implemented, however)
 - FM radio
 - external analog inputs (Composite, S-Video, audio in)
 - IR
Unfortunately, I cannot test DVB-T, since a usable DVB-T signal is not available, but it is implemented, and may in theory work. What I can confirm is that it does create devices in /dev/dvb, 'dvbtune' finds a "Zarlink ZL10353 DVB-T" frontend, and when trying to use it, the XC4000 driver (according to debug output) seems to be doing everything correctly to tune to the selected channel, but obviously there is no signal. So, if you do have access to DVB-T input, please report any success or failure trying to get it to work.

This is experimental code, so use it at your own risk, and only if you are familiar with compiling and installing the V4L-DVB drivers from source code. However, I do use it for a few months now without major problems, so it hopefully does not have serious reliability problems.

NOTE: when compiling V4L sources on Ubuntu, there may be errors in the 'firedtv' module; for more details and suggested fixes/workarounds, see this thread: [http://ubuntuforums.org/archive/index.php/t-1337146.html](http://ubuntuforums.org/archive/index.php/t-1337146.html).

---

### Post by istvanv on 2010-03-10
Update: it has been reported by one user that DVB-T works with the DTV2000 H Plus, but it used the wrong RF connector (cable instead of antenna). I have uploaded a new patch to the above mentioned site, which hopefully fixes this, and also some minor (mainly analog TV related) bugs in the CX88 driver. It is now also against a more recent revision of V4L-DVB.

---

### Post by cdekter on 2010-03-10
Thanks for your work on this Istvan! I've added a link to this thread to the relevant [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/458304"). I suppose the chances are remote but it would be great to get this into Lucid.

---

### Post by istvanv on 2010-03-24
Another update: the driver now supports the PxDVR3200 H (107d:6f39) as well (patch contributed by Mirek Slugen). Also, the web page has been moved to [http://istvanv.users.sourceforge.net/v4l/xc4000.html](http://istvanv.users.sourceforge.net/v4l/xc4000.html); the previous sharemation.com site is currently down.

---

### Post by pvautrin on 2010-06-05
Hi Istvan,

I am trying to make my PCTV 340e work on Lucid x64 for 7MHz channels (Australia).

I tried Devin's branch previously on a Karmic x64 but couldn't receive any channels since he only implemented 8MHz so far (and seems too busy currently to complete this project, including the rebase to a kernel more recent than 2.6.31).

I was hoping your patch, which is based on Devin's work, also included my usb stick, but apparently not.

I can apply patches and recompile, but my programming skills are a bit limited.

Could you please help creating some patches to add support for PCTV 340e?
I'm not sure if it would be simpler to add Devin's PCTV 340e bits to your latest driver, or add your driver+rebase code to Devin's branch...

Thanks for your work so far!
Cheers,
PY

Edit: Never mind, another user had already done the work. My PCTV 340e now works in Lucid with 7MHz channels.
[http://www.kernellabs.com/blog/?p=1279#comment-1501](http://www.kernellabs.com/blog/?p=1279#comment-1501)

---

### Post by btdave on 2010-06-17
I've also got one of these cards (DTV2000H Plus), firstly windows wouldn't pick it up right and installed the wrong drivers for it, then the software wouldn't install correctly either cause it couldn't find the card, long story short, I've gotten it to work under windows (abliet a bit shakily cause of the software)
However Ubuntu Studio... thats a different story.

I seem to be getting an I2C read failed in the dmesg output.

I've followed the procedure on here ([http://istvanv.users.sourceforge.net/v4l/xc4000.html](http://istvanv.users.sourceforge.net/v4l/xc4000.html)) however, there is no change in the dmesg output with or without the firmware being put into /lib/firmware

heres a part of my dmesg output:
[   16.469637] cfg80211: Calling CRDA to update world regulatory domain
[   16.474636] Linux video capture interface: v2.00
[   16.502061] cfg80211: World regulatory domain updated:
[   16.502064]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.502066]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.502068]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.502070]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.502072]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.502074]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.512450] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   16.512489]   alloc irq_desc for 22 on node -1
[   16.512491]   alloc kstat_irqs on node -1
[   16.512497] cx8800 0000:05:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.512717] cx88[0]: subsystem: 107d:6f44, board: WinFast DTV2000 H PLUS [card=85,insmod option], frontend(s): 1
[   16.512719] cx88[0]: TV tuner type 85, Radio tuner type 85
[   16.513791] ieee1394: raw1394: /dev/raw1394 device initialized
[   16.588721] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   16.590620] cx2388x alsa driver version 0.0.7 loaded
[   16.623200] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.623233] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.634815] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   16.639978] usbcore: registered new interface driver snd-usb-audio
[   16.719729] hda_codec: ALC888: BIOS auto-probing.
[   16.721082] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   16.877057] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.877065] nvidia 0000:01:00.0: setting latency timer to 64
[   16.877069] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.882488] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   16.972779] ppdev: user-space parallel port driver
[   16.996451] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   17.041961] xc4000 0-0061: creating new instance
[   17.043654] xc4000: I2C read failed
[   17.043658] xc4000 0-0061: destroying instance
[   17.043765] xc4000 0-0061: creating new instance
[   17.044557] xc4000: I2C read failed
[   17.044559] xc4000 0-0061: destroying instance
[   17.044762] input: cx88 IR (WinFast DTV2000 H PLUS as /devices/pci0000:00/0000:00:1e.0/0000:05:06.0/irrcv/irrcv0/input6
[   17.044832] irrcv0: cx88 IR (WinFast DTV2000 H PLUS as /devices/pci0000:00/0000:00:1e.0/0000:05:06.0/irrcv/irrcv0
[   17.044839] cx88[0]/0: found at 0000:05:06.0, rev: 5, irq: 22, latency: 64, mmio: 0xfd000000
[   17.044848] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.044906] cx88[0]/0: registered device video0 [v4l2]
[   17.044948] cx88[0]/0: registered device vbi0
[   17.044990] cx88[0]/0: registered device radio0
[   17.045125] tuner 0-0061: Tuner has no way to set tv freq
[   17.045233] rt2500pci 0000:05:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.069617] phy0: Selected rate control algorithm 'minstrel'
[   17.070216] Registered led device: rt2500pci-phy0::radio
[   17.070230] Registered led device: rt2500pci-phy0::quality
[   17.070340] cx88[0]/2: cx2388x 8802 Driver Manager
[   17.070355] cx88-mpeg driver manager 0000:05:06.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.070363] cx88[0]/2: found at 0000:05:06.2, rev: 5, irq: 22, latency: 64, mmio: 0xfb000000
[   17.070368] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.070529] cx88_audio 0000:05:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.070535] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.070557] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   17.095033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.162720] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   17.162723] cx88/2: registering cx8802 driver, type: dvb access: shared
[   17.162726] cx88[0]/2: subsystem: 107d:6f44, board: WinFast DTV2000 H PLUS [card=85]
[   17.162728] cx88[0]/2: cx2388x based DVB/ATSC card
[   17.162730] cx8802_alloc_frontends() allocating 1 frontend(s)
[   17.242479] xc4000 0-0061: creating new instance
[   17.243398] xc4000: I2C read failed
[   17.243401] xc4000 0-0061: destroying instance
[   17.243460] cx88[0]/2: xc4000 attach failed
[   17.243627] BUG: unable to handle kernel NULL pointer dereference at 0000000000000208
[   17.244007] IP: [<ffffffffa0eb890f>] dvb_frontend_stop+0x1f/0xb0 [dvb_core]
[   17.244226] PGD 687c0067 PUD 6b6b4067 PMD 0 
[   17.244226] Oops: 0002 [#1] PREEMPT SMP 
[   17.244918] last sysfs file: /sys/power/state
[   17.244918] CPU 0 
[   17.244918] Modules linked in: zl10353 cx88_dvb(+) dm_crypt cx88_vp3054_i2c videobuf_dvb dvb_core arc4 xc4000 tuner ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_usb_audio snd_usb_lib snd_hwdep snd_pcm_oss snd_mixer_oss cx88_alsa cx8802 snd_seq_dummy snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi rt2500pci snd_seq_midi_event rt2x00pci rt2x00lib snd_seq raw1394 cx8800 snd_timer snd_seq_device led_class mac80211 cx88xx v4l2_common videodev snd ir_common i2c_algo_bit tveeprom v4l1_compat ir_core v4l2_compat_ioctl32 videobuf_dma_sg btcx_risc videobuf_core cfg80211 eeprom_93cx6 nvidia(P) psmouse serio_raw lp soundcore parport snd_page_alloc ohci1394 ieee1394 fbcon tileblit font bitblit softcursor r8169 mii pata_jmicron vga16fb vgastate intel_agp
[   17.249263] Pid: 1223, comm: modprobe Tainted: P           2.6.32-22-preempt #36-Ubuntu MS-7519
[   17.249263] RIP: 0010:[<ffffffffa0eb890f>]  [<ffffffffa0eb890f>] dvb_frontend_stop+0x1f/0xb0 [dvb_core]
[   17.249263] RSP: 0018:ffff88007a66bdc8  EFLAGS: 00010246
[   17.249263] RAX: ffff88007a66a000 RBX: 0000000000000000 RCX: 0000000000000fdc
[   17.249263] RDX: ffff880001c167c8 RSI: 0000000000000000 RDI: ffff8800652b2c08
[   17.249263] RBP: ffff88007a66bdd8 R08: 0000000000000000 R09: 0000000000000000
[   17.249263] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8800652b2c08
[   17.249263] R13: ffff88007b975800 R14: ffff88007a563800 R15: ffff8800652b3180
[   17.249263] FS:  00007fe81b336700(0000) GS:ffff880001c00000(0000) knlGS:0000000000000000
[   17.249263] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   17.249263] CR2: 0000000000000208 CR3: 0000000037bff000 CR4: 00000000000006f0
[   17.249263] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   17.249263] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   17.249263] Process modprobe (pid: 1223, threadinfo ffff88007a66a000, task ffff88007bfdc4d0)
[   17.249263] Stack:
[   17.249263]  0000000000000000 0000000000000000 ffff88007a66be28 ffffffffa0eb89dc
[   17.249263] <0> ffff88007a66be08 ffffffff810a3ebd ffff88007a66be08 ffff8800652b2c08
[   17.249263] <0> ffff88007a66be28 ffffffffa0eb812d ffff88007a563800 ffff8800652b3000
[   17.331275] Call Trace:
[   17.331275]  [<ffffffffa0eb89dc>] dvb_unregister_frontend+0x3c/0x110 [dvb_core]
[   17.331275]  [<ffffffff810a3ebd>] ? symbol_put_addr+0x3d/0x50
[   17.331275]  [<ffffffffa0eb812d>] ? dvb_frontend_detach+0x7d/0x90 [dvb_core]
[   17.331275]  [<ffffffffa0ddc4a4>] cx8802_dvb_probe+0x6d4/0x23c0 [cx88_dvb]
[   17.331275]  [<ffffffff8113fc96>] ? __kmalloc+0x1a6/0x1b0
[   17.331275]  [<ffffffffa0dec7fa>] cx8802_register_driver+0x19a/0x220 [cx8802]
[   17.331275]  [<ffffffffa0cd1000>] ? dvb_init+0x0/0x29 [cx88_dvb]
[   17.331275]  [<ffffffffa0cd1027>] dvb_init+0x27/0x29 [cx88_dvb]
[   17.331275]  [<ffffffff8100a04c>] do_one_initcall+0x3c/0x1a0
[   17.331275]  [<ffffffff810a62cf>] sys_init_module+0xdf/0x260
[   17.331275]  [<ffffffff81013232>] system_call_fastpath+0x16/0x1b
[   17.331275] Code: 66 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 53 48 83 ec 08 0f 1f 44 00 00 8b 35 74 bb 00 00 48 8b 9f 08 03 00 00 85 f6 75 64 <c7> 83 08 02 00 00 01 00 00 00 0f ae f0 48 8b bb f8 01 00 00 48 
[   17.331275] RIP  [<ffffffffa0eb890f>] dvb_frontend_stop+0x1f/0xb0 [dvb_core]
[   17.331275]  RSP <ffff88007a66bdc8>
[   17.331275] CR2: 0000000000000208
[   17.477138] ---[ end trace e392b7d8297b1e0c ]---
[   17.502604] CPU0 attaching NULL sched-domain.
[   17.502610] CPU1 attaching NULL sched-domain.
[   17.509177] CPU0 attaching sched-domain:
[   17.509181]  domain 0: span 0-1 level MC
[   17.509183]   groups: 0 1
[   17.509187] CPU1 attaching sched-domain:
[   17.509189]  domain 0: span 0-1 level MC
[   17.509191]   groups: 1 0
[   17.576351] Intel AES-NI instructions are not detected.
[   17.588813] padlock: VIA PadLock not detected.
[   17.605955] padlock: VIA PadLock Hash Engine not detected.
[   17.803231] Adding 6025208k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:6025208k 
[   19.468169] CPU0 attaching NULL sched-domain.
[   19.468176] CPU1 attaching NULL sched-domain.
[   19.482461] CPU0 attaching sched-domain:
[   19.482465]  domain 0: span 0-1 level MC
[   19.482467]   groups: 0 1
[   19.482473] CPU1 attaching sched-domain:
[   19.482474]  domain 0: span 0-1 level MC
[   19.482476]   groups: 1 0
[   42.110892] Valid eCryptfs headers not found in file header region or xattr region
[   42.110896] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   42.157057] Valid eCryptfs headers not found in file header region or xattr region
[   42.157062] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   45.111601] wlan0: direct probe to AP 00:1e:2a:20:7f:e8 (try 1)
[   45.111616] wlan0: deauthenticating from 00:1e:2a:20:7f:e8 by local choice (reason=3)
[   45.111636] wlan0: direct probe to AP 00:1e:2a:20:7f:e8 (try 1)
[   45.113456] wlan0: direct probe responded
[   45.113461] wlan0: authenticate with AP 00:1e:2a:20:7f:e8 (try 1)
[   45.116154] wlan0: authenticated
[   45.116175] wlan0: associate with AP 00:1e:2a:20:7f:e8 (try 1)
[   45.118911] wlan0: RX AssocResp from 00:1e:2a:20:7f:e8 (capab=0x471 status=0 aid=3)
[   45.118913] wlan0: associated
[   45.119345] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.565009] wlan0: no IPv6 routers present


hmmm just got an idea will report back in about 5-10 minutes to let you guys know how it does

any help would be appreciated

---

### Post by btdave on 2010-06-17
tried putting the firmware files into the <kernal_version> directory and no joy there either :(

again any help would be greatly appreciated :D

---

### Post by warrenc5 on 2010-06-18
firmware files only go in /lib/firmware

patch for tip and ubuntu Linux 2.6.32-22-generic #36-Ubuntu
config file goes in v4l/.config

dmesg -c 

[  542.862786] usb 1-1.1.2.3: USB disconnect, address 12
[  546.132336] usb 1-1.1.2.3: new high speed USB device using ehci_hcd and address 13
[  546.225138] usb 1-1.1.2.3: configuration #1 chosen from 1 choice
[  546.256283] dib0700: loaded with support for 14 different device-types
[  546.256459] dvb-usb: found a 'Pinnacle PCTV 340e HD Pro USB Stick' in cold state, will try to load a firmware
[  546.256465] usb 1-1.1.2.3: firmware: requesting dvb-usb-dib0700-1.20.fw
[  546.283426] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[  546.485569] dib0700: firmware started successfully.
[  546.988058] dvb-usb: found a 'Pinnacle PCTV 340e HD Pro USB Stick' in warm state.
[  546.988143] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  546.988577] DVB: registering new adapter (Pinnacle PCTV 340e HD Pro USB Stick)
[  547.812772] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[  547.823723] xc4000 3-0061: creating new instance
[  547.829041] xc4000: Successfully identified at address 0x61
[  547.829047] xc4000: Firmware has not been loaded previously
[  547.829053] Reading firmware dvb-fe-xc4000-1.4.1.fw
[  547.829060] usb 1-1.1.2.3: firmware: requesting dvb-fe-xc4000-1.4.1.fw
[  547.831041] Error: firmware dvb-fe-xc4000-1.4.1.fw not found.
[  547.831133] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2.3/input/input12
[  547.831208] dvb-usb: schedule remote query interval to 50 msecs.
[  547.831213] dvb-usb: Pinnacle PCTV 340e HD Pro USB Stick successfully initialized and connected.
[  547.831564] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by warrenc5 on 2010-06-18
attachments, have fun!

---

### Post by btdave on 2010-06-18
Cheers for that, 
It turns out however that my particular card has the XC3028 tuner in it, even though it states on the box that its a XC4000, this is what alerted me to it [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek)

Will for some fun give this a try and see if it picks it up.
Does your patch pick up that it needs to get the firmware? Doing it the way I tried it was just using firmware that it had already gotten from somewhere, no idea where though.

---

### Post by jonbonjovi on 2011-03-15
> **warrenc5 said:**
> attachments, have fun!

Could you please write a little How-to to make 340e device work? I get an error while compiling on Ubuntu 10.04.2 32 bit with 2.6.32.29 kernel. Thanx man!

---

