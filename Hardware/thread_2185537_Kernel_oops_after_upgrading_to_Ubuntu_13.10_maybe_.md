---
title: "Kernel oops after upgrading to Ubuntu 13.10 maybe related to ethernet adapter?"
date: 2013-11-03
forum: Hardware
---

### Post by christoph-scholz on 2013-11-03
After updating my machine from Ubuntu 13.04 to Ubuntu 13.10 a few days ago I see kernel oops'es after booting up the machine about every 2 out of 3 tries. The machine then seems to be completely locked up (showing different slightly distorted splash screens) and needs to be hard rebooted (i.e. by long pressing of the power button).


It will work perfectly fine and absolutely reliably if the machine comes up cleanly (about 1 out of 3 boots).


I am using a desktop computer FUJITSU SIEMENS ESPRIMO E5730.


From the stack trace (see below) i guess it could be related to my onboard ethernet module: Intel Corporation 82567LF-3 Gigabit Network. But not sure about this.


I did not experience similar problems with Ubuntu 13.04.

Any hints as how this could be resolved or further investigated would be appreciated.




Cheers


Christoph


```
Nov  3 10:49:06 kurtz kernel: [   15.268020] BUG: unable to handle kernel paging request at fffffffffffffff8
Nov  3 10:49:06 kurtz kernel: [   15.268092] IP: [<ffffffff813602fb>] plist_add+0x5b/0xe0
Nov  3 10:49:06 kurtz kernel: [   15.268142] PGD 1c11067 PUD 1c13067 PMD 0 
Nov  3 10:49:06 kurtz kernel: [   15.268224] Oops: 0000 [#1] SMP 
Nov  3 10:49:06 kurtz kernel: [   15.268285] Modules linked in: dib8000 dib7000m dib0090 dib0070 dib7000p dib3000mc dibx000_common dvb_usb dvb_core rc_core joydev(F) snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) microcode(F+) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) psmouse(F) serio_raw(F) snd(F) lpc_ich soundcore(F) mei_me mei parport_pc(F) tpm_tis i915 mac_hid video(F) drm_kms_helper drm i2c_algo_bit lp(F) parport(F) hid_logitech ff_memless floppy(F) usbhid hid e1000e(F) ptp(F) pps_core(F)
Nov  3 10:49:06 kurtz kernel: [   15.269385] CPU: 0 PID: 396 Comm: ip Tainted: GF            3.11.0-12-generic #19-Ubuntu
Nov  3 10:49:06 kurtz kernel: [   15.269441] Hardware name: FUJITSU SIEMENS ESPRIMO E5730                 /D2824-A1, BIOS 6.00 R1.19.2824.A1               11/05/2009
Nov  3 10:49:06 kurtz kernel: [   15.269503] task: ffff8800cd862ee0 ti: ffff8800cda4e000 task.ti: ffff8800cda4e000
Nov  3 10:49:06 kurtz kernel: [   15.269558] RIP: 0010:[<ffffffff813602fb>]  [<ffffffff813602fb>] plist_add+0x5b/0xe0
Nov  3 10:49:06 kurtz kernel: [   15.269633] RSP: 0018:ffff8800cda4f6c0  EFLAGS: 00010083
Nov  3 10:49:06 kurtz kernel: [   15.269672] RAX: fffffffffffffff8 RBX: ffff8801042b4750 RCX: 0000000077359400
Nov  3 10:49:06 kurtz kernel: [   15.269715] RDX: fffffffffffffff8 RSI: ffff8800ce5b9d68 RDI: 0000000000000000
Nov  3 10:49:06 kurtz kernel: [   15.269757] RBP: ffff8800cda4f6e8 R08: ffff8800ce5b9d68 R09: 000000000000000f
Nov  3 10:49:06 kurtz kernel: [   15.269800] R10: 0000000000000001 R11: 0000000000000000 R12: ffffffff81c4aea0
Nov  3 10:49:06 kurtz kernel: [   15.269842] R13: ffff8801042b4768 R14: ffffffff81c4aea0 R15: ffff8801042b4758
Nov  3 10:49:06 kurtz kernel: [   15.269885] FS:  00007f3e47b93740(0000) GS:ffff88010dc00000(0000) knlGS:0000000000000000
Nov  3 10:49:06 kurtz kernel: [   15.269942] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  3 10:49:06 kurtz kernel: [   15.269982] CR2: fffffffffffffff8 CR3: 00000000cda7e000 CR4: 00000000000407f0
Nov  3 10:49:06 kurtz kernel: [   15.270024] Stack:
Nov  3 10:49:06 kurtz kernel: [   15.270058]  ffff8801042b4750 ffffffff81c4aea0 0000000000000000 0000000077359400
Nov  3 10:49:06 kurtz kernel: [   15.270185]  0000000000000000 ffff8800cda4f728 ffffffff810a8c45 0000000000000292
Nov  3 10:49:06 kurtz kernel: [   15.270313]  ffff8801042b4000 ffff8801042b4750 0000000000000001 00000000ffffffff
Nov  3 10:49:06 kurtz kernel: [   15.270440] Call Trace:
Nov  3 10:49:06 kurtz kernel: [   15.270478]  [<ffffffff810a8c45>] pm_qos_update_target+0x125/0x1d0
Nov  3 10:49:06 kurtz kernel: [   15.270520]  [<ffffffff810a8d83>] pm_qos_add_request+0x93/0x100
Nov  3 10:49:06 kurtz kernel: [   15.270571]  [<ffffffffa00398e4>] e1000_open+0xe4/0x5b0 [e1000e]
Nov  3 10:49:06 kurtz kernel: [   15.270613]  [<ffffffff8108a006>] ? raw_notifier_call_chain+0x16/0x20
Nov  3 10:49:06 kurtz kernel: [   15.270657]  [<ffffffff815f12df>] __dev_open+0xbf/0x140
Nov  3 10:49:06 kurtz kernel: [   15.270697]  [<ffffffff815f15a2>] __dev_change_flags+0x92/0x170
Nov  3 10:49:06 kurtz kernel: [   15.270738]  [<ffffffff815f172d>] dev_change_flags+0x1d/0x60
Nov  3 10:49:06 kurtz kernel: [   15.270780]  [<ffffffff815febd2>] do_setlink+0x332/0x9f0
Nov  3 10:49:06 kurtz kernel: [   15.270822]  [<ffffffff8137cc52>] ? nla_parse+0x32/0xe0
Nov  3 10:49:06 kurtz kernel: [   15.270862]  [<ffffffff815ffef4>] rtnl_newlink+0x394/0x5e0
Nov  3 10:49:06 kurtz kernel: [   15.270904]  [<ffffffff8114110c>] ? filemap_fault+0xac/0x400
Nov  3 10:49:06 kurtz kernel: [   15.270946]  [<ffffffff81316c04>] ? apparmor_capable+0x24/0xe0
Nov  3 10:49:06 kurtz kernel: [   15.270987]  [<ffffffff815fc9b9>] rtnetlink_rcv_msg+0x99/0x260
Nov  3 10:49:06 kurtz kernel: [   15.271029]  [<ffffffff81190848>] ? __kmalloc_node_track_caller+0x58/0x1d0
Nov  3 10:49:06 kurtz kernel: [   15.271072]  [<ffffffff815e013e>] ? __alloc_skb+0x7e/0x2a0
Nov  3 10:49:06 kurtz kernel: [   15.271113]  [<ffffffff815fc920>] ? rtnetlink_rcv+0x30/0x30
Nov  3 10:49:06 kurtz kernel: [   15.271154]  [<ffffffff8161a809>] netlink_rcv_skb+0xa9/0xc0
Nov  3 10:49:06 kurtz kernel: [   15.271195]  [<ffffffff815fc918>] rtnetlink_rcv+0x28/0x30
Nov  3 10:49:06 kurtz kernel: [   15.271235]  [<ffffffff81619e5d>] netlink_unicast+0xdd/0x190
Nov  3 10:49:06 kurtz kernel: [   15.271276]  [<ffffffff8136d77d>] ? memcpy_fromiovec+0x4d/0x90
Nov  3 10:49:06 kurtz kernel: [   15.271317]  [<ffffffff8161a20f>] netlink_sendmsg+0x2ff/0x740
Nov  3 10:49:06 kurtz kernel: [   15.271359]  [<ffffffff815d7c69>] sock_sendmsg+0x99/0xd0
Nov  3 10:49:06 kurtz kernel: [   15.271399]  [<ffffffff815d805c>] ___sys_sendmsg+0x36c/0x380
Nov  3 10:49:06 kurtz kernel: [   15.271443]  [<ffffffff81167fd9>] ? handle_mm_fault+0x299/0x670
Nov  3 10:49:06 kurtz kernel: [   15.271486]  [<ffffffff816f06a4>] ? __do_page_fault+0x204/0x540
Nov  3 10:49:06 kurtz kernel: [   15.271528]  [<ffffffff811bb4ef>] ? __d_free+0x3f/0x60
Nov  3 10:49:06 kurtz kernel: [   15.271568]  [<ffffffff8108c8da>] ? lg_local_unlock+0x1a/0x20
Nov  3 10:49:06 kurtz kernel: [   15.271609]  [<ffffffff811c53ee>] ? mntput_no_expire+0x3e/0x150
Nov  3 10:49:06 kurtz kernel: [   15.271650]  [<ffffffff811c5526>] ? mntput+0x26/0x40
Nov  3 10:49:06 kurtz kernel: [   15.271691]  [<ffffffff811a880c>] ? __fput+0x16c/0x230
Nov  3 10:49:06 kurtz kernel: [   15.271731]  [<ffffffff815d8e42>] __sys_sendmsg+0x42/0x80
Nov  3 10:49:06 kurtz kernel: [   15.271771]  [<ffffffff815d8e92>] SyS_sendmsg+0x12/0x20
Nov  3 10:49:06 kurtz kernel: [   15.271811]  [<ffffffff816f521d>] system_call_fastpath+0x1a/0x1f
Nov  3 10:49:06 kurtz kernel: [   15.271852] Code: 36 49 39 f6 74 53 48 83 ee 18 8b 0b 45 31 c0 48 89 f0 eb 17 0f 1f 40 00 48 8b 78 08 48 8d 57 f8 48 39 d6 74 14 49 89 c0 48 89 d0 <39> 08 7e e9 4c 8d 60 18 48 89 c2 4c 89 c0 48 85 c0 74 04 39 08 
Nov  3 10:49:06 kurtz kernel: [   15.272007] RIP  [<ffffffff813602fb>] plist_add+0x5b/0xe0
Nov  3 10:49:06 kurtz kernel: [   15.272007]  RSP <ffff8800cda4f6c0>
Nov  3 10:49:06 kurtz kernel: [   15.272007] CR2: fffffffffffffff8
Nov  3 10:49:06 kurtz kernel: [   15.272007] ---[ end trace ed308e2955d06325 ]---

```

---

