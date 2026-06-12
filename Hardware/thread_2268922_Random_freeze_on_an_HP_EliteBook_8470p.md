---
title: "Random freeze on an HP EliteBook 8470p"
date: 2015-03-12
forum: Hardware
---

### Post by theonemule on 2015-03-12
I'm trying to troubleshoot a problem on my laptop. I'm running an HP EliteBook 8470p with an ATI GPU.

My laptop seems to randomly freeze... I can't drop to a terminal (ctrl alt F-key) or restart x (ctrl alt bkspc bkspc) or any other keyboard combination. When this happens, everything is frozen. Caps lock or any other lock key won't change the indicator light, the mouse cursor freezes, and the CPU fan maxes out. The only thing I can do is a hard shutdown (5 seconds on the power button) and restart.

I'm running Ubuntu without any problems on two other boxes, so I'm convinced this is a hardware issue with this particular machine.

I've tried switching desktop environments, (KDE, Cinnamon, Mate, XFCE) and switching between open and closed source drivers for the GPU. Nothing seems to work. 

The kernel log doesn't show a kernel panic and doesn't really have anything that I can tell that happens right before the lock up occurs other than this...

Mar 12 10:29:21 machine-name kernel: [ 1082.795235] INFO: task python:713 blocked for more than 120 seconds.
Mar 12 10:29:21 machine-name kernel: [ 1082.795239]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu
Mar 12 10:29:21 machine-name kernel: [ 1082.795239] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 12 10:29:21 machine-name kernel: [ 1082.795241] python          D ffff88043dd14480     0   713      1 0x00000000
Mar 12 10:29:21 machine-name kernel: [ 1082.795244]  ffff8800b61ede10 0000000000000082 ffff8800b6610000 ffff8800b61edfd8
Mar 12 10:29:21 machine-name kernel: [ 1082.795247]  0000000000014480 0000000000014480 ffff8800b6610000 ffffffffa00c8040
Mar 12 10:29:21 machine-name kernel: [ 1082.795248]  ffffffffa00c8044 ffff8800b6610000 00000000ffffffff ffffffffa00c8048
Mar 12 10:29:21 machine-name kernel: [ 1082.795250] Call Trace:
Mar 12 10:29:21 machine-name kernel: [ 1082.795267]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70
Mar 12 10:29:21 machine-name kernel: [ 1082.795270]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0
Mar 12 10:29:21 machine-name kernel: [ 1082.795274]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f
Mar 12 10:29:21 machine-name kernel: [ 1082.795277]  [<ffffffffa00c5cc3>] pp_ioctl+0x23/0x50 [ppdev]
Mar 12 10:29:21 machine-name kernel: [ 1082.795281]  [<ffffffff811d03a0>] do_vfs_ioctl+0x2e0/0x4c0
Mar 12 10:29:21 machine-name kernel: [ 1082.795283]  [<ffffffff811d0601>] SyS_ioctl+0x81/0xa0
Mar 12 10:29:21 machine-name kernel: [ 1082.795285]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f
Mar 12 10:31:21 machine-name kernel: [ 1202.897397] INFO: task python:713 blocked for more than 120 seconds.
Mar 12 10:31:21 machine-name kernel: [ 1202.897407]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu
Mar 12 10:31:21 machine-name kernel: [ 1202.897409] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 12 10:31:21 machine-name kernel: [ 1202.897412] python          D ffff88043dd14480     0   713      1 0x00000000
Mar 12 10:31:21 machine-name kernel: [ 1202.897419]  ffff8800b61ede10 0000000000000082 ffff8800b6610000 ffff8800b61edfd8
Mar 12 10:31:21 machine-name kernel: [ 1202.897425]  0000000000014480 0000000000014480 ffff8800b6610000 ffffffffa00c8040
Mar 12 10:31:21 machine-name kernel: [ 1202.897430]  ffffffffa00c8044 ffff8800b6610000 00000000ffffffff ffffffffa00c8048
Mar 12 10:31:21 machine-name kernel: [ 1202.897436] Call Trace:
Mar 12 10:31:21 machine-name kernel: [ 1202.897468]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70
Mar 12 10:31:21 machine-name kernel: [ 1202.897475]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0
Mar 12 10:31:21 machine-name kernel: [ 1202.897486]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f
Mar 12 10:31:21 machine-name kernel: [ 1202.897496]  [<ffffffffa00c5cc3>] pp_ioctl+0x23/0x50 [ppdev]
Mar 12 10:31:21 machine-name kernel: [ 1202.897505]  [<ffffffff811d03a0>] do_vfs_ioctl+0x2e0/0x4c0
Mar 12 10:31:21 machine-name kernel: [ 1202.897512]  [<ffffffff811d0601>] SyS_ioctl+0x81/0xa0
Mar 12 10:31:21 machine-name kernel: [ 1202.897518]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f
Mar 12 10:33:21 machine-name kernel: [ 1322.999451] INFO: task python:713 blocked for more than 120 seconds.
Mar 12 10:33:21 machine-name kernel: [ 1322.999459]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu
Mar 12 10:33:21 machine-name kernel: [ 1322.999461] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 12 10:33:21 machine-name kernel: [ 1322.999464] python          D ffff88043dd14480     0   713      1 0x00000000
Mar 12 10:33:21 machine-name kernel: [ 1322.999471]  ffff8800b61ede10 0000000000000082 ffff8800b6610000 ffff8800b61edfd8
Mar 12 10:33:21 machine-name kernel: [ 1322.999477]  0000000000014480 0000000000014480 ffff8800b6610000 ffffffffa00c8040
Mar 12 10:33:21 machine-name kernel: [ 1322.999482]  ffffffffa00c8044 ffff8800b6610000 00000000ffffffff ffffffffa00c8048
Mar 12 10:33:21 machine-name kernel: [ 1322.999487] Call Trace:
Mar 12 10:33:21 machine-name kernel: [ 1322.999516]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70
Mar 12 10:33:21 machine-name kernel: [ 1322.999523]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0
Mar 12 10:33:21 machine-name kernel: [ 1322.999532]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f
Mar 12 10:33:21 machine-name kernel: [ 1322.999541]  [<ffffffffa00c5cc3>] pp_ioctl+0x23/0x50 [ppdev]
Mar 12 10:33:21 machine-name kernel: [ 1322.999549]  [<ffffffff811d03a0>] do_vfs_ioctl+0x2e0/0x4c0
Mar 12 10:33:21 machine-name kernel: [ 1322.999555]  [<ffffffff811d0601>] SyS_ioctl+0x81/0xa0
Mar 12 10:33:21 machine-name kernel: [ 1322.999560]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f

