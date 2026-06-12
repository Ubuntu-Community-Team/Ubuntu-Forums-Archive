---
title: "X crashes frequently on Macbook"
date: 2010-10-22
forum: Hardware
---

### Post by Edddd on 2010-10-22
Hi all,

I finally got my wife to give Linux a go and unfortunately it's not working out too great.  Everything is pretty working fine it's just that X keeps freezing when she's in the middle of using it and she's getting pretty hacked off with.

It's a complete freeze, mouse cursor included.  Though brightness still goes up and down so I guess it's not a total system crash.  I had a look in /var/log/messages and I found this kernel oops relating to the video hardware, so I guess this is probably the source of the problem.  It's a first gen x86 MacBook bought about 4 years ago.

But how do I go about fixing it?  Any help would be greatly appreciated..

```

Oct 23 08:54:12 MaiMac kernel: [12127.872055] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 23 08:56:04 MaiMac kernel: [12240.308144] i915          D 00002dfe     0   688      2 0x00000000
Oct 23 08:56:04 MaiMac kernel: [12240.308154]  f398fedc 00000046 f1660000 00002dfe 00000000 c0848760 f38c426c c0848760
Oct 23 08:56:04 MaiMac kernel: [12240.308169]  e286b598 00000b04 c0848760 c0848760 f38c426c c0848760 c0848760 f1fe1dc0
Oct 23 08:56:04 MaiMac kernel: [12240.308183]  00000001 00000b04 f38c3fc0 f71c7c14 f71c7c18 ffffffff f398ff08 c058c1a6
Oct 23 08:56:04 MaiMac kernel: [12240.308197] Call Trace:
Oct 23 08:56:04 MaiMac kernel: [12240.308213]  [<c058c1a6>] __mutex_lock_slowpath+0xd6/0x140
Oct 23 08:56:04 MaiMac kernel: [12240.308220]  [<c058c0b5>] mutex_lock+0x25/0x40
Oct 23 08:56:04 MaiMac kernel: [12240.308258]  [<f867b183>] intel_idle_update+0x33/0x180 [i915]
Oct 23 08:56:04 MaiMac kernel: [12240.308275]  [<c058b17c>] ? schedule+0x44c/0x840
Oct 23 08:56:04 MaiMac kernel: [12240.308285]  [<c016399e>] run_workqueue+0x8e/0x150
Oct 23 08:56:04 MaiMac kernel: [12240.308311]  [<f867b150>] ? intel_idle_update+0x0/0x180 [i915]
Oct 23 08:56:04 MaiMac kernel: [12240.308320]  [<c0163ae4>] worker_thread+0x84/0xe0
Oct 23 08:56:04 MaiMac kernel: [12240.308328]  [<c0167a60>] ? autoremove_wake_function+0x0/0x50
Oct 23 08:56:04 MaiMac kernel: [12240.308336]  [<c0163a60>] ? worker_thread+0x0/0xe0
Oct 23 08:56:04 MaiMac kernel: [12240.308343]  [<c01677d4>] kthread+0x74/0x80
Oct 23 08:56:04 MaiMac kernel: [12240.308350]  [<c0167760>] ? kthread+0x0/0x80
Oct 23 08:56:04 MaiMac kernel: [12240.308358]  [<c0104087>] kernel_thread_helper+0x7/0x10
Oct 23 08:56:04 MaiMac kernel: [12240.308389] Xorg          D 00025723     0  1088   1033 0x00400004
Oct 23 08:56:04 MaiMac kernel: [12240.308398]  f3ab1e14 00203082 f1660000 00025723 00000000 c0848760 f393f56c c0848760
Oct 23 08:56:04 MaiMac kernel: [12240.308412]  c6915d56 00000b04 c0848760 c0848760 f393f56c c0848760 c0848760 f397ca80
Oct 23 08:56:04 MaiMac kernel: [12240.308426]  00000000 00000b04 f393f2c0 f71c7c14 f71c7c18 ffffffff f3ab1e40 c058c1a6
Oct 23 08:56:04 MaiMac kernel: [12240.308440] Call Trace:
Oct 23 08:56:04 MaiMac kernel: [12240.308449]  [<c058c1a6>] __mutex_lock_slowpath+0xd6/0x140
Oct 23 08:56:04 MaiMac kernel: [12240.308456]  [<c058c0b5>] mutex_lock+0x25/0x40
Oct 23 08:56:04 MaiMac kernel: [12240.308483]  [<f866b755>] i915_gem_madvise_ioctl+0x45/0x120 [i915]
Oct 23 08:56:04 MaiMac kernel: [12240.308510]  [<f80f980d>] drm_ioctl+0x29d/0x410 [drm]
Oct 23 08:56:04 MaiMac kernel: [12240.308537]  [<f866b710>] ? i915_gem_madvise_ioctl+0x0/0x120 [i915]
Oct 23 08:56:04 MaiMac kernel: [12240.308550]  [<c058d24f>] ? _spin_lock_irqsave+0x2f/0x50
Oct 23 08:56:04 MaiMac kernel: [12240.308558]  [<c0167a60>] ? autoremove_wake_function+0x0/0x50
Oct 23 08:56:04 MaiMac kernel: [12240.308568]  [<c02f58c4>] ? security_file_permission+0x14/0x20
Oct 23 08:56:04 MaiMac kernel: [12240.308590]  [<f80f9570>] ? drm_ioctl+0x0/0x410 [drm]
Oct 23 08:56:04 MaiMac kernel: [12240.308601]  [<c0216f71>] vfs_ioctl+0x21/0x90
Oct 23 08:56:04 MaiMac kernel: [12240.308609]  [<c0171ec5>] ? ktime_get_ts+0xe5/0x110
Oct 23 08:56:04 MaiMac kernel: [12240.308616]  [<c0217259>] do_vfs_ioctl+0x79/0x310
Oct 23 08:56:04 MaiMac kernel: [12240.308623]  [<c0217557>] sys_ioctl+0x67/0x80
Oct 23 08:56:04 MaiMac kernel: [12240.308630]  [<c01033ec>] syscall_call+0x7/0xb

```

---

### Post by Edddd on 2010-10-26
Any ideas on this?

---

