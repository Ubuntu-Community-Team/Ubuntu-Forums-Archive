---
title: "strange cpu error in syslog"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by arathorn2nd on 2007-06-17
Hello folks.

I decided to reencode my mp3s for use on my mobile, and using my dual-core laptop and lame, it was going like a breeze. But after a few minutes, I got a CPU error from syslog.

This is something new to me; should I get worried about this?

```
Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] Oops: 0000 [#1]

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] SMP 

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] CPU:    1

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] EIP:    0060:[_proxy_pda+0/1024]    Not tainted VLI

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] EFLAGS: 00010246   (2.6.20-16-generic #2)

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] EIP is at 0x0

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] eax: 00000000   ebx: 00000000   ecx: 00000400   edx: c8b81b40

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] esi: 00000000   edi: 00000000   ebp: 00000000   esp: cab95fc0

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] Process mmcqd (pid: 8410, ti=cab94000 task=cc505030 task.ti=cab94000)

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000] Stack: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...
paulo-laptop kernel: [ 3186.232000]        00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@paulo-laptop at Sun Jun 17 16:34:36 2007 ...

```

---

### Post by kidders on 2007-06-19
Hi there,

This could be the result of (among other things) ...[LIST]
[*]A serious bug in the Linux kernel that applies specifically to your hardware, or an incompatibility with your hardware.
[*]An overheating or otherwise faulty CPU.
[*]Dodgy RAM.[/LIST]For your own peace of mind, it would probably be worth trying to figure out which (if any) of these is the cause. Since you mention your PC is a laptop, my first suspicion would be the that it might not be cooling itself adequately ... especially since you say you were doing some audio encoding (which can be quite processor-intensive) at the time. You could try turning up your fans.

"Oops" is a rare error ... the majority of users never see one. If Linux ever says that to you, you should consider rebooting. (Kernel oopses can lead to odd behaviour.)

---

