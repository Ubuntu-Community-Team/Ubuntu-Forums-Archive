---
title: "Failure to wake from hibernation ([fglrx] ASIC hang happens.)"
date: 2009-02-12
forum: Hardware
---

### Post by AKADAP on 2009-02-12
I can hibernate my desktop, but when I try to wake, I get to where the login screen would show up in a normal boot and get stuck with a black screen.

Syslog shows:
Feb 11 16:03:03 Compromise kernel: [  362.748137] [fglrx] ASIC hang happens.
Feb 11 16:03:03 Compromise kernel: [  362.748144] Pid: 6688, comm: Xorg Tainted: P          2.6.27-11-generic #1
Feb 11 16:03:03 Compromise kernel: [  362.748147] 
Feb 11 16:03:03 Compromise kernel: [  362.748148] Call Trace:
Feb 11 16:03:03 Compromise kernel: [  362.748202]  [<ffffffffa020bcfe>] KCL_dump_stack+0xe/0x10 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748243]  [<ffffffffa021e78c>] firegl_hardwareHangRecovery+0x1c/0x50 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748314]  [<ffffffffa02929d9>] ? _ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x10 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748384]  [<ffffffffa029298c>] ? _ZN4Asic9WaitUntil15WaitForCompleteEv+0x6c/0xb0 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748454]  [<ffffffffa0291a7d>] ? _ZN4Asic19PM4ElapsedTimeStampERK23PM4_TS_INTERRUPT_PARAMSj14_LARGE_INTEGER+0x18d/0x1c0 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748461]  [<ffffffff80245b90>] ? load_balance_newidle+0x90/0x280
Feb 11 16:03:03 Compromise kernel: [  362.748466]  [<ffffffff80210219>] ? test_ti_thread_flag+0x9/0x20
Feb 11 16:03:03 Compromise kernel: [  362.748470]  [<ffffffff802107f6>] ? __switch_to+0x3e6/0x490
Feb 11 16:03:03 Compromise kernel: [  362.748477]  [<ffffffff8050171a>] ? thread_return+0x6d/0x3c3
Feb 11 16:03:03 Compromise kernel: [  362.748543]  [<ffffffffa0284a52>] ? _Z19uQSTimeStampRetiredmjj14_LARGE_INTEGER+0xd2/0xe0 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748609]  [<ffffffffa0280a38>] ? _Z8uCWDDEQCmjjPvjS_+0x378/0x1040 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748656]  [<ffffffffa02386e8>] ? firegl_cmmqs_CWDDE_32+0x368/0x410 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748702]  [<ffffffffa02372e3>] ? firegl_cmmqs_CWDDE32+0x73/0x110 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748707]  [<ffffffff80386a31>] ? apparmor_capable+0x21/0x70
Feb 11 16:03:03 Compromise kernel: [  362.748752]  [<ffffffffa0237270>] ? firegl_cmmqs_CWDDE32+0x0/0x110 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748791]  [<ffffffffa021a40d>] ? firegl_ioctl+0x1ed/0x260 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748828]  [<ffffffffa020fd26>] ? ip_firegl_ioctl+0x16/0x20 [fglrx]
Feb 11 16:03:03 Compromise kernel: [  362.748833]  [<ffffffff802f8975>] ? vfs_ioctl+0x85/0xb0
Feb 11 16:03:03 Compromise kernel: [  362.748836]  [<ffffffff802f8c13>] ? do_vfs_ioctl+0x273/0x2f0
Feb 11 16:03:03 Compromise kernel: [  362.748840]  [<ffffffff802f8d31>] ? sys_ioctl+0xa1/0xb0
Feb 11 16:03:03 Compromise kernel: [  362.748844]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
etc.

The System is Ubuntu64 on an Asus P6T Delux motherboard with an ATI HD4850 video card

---

