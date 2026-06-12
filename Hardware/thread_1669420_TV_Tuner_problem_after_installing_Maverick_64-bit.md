---
title: "TV Tuner problem after installing Maverick 64-bit"
date: 2011-01-17
forum: Hardware
---

### Post by Is Mise on 2011-01-17
After installing Ubuntu 10.10 64-bit (I was using 10.04 32-bit before) my Hauppage HVR-1250 TV Tuner no longer works. Scanning for channels in Me-TV causes the program to freeze halfway through, and scanning using 'scan' from dvb-apps also freezes halfway.

Here's the output from scan:
```
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB
service is running. Channel number: 5:1. Name: 'CBC Toronto High Definition Television'
>>> tune to: 515028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 551028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 551028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb

```

And here's the relevant dmesg error output:
```
[  219.827050] BUG: unable to handle kernel paging request at 0000010100000028
[  219.827064] IP: [<ffffffffa004f563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
[  219.827085] PGD 0 
[  219.827091] Oops: 0000 [#1] SMP 
[  219.827096] last sysfs file: /sys/devices/pci0000:00/0000:00:11.0/host2/target2:0:0/2:0:0:0/block/sda/sda7/uevent
[  219.827104] CPU 0 
[  219.827107] Modules linked in: nls_utf8 udf parport_pc ppdev snd_hda_codec_nvhdmi binfmt_misc arc4 nvidia(P) ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state mt2131 s5h1409 snd_hda_codec_realtek ip6table_filter ip6_tables snd_hda_intel nf_nat_irc ir_lirc_codec lirc_dev snd_hda_codec nf_conntrack_irc snd_usb_audio nf_nat_ftp nf_nat ir_sony_decoder snd_pcm nf_conntrack_ipv4 ath5k ir_jvc_decoder nf_defrag_ipv4 snd_hwdep snd_usbmidi_lib ir_rc6_decoder nf_conntrack_ftp snd_seq_midi snd_seq_midi_event ir_rc5_decoder nf_conntrack cx23885 mac80211 snd_seq ir_nec_decoder ath iptable_filter snd_rawmidi ir_core snd_timer cx2341x uvcvideo ip_tables cfg80211 v4l2_common snd_seq_device videobuf_dma_sg edac_core videodev v4l1_compat psmouse videobuf_dvb x_tables v4l2_compat_ioctl32 serio_raw led_class edac_mce_amd k8temp snd soundcore dvb_core videobuf_core btcx_risc i2c_piix4 tveeprom snd_page_alloc lp parport usb_storage firewire_ohci ahci firewire_core pata_atiixp sky2 crc_itu_t libahci
[  219.827222] 
[  219.827230] Pid: 2189, comm: cx23885[0] dvb Tainted: P            2.6.35-24-generic #42-Ubuntu RS740DVF/Aspire M1201
[  219.827236] RIP: 0010:[<ffffffffa004f563>]  [<ffffffffa004f563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
[  219.827250] RSP: 0018:ffff880026953dc0  EFLAGS: 00010246
[  219.827255] RAX: 0000010100000000 RBX: ffff88001bd21ef8 RCX: 0000000000000002
[  219.827260] RDX: 0000000000000006 RSI: ffffc900001fe000 RDI: ffff88003e7880a0
[  219.827265] RBP: ffff880026953dd0 R08: ffff880026952000 R09: 00000000ffffffff
[  219.827270] R10: 00000000ffffffff R11: 0000000000000001 R12: ffff88002f8cf028
[  219.827275] R13: ffff88001bd21ef8 R14: ffff88002f8cf028 R15: ffff8800181716e0
[  219.827281] FS:  00007f46030f5840(0000) GS:ffff880001e00000(0000) knlGS:0000000000000000
[  219.827287] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  219.827292] CR2: 0000010100000028 CR3: 00000000256eb000 CR4: 00000000000006f0
[  219.827297] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  219.827303] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  219.827309] Process cx23885[0] dvb (pid: 2189, threadinfo ffff880026952000, task ffff8800181716e0)
[  219.827313] Stack:
[  219.827316]  ffff88001bd21ef8 ffff88001bd21e00 ffff880026953e00 ffffffffa0b9512a
[  219.827324] <0> ffff880026953df0 ffff88002f8cf028 ffff88002f8cf028 ffff88002f8cf128
[  219.827333] <0> ffff880026953e10 ffffffffa0b96d5e ffff880026953e40 ffffffffa00b6457
[  219.827342] Call Trace:
[  219.827368]  [<ffffffffa0b9512a>] cx23885_free_buffer+0x5a/0xa0 [cx23885]
[  219.827385]  [<ffffffffa0b96d5e>] dvb_buf_release+0xe/0x10 [cx23885]
[  219.827400]  [<ffffffffa00b6457>] videobuf_queue_cancel+0xf7/0x120 [videobuf_core]
[  219.827413]  [<ffffffffa00b64e7>] __videobuf_read_stop+0x17/0x70 [videobuf_core]
[  219.827425]  [<ffffffffa00b655e>] videobuf_read_stop+0x1e/0x30 [videobuf_core]
[  219.827437]  [<ffffffffa00e68c8>] videobuf_dvb_thread+0x168/0x1e0 [videobuf_dvb]
[  219.827448]  [<ffffffffa00e6760>] ? videobuf_dvb_thread+0x0/0x1e0 [videobuf_dvb]
[  219.827460]  [<ffffffff8107f1d6>] kthread+0x96/0xa0
[  219.827469]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[  219.827476]  [<ffffffff8107f140>] ? kthread+0x0/0xa0
[  219.827482]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[  219.827486] Code: 19 75 6e 8b 53 28 85 d2 74 4b 48 8b 7f 28 8b 4b 30 48 8b 73 20 48 85 ff 74 4e 48 8b 87 e8 01 00 00 48 85 c0 74 42 83 f9 02 77 5d <48> 8b 40 28 48 85 c0 74 0a 45 31 c0 90 ff d0 48 8b 73 20 48 89 
[  219.827546] RIP  [<ffffffffa004f563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
[  219.827557]  RSP <ffff880026953dc0>
[  219.827560] CR2: 0000010100000028
[  219.827566] ---[ end trace 5a971cb9e524eb81 ]---

```

