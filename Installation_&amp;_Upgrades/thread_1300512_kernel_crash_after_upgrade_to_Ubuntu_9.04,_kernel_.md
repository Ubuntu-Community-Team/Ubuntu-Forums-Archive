---
title: "kernel crash after upgrade to Ubuntu 9.04, kernel 2.6.28-16-generic"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by dreamingdarkness on 2009-10-25
The title mostly describes the issue.
I've noticed some problems with connectivity via wi-fi on my Ubuntu machine, but not on either Windows box in my house, since upgrading to 2.6.28-15-generic. 

While trying to diagnose this, which continued after the move to kernel 2.6.28-16-generic, I typically run pings constantly between the laptop and the router, cable modem, and an external site (ISP or google.com). During this, I managed to lock up. I first noticed one of my pings would not abort (ctrl-c) for a few minutes before it finally accepted the abort, though suspend (ctrl-z) did work. 

Two other command prompt windows were also running pings, and when I tried to abort the processes there they locked completely. Attempting to close the terminal window caused a full hard lock up of the PC.

Syslog/kernel log data as follows below.
Any thoughts on this? Or should I push it upstream to launchpad to report it to kernel maintainers?

```
Kernel error:

Oct 25 00:41:59 secondary kernel: [ 4922.868489] BUG: unable to handle kernel paging request at 0000000000008928
Oct 25 00:41:59 secondary kernel: [ 4922.868495] IP: [<ffffffff802e5837>] filp_close+0x17/0x90
Oct 25 00:41:59 secondary kernel: [ 4922.868503] PGD 0 
Oct 25 00:41:59 secondary kernel: [ 4922.868505] Oops: 0000 [#1] SMP 
Oct 25 00:41:59 secondary kernel: [ 4922.868508] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Oct 25 00:41:59 secondary kernel: [ 4922.868510] Dumping ftrace buffer:
Oct 25 00:41:59 secondary kernel: [ 4922.868512]    (ftrace buffer empty)
Oct 25 00:41:59 secondary kernel: [ 4922.868514] CPU 1 
Oct 25 00:41:59 secondary kernel: [ 4922.868515] Modules linked in: aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb snd_seq_oss snd_seq_midi snd_rawmidi iwlagn iwlcore snd_seq_midi_event snd_seq video snd_timer uvcvideo mac80211 sdhci_pci psmouse snd_seq_device compat_ioctl32 videodev iTCO_wdt asus_laptop pcspkr ricoh_mmc sdhci output serio_raw v4l1_compat iTCO_vendor_support intel_agp led_class joydev snd soundcore snd_page_alloc cfg80211 nvidia(P) usbhid ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Oct 25 00:41:59 secondary kernel: [ 4922.868550] Pid: 15413, comm: ping Tainted: P           2.6.28-16-generic #55-Ubuntu
Oct 25 00:41:59 secondary kernel: [ 4922.868552] RIP: 0010:[<ffffffff802e5837>]  [<ffffffff802e5837>] filp_close+0x17/0x90
Oct 25 00:41:59 secondary kernel: [ 4922.868555] RSP: 0018:ffff88011619fe68  EFLAGS: 00010282
Oct 25 00:41:59 secondary kernel: [ 4922.868557] RAX: ffff880132ce5800 RBX: 0000000000008900 RCX: ffffffff802c9793
Oct 25 00:41:59 secondary kernel: [ 4922.868558] RDX: 0000000000000000 RSI: ffff88011624f900 RDI: 0000000000008900
Oct 25 00:41:59 secondary kernel: [ 4922.868560] RBP: ffff88011619fe88 R08: ffff88011624f900 R09: ffff880028102300
Oct 25 00:41:59 secondary kernel: [ 4922.868561] R10: 0000000000000002 R11: 0000000000000000 R12: 0000000000000000
Oct 25 00:41:59 secondary kernel: [ 4922.868563] R13: ffff880122488380 R14: 0000000000000000 R15: 0000000000000000
Oct 25 00:41:59 secondary kernel: [ 4922.868565] FS:  0000000000000000(0000) GS:ffff88013f803a80(0000) knlGS:0000000000000000
Oct 25 00:41:59 secondary kernel: [ 4922.868567] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 25 00:41:59 secondary kernel: [ 4922.868568] CR2: 0000000000008928 CR3: 0000000000201000 CR4: 00000000000006a0
Oct 25 00:41:59 secondary kernel: [ 4922.868570] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 25 00:41:59 secondary kernel: [ 4922.868572] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 25 00:41:59 secondary kernel: [ 4922.868574] Process ping (pid: 15413, threadinfo ffff88011619e000, task ffff88012014c320)
Oct 25 00:41:59 secondary kernel: [ 4922.868576] Stack:
Oct 25 00:41:59 secondary kernel: [ 4922.868577]  0000000000000282 000000000000000f 0000000000000000 ffff880122488380
Oct 25 00:41:59 secondary kernel: [ 4922.868580]  ffff88011619fec8 ffffffff8025325d ffff88011624f900 ffff88012014c914
Oct 25 00:41:59 secondary kernel: [ 4922.868583]  ffff88012014c320 ffff88011624f900 0000000000000003 ffff88012014c918
Oct 25 00:41:59 secondary kernel: [ 4922.868586] Call Trace:
Oct 25 00:41:59 secondary kernel: [ 4922.868588]  [<ffffffff8025325d>] put_files_struct+0x7d/0xe0
Oct 25 00:41:59 secondary kernel: [ 4922.868592]  [<ffffffff8025330f>] exit_files+0x4f/0x60
Oct 25 00:41:59 secondary kernel: [ 4922.868595]  [<ffffffff802550d1>] do_exit+0x1b1/0x3b0
Oct 25 00:41:59 secondary kernel: [ 4922.868598]  [<ffffffff80255312>] do_group_exit+0x42/0xc0
Oct 25 00:41:59 secondary kernel: [ 4922.868601]  [<ffffffff802553a2>] sys_exit_group+0x12/0x20
Oct 25 00:41:59 secondary kernel: [ 4922.868603]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Oct 25 00:41:59 secondary kernel: [ 4922.868606] Code: c8 e8 7e 9d f4 ff 90 5b 41 5c 41 5d 41 5e c9 c3 0f 0b eb fe 55 48 89 e5 48 83 ec 20 48 89 5d e8 4c 89 65 f0 48 89 fb 4c 89 6d f8 <48> 83 7f 28 00 49 89 f4 74 54 48 8b 47 20 48 85 c0 74 46 48 8b 
Oct 25 00:41:59 secondary kernel: [ 4922.868632] RIP  [<ffffffff802e5837>] filp_close+0x17/0x90
Oct 25 00:41:59 secondary kernel: [ 4922.868635]  RSP <ffff88011619fe68>
Oct 25 00:41:59 secondary kernel: [ 4922.868636] CR2: 0000000000008928
Oct 25 00:41:59 secondary kernel: [ 4922.868638] ---[ end trace 69c105209ecadf78 ]---
Oct 25 00:41:59 secondary kernel: [ 4922.868640] Fixing recursive fault but reboot is needed!
Oct 25 00:42:44 secondary kernel: [ 4967.516798] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Oct 25 00:42:44 secondary kernel: [ 4967.516804] IP: [<ffffffff80268e92>] add_wait_queue+0x32/0x60
Oct 25 00:42:44 secondary kernel: [ 4967.516811] PGD 11f515067 PUD 11f514067 PMD 0 
Oct 25 00:42:44 secondary kernel: [ 4967.516814] Oops: 0002 [#2] SMP 
Oct 25 00:42:44 secondary kernel: [ 4967.516817] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Oct 25 00:42:44 secondary kernel: [ 4967.516819] CPU 1 
Oct 25 00:42:44 secondary kernel: [ 4967.516821] Modules linked in: aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb snd_seq_oss snd_seq_midi snd_rawmidi iwlagn iwlcore snd_seq_midi_event snd_seq video snd_timer uvcvideo mac80211 sdhci_pci psmouse snd_seq_device compat_ioctl32 videodev iTCO_wdt asus_laptop pcspkr ricoh_mmc sdhci output serio_raw v4l1_compat iTCO_vendor_support intel_agp led_class joydev snd soundcore snd_page_alloc cfg80211 nvidia(P) usbhid ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Oct 25 00:42:44 secondary kernel: [ 4967.516852] Pid: 6277, comm: gnome-terminal Tainted: P      D    2.6.28-16-generic #55-Ubuntu
Oct 25 00:42:44 secondary kernel: [ 4967.516854] RIP: 0010:[<ffffffff80268e92>]  [<ffffffff80268e92>] add_wait_queue+0x32/0x60
Oct 25 00:42:44 secondary kernel: [ 4967.516857] RSP: 0018:ffff88011d5afaa8  EFLAGS: 00010046
Oct 25 00:42:44 secondary kernel: [ 4967.516858] RAX: 0000000000000000 RBX: ffff88011d5afbd8 RCX: 0000000000000000
Oct 25 00:42:44 secondary kernel: [ 4967.516860] RDX: ffff88011d5afbf0 RSI: 0000000000000286 RDI: ffff880131d28800
Oct 25 00:42:44 secondary kernel: [ 4967.516861] RBP: ffff88011d5afab8 R08: 0000000000000001 R09: ffff8801201299e8
Oct 25 00:42:44 secondary kernel: [ 4967.516863] R10: 0000000000000001 R11: 0000000000000202 R12: ffff880131d28800
Oct 25 00:42:44 secondary kernel: [ 4967.516864] R13: ffff8801201299c0 R14: ffff880131d28800 R15: ffff88011d5afe34
Oct 25 00:42:44 secondary kernel: [ 4967.516866] FS:  00007fb6ae7197d0(0000) GS:ffff88013f803a80(0000) knlGS:0000000000000000
Oct 25 00:42:44 secondary kernel: [ 4967.516868] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 25 00:42:44 secondary kernel: [ 4967.516870] CR2: 0000000000000008 CR3: 000000011d436000 CR4: 00000000000006a0
Oct 25 00:42:44 secondary kernel: [ 4967.516871] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 25 00:42:44 secondary kernel: [ 4967.516873] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 25 00:42:44 secondary kernel: [ 4967.516875] Process gnome-terminal (pid: 6277, threadinfo ffff88011d5ae000, task ffff88012014d980)
Oct 25 00:42:44 secondary kernel: [ 4967.516876] Stack:
Oct 25 00:42:44 secondary kernel: [ 4967.516877]  0000000000000000 ffff88011d5afbb8 ffff88011d5afae8 ffffffff802f87d8
Oct 25 00:42:44 secondary kernel: [ 4967.516880]  ffff880131d28800 ffff8801201299c0 ffff8801201299c0 0000000000000000
Oct 25 00:42:44 secondary kernel: [ 4967.516883]  ffff88011d5afb08 ffffffff802eeaee ffff88011d5afbb8 ffff88011d5afe14
Oct 25 00:42:44 secondary kernel: [ 4967.516886] Call Trace:
Oct 25 00:42:44 secondary kernel: [ 4967.516888]  [<ffffffff802f87d8>] __pollwait+0x88/0x120
Oct 25 00:42:44 secondary kernel: [ 4967.516891]  [<ffffffff802eeaee>] pipe_poll+0x2e/0xa0
Oct 25 00:42:44 secondary kernel: [ 4967.516894]  [<ffffffff802f7829>] do_poll+0xe9/0x280
Oct 25 00:42:44 secondary kernel: [ 4967.516896]  [<ffffffff802f7cf4>] do_sys_poll+0x134/0x200
Oct 25 00:42:44 secondary kernel: [ 4967.516899]  [<ffffffff802f8750>] ? __pollwait+0x0/0x120
Oct 25 00:42:44 secondary kernel: [ 4967.516901]  [<ffffffff8024a6f0>] ? default_wake_function+0x0/0x10
Oct 25 00:42:44 secondary kernel: [ 4967.516904]  [<ffffffff805a2338>] ? __sock_sendmsg+0x68/0x80
Oct 25 00:42:44 secondary kernel: [ 4967.516908]  [<ffffffff805a2454>] ? sock_aio_write+0x104/0x120
Oct 25 00:42:44 secondary kernel: [ 4967.516910]  [<ffffffff8069b9f9>] ? _spin_lock+0x9/0x10
Oct 25 00:42:44 secondary kernel: [ 4967.516914]  [<ffffffff805a2350>] ? sock_aio_write+0x0/0x120
Oct 25 00:42:44 secondary kernel: [ 4967.516917]  [<ffffffff802e7a2b>] ? do_sync_readv_writev+0xeb/0x130
Oct 25 00:42:44 secondary kernel: [ 4967.516920]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Oct 25 00:42:44 secondary kernel: [ 4967.516923]  [<ffffffff80268af0>] ? autoremove_wake_function+0x0/0x40
Oct 25 00:42:44 secondary kernel: [ 4967.516926]  [<ffffffff8069b9f9>] ? _spin_lock+0x9/0x10
Oct 25 00:42:44 secondary kernel: [ 4967.516928]  [<ffffffff8041cd65>] ? rb_erase+0xe5/0x170
Oct 25 00:42:44 secondary kernel: [ 4967.516931]  [<ffffffff802105d0>] ? __switch_to+0x1b0/0x490
Oct 25 00:42:44 secondary kernel: [ 4967.516935]  [<ffffffff8024662b>] ? finish_task_switch+0x2b/0xf0
Oct 25 00:42:44 secondary kernel: [ 4967.516937]  [<ffffffff806999ec>] ? thread_return+0x37/0x36b
Oct 25 00:42:44 secondary kernel: [ 4967.516940]  [<ffffffff802f7fb7>] sys_poll+0x77/0x110
Oct 25 00:42:44 secondary kernel: [ 4967.516942]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Oct 25 00:42:44 secondary kernel: [ 4967.516945] Code: 10 48 89 1c 24 4c 89 64 24 08 49 89 fc 83 26 fe 48 89 f3 e8 21 2a 43 00 48 89 c6 49 8b 44 24 08 48 8d 53 18 4c 89 e7 48 89 43 18 <48> 89 50 08 49 8d 44 24 08 49 89 54 24 08 48 89 43 20 e8 a7 2b 
Oct 25 00:42:44 secondary kernel: [ 4967.516969] RIP  [<ffffffff80268e92>] add_wait_queue+0x32/0x60
Oct 25 00:42:44 secondary kernel: [ 4967.516971]  RSP <ffff88011d5afaa8>
Oct 25 00:42:44 secondary kernel: [ 4967.516973] CR2: 0000000000000008
Oct 25 00:42:44 secondary kernel: [ 4967.516975] ---[ end trace 69c105209ecadf78 ]---
```

---

