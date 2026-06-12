---
title: "wlan connection dies and causes kernel-error."
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-05-01
My WLAN connection just died and i got this kernel error:

[134590.448000] CPU:    0
[134590.448000] EIP:    0060:[<c013735e>]    Not tainted VLI
[134590.448000] EFLAGS: 00010296   (2.6.20-15-generic #2)
[134590.448000] EIP is at run_workqueue+0xee/0x140
[134590.448000] eax: 06dd3a5c   ebx: f5d1c94c   ecx: 00000246   edx: 00000000
[134590.448000] esi: f5d1c940   edi: f5d1c948   ebp: 00000246   esp: f5dbdf58
[134590.448000] ds: 007b   es: 007b   ss: 0068
[134590.448000] Process ipw3945/0 (pid: 3739, ti=f5dbc000 task=dfa32030 task.ti=f5dbc000)
[134590.448000] Stack: 00000000 f5d1c94c f5d1c954 f5dbdf9c f5d1c94b f5d1c960 00000001 f5d1c940 
[134590.448000]        f5d1c94c f5d1c954 f5dbdf9c c0137d87 00000001 00000000 c20044c0 00010000 
[134590.448000]        00000000 00000000 dfa32030 c0120b40 00100100 00200200 ffffffff ffffffff 
[134590.448000] Call Trace:
[134590.448000]  [<c0137d87>] worker_thread+0x147/0x170
[134590.448000]  [<c0120b40>] default_wake_function+0x0/0x10
[134590.448000]  [<c0137c40>] worker_thread+0x0/0x170
[134590.448000]  [<c013ac3a>] kthread+0xba/0xf0
[134590.448000]  [<c013ab7e>] keventd_create_kthread+0x6e/0x70
[134590.448000]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[134590.448000]  =======================

I was not able to re-establish the connection and soon afterwards my wlan-card was not longer appearing in iwconfig.
Reloading the ipw3945 module also was not possible.

---

