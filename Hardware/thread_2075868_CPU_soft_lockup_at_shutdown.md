---
title: "CPU soft lockup at shutdown"
date: 2012-10-24
forum: Hardware
---

### Post by CSNate on 2012-10-24
Hello all, I have just upgraded to Ubuntu 12.10.  I am having at issue at shutdown.  The kernel seems to lockup for some reason and lists all kernel modules?  Here is a snippet from my system log.  This happens only at shutdown or halt.

My computer is a Dell Studio 1569.

```

GLADOS kernel: [11130.116542] BUG: soft lockup - CPU#2 stuck for 22s! [kworker/2:1:12579]
Oct 22 17:42:57 GLADOS kernel: [11130.116549] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xts gf128mul dm_crypt joydev parport_pc bnep ppdev rfcomm bluetooth ext2 arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi dell_laptop snd_hda_codec_realtek dcdbas coretemp kvm_intel kvm microcode snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi serio_raw intel_ips snd_seq_midi_event lpc_ich snd_seq snd_timer snd_seq_device iwlwifi mac80211 snd cfg80211 uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops soundcore snd_page_alloc mei mac_hid lp parport hid_generic usbhid hid i915 r8169 drm_kms_helper drm i2c_algo_bit wmi video
Oct 22 17:42:57 GLADOS kernel: [11130.116639] CPU 2 
Oct 22 17:42:57 GLADOS kernel: [11130.116641] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xts gf128mul dm_crypt joydev parport_pc bnep ppdev rfcomm bluetooth ext2 arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi dell_laptop snd_hda_codec_realtek dcdbas coretemp kvm_intel kvm microcode snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi serio_raw intel_ips snd_seq_midi_event lpc_ich snd_seq snd_timer snd_seq_device iwlwifi mac80211 snd cfg80211 uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops soundcore snd_page_alloc mei mac_hid lp parport hid_generic usbhid hid i915 r8169 drm_kms_helper drm i2c_algo_bit wmi video
Oct 22 17:42:57 GLADOS kernel: [11130.116698] 
Oct 22 17:42:57 GLADOS kernel: [11130.116701] Pid: 12579, comm: kworker/2:1 Tainted: G        W  O 3.5.0-17-generic #28-Ubuntu Dell Inc. Studio 1569/0R225F
Oct 22 17:42:57 GLADOS kernel: [11130.116707] RIP: 0010:[<ffffffff8105a770>]  [<ffffffff8105a770>] __do_softirq+0x60/0x1d0
Oct 22 17:42:57 GLADOS kernel: [11130.116718] RSP: 0018:ffff88023bd03ee0  EFLAGS: 00000206
Oct 22 17:42:57 GLADOS kernel: [11130.116721] RAX: ffff88010a623fd8 RBX: 0000000000000001 RCX: 0000000000000020
Oct 22 17:42:57 GLADOS kernel: [11130.116724] RDX: 0000000000000002 RSI: 000000000000000e RDI: 0000000000000380
Oct 22 17:42:57 GLADOS kernel: [11130.116726] RBP: ffff88023bd03f40 R08: 00000a248cb87800 R09: ffffffff81e4ca00
Oct 22 17:42:57 GLADOS kernel: [11130.116728] R10: 0000000000000800 R11: 0000000000000000 R12: ffff88023bd03e58
Oct 22 17:42:57 GLADOS kernel: [11130.116731] R13: ffffffff8168a7ca R14: ffff88023bd03f40 R15: 0000000000000046
Oct 22 17:42:57 GLADOS kernel: [11130.116734] FS:  0000000000000000(0000) GS:ffff88023bd00000(0000) knlGS:0000000000000000
Oct 22 17:42:57 GLADOS kernel: [11130.116737] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 22 17:42:57 GLADOS kernel: [11130.116739] CR2: 00007f987e7d9000 CR3: 0000000001c0b000 CR4: 00000000000007e0
Oct 22 17:42:57 GLADOS kernel: [11130.116742] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 22 17:42:57 GLADOS kernel: [11130.116744] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 22 17:42:57 GLADOS kernel: [11130.116747] Process kworker/2:1 (pid: 12579, threadinfo ffff88010a622000, task ffff8801d3f01700)
Oct 22 17:42:57 GLADOS kernel: [11130.116749] Stack:
Oct 22 17:42:57 GLADOS kernel: [11130.116751]  ffffffff810a7c16 000000020a623fd8 ffff88010a623fd8 ffff88010a623fd8
Oct 22 17:42:57 GLADOS kernel: [11130.116757]  000000000000000a ffff88023bd03f18 ffffffff810a9164 ffff88010a623fd8
Oct 22 17:42:57 GLADOS kernel: [11130.116762]  0000000000000046 ffff88022e51a000 ffff88023bd0e400 ffff8801d3f01700
Oct 22 17:42:57 GLADOS kernel: [11130.116767] Call Trace:
Oct 22 17:42:57 GLADOS kernel: [11130.116770]  <IRQ> 
Oct 22 17:42:57 GLADOS kernel: [11130.116772]  [<ffffffff810a7c16>] ? clockevents_program_event+0x76/0x120
Oct 22 17:42:57 GLADOS kernel: [11130.116784]  [<ffffffff810a9164>] ? tick_program_event+0x24/0x30
Oct 22 17:42:57 GLADOS kernel: [11130.116791]  [<ffffffff8168b11c>] call_softirq+0x1c/0x30
Oct 22 17:42:57 GLADOS kernel: [11130.116798]  [<ffffffff81015115>] do_softirq+0x75/0xb0
Oct 22 17:42:57 GLADOS kernel: [11130.116802]  [<ffffffff8105ab95>] irq_exit+0xa5/0xb0
Oct 22 17:42:57 GLADOS kernel: [11130.116807]  [<ffffffff8168ba5e>] smp_apic_timer_interrupt+0x6e/0x99
Oct 22 17:42:57 GLADOS kernel: [11130.116814]  [<ffffffff8168a7ca>] apic_timer_interrupt+0x6a/0x70
Oct 22 17:42:57 GLADOS kernel: [11130.116816]  <EOI> 
Oct 22 17:42:57 GLADOS kernel: [11130.116820]  [<ffffffffa0159e88>] ? mei_timer+0xa8/0x270 [mei]
Oct 22 17:42:57 GLADOS kernel: [11130.116832]  [<ffffffff8107079a>] process_one_work+0x12a/0x420
Oct 22 17:42:57 GLADOS kernel: [11130.116840]  [<ffffffffa0159de0>] ? mei_interrupt_quick_handler+0x50/0x50 [mei]
Oct 22 17:42:57 GLADOS kernel: [11130.116844]  [<ffffffff8107133e>] worker_thread+0x12e/0x2f0
Oct 22 17:42:57 GLADOS kernel: [11130.116848]  [<ffffffff81071210>] ? manage_workers.isra.26+0x200/0x200
Oct 22 17:42:57 GLADOS kernel: [11130.116854]  [<ffffffff81075e33>] kthread+0x93/0xa0
Oct 22 17:42:57 GLADOS kernel: [11130.116858]  [<ffffffff8168b024>] kernel_thread_helper+0x4/0x10
Oct 22 17:42:57 GLADOS kernel: [11130.116863]  [<ffffffff81075da0>] ? kthread_freezable_should_stop+0x70/0x70
Oct 22 17:42:57 GLADOS kernel: [11130.116867]  [<ffffffff8168b020>] ? gs_change+0x13/0x13
Oct 22 17:42:57 GLADOS kernel: [11130.116869] Code: 50 dc 00 00 c7 45 c0 0a 00 00 00 89 55 ac 48 89 45 b0 48 89 45 b8 0f 1f 44 00 00 65 c7 04 25 40 15 01 00 00 00 00 00 fb 66 66 90 <66> 66 90 49 c7 c4 80 40 c0 81 eb 0c 0f 1f 40 00 49 83 c4 08 d1 
Oct 22 17:43:25 GLADOS kernel: [11158.061088] BUG: soft lockup - CPU#2 stuck for 22s! [kworker/2:1:12579]
Oct 22 17:43:25 GLADOS kernel: [11158.061094] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) xts gf128mul dm_crypt joydev parport_pc bnep ppdev rfcomm bluetooth ext2 arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi dell_laptop snd_hda_codec_realtek dcdbas coretemp kvm_intel kvm microcode snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi serio_raw iOct 22 17:44:40 GLADOS kernel: imklog 5.8.6, log source = /proc/kmsg started.

```

Any help is appreciated.

---

### Post by LucidREM on 2013-07-17
i have been having the same issue with the same Dell 1569 laptop computer .. it never seemed to be an issue prior (i believe the Ubuntu 10) but ever since it started happening it will not go away .. during the shutdown or reboot process it hangs and will not complete .. recently i keep getting the BUG SOFT LOCKUP CPU#1 error .. there must be something which was modified from the older Ubuntu that this model dislikes

---