---

### Post by substorm on 2011-01-18
Hi.  I think I have a solution to your problem.  I've been trying to get my Hauppauge-1250 TV Tuner to work with Mythbuntu 10.10.  Whenever I tried to to run a channel scan, the system would freeze in the manner you describe.  When I started working on the problem, I was running Kernel Version 2.6.35-22-generic.  I then followed the instructions at [http://ubuntuforums.org/showthread.php?t=1648472](http://ubuntuforums.org/showthread.php?t=1648472) and I was able to make things work.

My system then did an automatic upgrade to Kernel 2.6.35-24-generic, and things started freezing again.  I finally figured out that if I rollback to the old kernel version, things worked fine.

I hope that helps you.

Good luck!

---

### Post by Is Mise on 2011-01-18
Thanks! That's great! It's working perfect for me now.

I didn't need to change anything in 'cx23885-cards.c' though since it was already set to the right number, so I guess it must just be some sort of bug in the version they used to build the driver for 10.10.

My system was already using the 2.6.35-24 kernel, so I tried installing it on that, and it works fine. I bet if you just repeat the 'sudo make install' step while booted into 2.6.35-24 you should get it working on there too.

---

### Post by substorm on 2011-01-18
Great!  I'm glad it worked.  I actually tried recompiling the driver 3 or 4 times after the new kernel install, and even did a "make clean" and a new "make config".  I'm not sure why it wouldn't work for me, but I'm happy for now.  Maybe in the future I'll give the new kernel a try again.

Take care.

---

### Post by substorm on 2011-01-18
Great!  I'm glad it worked.  I actually tried recompiling the driver 3 or 4 times after the new kernel install, and even did a "make clean" and a new "make config".  I'm not sure why it wouldn't work for me, but I'm happy for now.  Maybe in the future I'll give the new kernel a try again.

Take care.

---

### Post by substorm on 2011-01-18
Great!  I'm glad it worked.  I actually tried recompiling the driver 3 or 4 times after the new kernel install, and even did a "make clean" and a new "make config".  I'm not sure why it wouldn't work for me, but I'm happy for now.  Maybe in the future I'll give the new kernel a try again.

Take care.

---

