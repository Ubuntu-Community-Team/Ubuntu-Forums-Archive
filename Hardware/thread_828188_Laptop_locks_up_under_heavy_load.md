---
title: "Laptop locks up under heavy load"
date: 2008-06-13
forum: Hardware
---

### Post by gerbalblaste on 2008-06-13
I have a gateway cx210. 
Intel Core 2 T7200 2ghz
ATI radeon mobility x1400

When running CPU intensive tasks or games my laptop will lockup. The screen will freeze. Sometimes sound continues to function but other times the sound will start looping the previous second or so. The computer becomes quite hot to the touch but not 'cookin' hot. 

The only way to recover is a hard reboot.

---

### Post by gerbalblaste on 2008-07-24
*bump*
Problem is still occurring after several kernel updates and has been occurring for quite a while. I have identified it as a soft lock-up. The cause remains unknown.

the following is the syslog of one such incident. 
```
Jul 24 19:27:53 gerbal-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775433] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:5791]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775440] 
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775442] Pid: 5791, comm: Xorg Tainted: P        (2.6.24-19-generic #1)
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775445] EIP: 0060:[<f904d3ee>] EFLAGS: 00203246 CPU: 1
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775534] EIP is at _ZN4Asic16WaitForBitsClear19ConditionSuccessfulEv+0x1e/0x70 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775537] EAX: 90010140 EBX: 007ffff9 ECX: 00000000 EDX: f8fa0e40
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775540] ESI: 00000000 EDI: efa61d58 EBP: efa61d00 ESP: efa61ce8
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775543]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775545] CR0: 80050033 CR2: 08da91b4 CR3: 2fb01000 CR4: 00000690
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775548] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775550] DR6: ffff0ff0 DR7: 00000400
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775573]  [<f904c6e8>] _ZN4Asic9WaitUntil15WaitForCompleteEv+0x38/0xf0 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775662]  [<f90507bc>] _ZN6AsicR616ASICIdleInternalEN4Asic15idle_WaitMethodE+0xcc/0x1f0 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775751]  [<c0125f20>] default_wake_function+0x0/0x10
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775786]  [<f902e4b6>] QSSubmitList+0x146/0x150 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775866]  [<f904af9c>] _ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x4c/0x80 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775952]  [unix_stream_recvmsg+0x25d/0x550] unix_stream_recvmsg+0x25d/0x550
Jul 24 19:27:59 gerbal-laptop kernel: [16329.775962]  [<f9045645>] _ZN15QS_PRIVATE_CORE7PM4idleEN4Asic15idle_WaitMethodE+0x35/0x70 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776049]  [<f9035321>] _ZN10QS_PRIVATE11synchronizeEv+0x31/0x40 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776132]  [<f902e4d7>] QSSynchronize+0x17/0x20 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776211]  [<f9035e69>] _Z14uQSSynchronizej+0x19/0x20 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776293]  [<f903d49f>] _Z8uCWDDEQCjjjPvjS_+0x33f/0x11a0 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776385]  [<f902ddf4>] CMMQS_uCWDDEQC+0x34/0x40 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776466]  [<f8ff4e48>] firegl_cmmqs_CWDDE_32+0x238/0x340 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776535]  [sys_quotactl+0x4e6/0x680] sys_quotactl+0x4e6/0x680
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776542]  [<f8ff3e06>] firegl_cmmqs_CWDDE32+0x76/0x110 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776614]  [<f8ff3d90>] firegl_cmmqs_CWDDE32+0x0/0x110 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776680]  [<f8fe64be>] firegl_ioctl+0x19e/0x220 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776743]  [sys_quotactl+0x4e6/0x680] sys_quotactl+0x4e6/0x680
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776752]  [sock_aio_write+0x0/0x120] sock_aio_write+0x0/0x120
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776762]  [sys_quotactl+0x4e6/0x680] sys_quotactl+0x4e6/0x680
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776767]  [<f8fdb85c>] ip_firegl_ioctl+0x1c/0x30 [fglrx]
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776828]  [sys_quotactl+0x4e6/0x680] sys_quotactl+0x4e6/0x680
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776836]  [do_ioctl+0x78/0x90] do_ioctl+0x78/0x90
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776845]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776854]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776863]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776868]  [sys_quotactl+0x4e6/0x680] sys_quotactl+0x4e6/0x680
Jul 24 19:27:59 gerbal-laptop kernel: [16329.776881]  =======================
```

As far as I can tell these events occur in a similar manner every time. 

Any and all help is truly appreciated.

---

### Post by sdennie on 2008-07-24
It looks like it's a problem with the ATI driver.  I would see if you can find a newer version and see if that helps.

---

### Post by gerbalblaste on 2008-07-25
Thanks, updating the ATI drivers helped alot. The problem is not entirely resolved but my system no longer locks up at the drop of a hat.

---

### Post by evets25 on 2008-07-25
Graphics drivers are the #1 cause of system lockup and crashes. Keep on doing kernel updates and graphics driver updates, and eventually these problems will resolve themselves. 

In the meantime, if your computer does freeze up again, you can safely shut it down with the magic sysreq key: 

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Just press and hold alt+sysrq, then while holding them, type (slowly) r e i s u b and your computer will reboot, even if it's frozen from the graphics driver freaking out again. 

Also, you might want to double-check and make sure that your temperature is okay and nothing's overheating, as that could also cause this type of problem.

---