I really wish I had more to go on... any help would be appreciated.

---

### Post by tgalati4 on 2015-03-13
What is the ATI chip?  How old is the machine?

A graphics chip that has delaminated will behave in a similar fashion.

```
lspci | grep VGA
```

---

### Post by theonemule on 2015-03-13
Here's the output from lspci: 

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M]
```

All 8470p's have a 7570M

It's not very old. They were released in Q2 in 2012. I got Q3 2013. I recently switched from Windows to Linux on this box though...

I did some tweaks yesterday to the sysctl.conf per this post here. 

[http://www.blackmoreops.com/2014/09/22/linux-kernel-panic-issue-fix-hung_task_timeout_secs-blocked-120-seconds-problem/](http://www.blackmoreops.com/2014/09/22/linux-kernel-panic-issue-fix-hung_task_timeout_secs-blocked-120-seconds-problem/)

It looked unrelated because my symptoms weren't the same as these, but I did the tweaks at the bottom and it seems to be more stable. But I don't wan't to say it's resolved yet because I haven't identified a pattern to the crashes yet, other than what I posted from the kernel log in the OP. But there's been no more recurrences of the timeout in the kernel log either.

```
sudo nano /etc/sysctl.conf
```

Added this to the bottom:

```
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10
```

Saved and rebooted.

```
sudo reboot now
```

---

### Post by theonemule on 2015-03-16
Happened again...this time I had nothing in the kernel log indicating a kernel panic or error. Strange.

---

