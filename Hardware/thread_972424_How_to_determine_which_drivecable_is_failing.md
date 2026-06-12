---
title: "How to determine which drive/cable is failing?"
date: 2008-11-05
forum: Hardware
---

### Post by fermulator on 2008-11-05
Good day all,

Every once in a while my system crashes.  Running Ubuntu server 7.04.

Usually all I can see are "kernel panic" messages on the screen.

This time it crashed I happened to be SSH'd into the box and it spat out the following:

> Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] EFLAGS: 00010807   (2.6.20-17-server #2)

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] EIP:    0060:[cache_alloc_refill+262/1312]    Not tainted VLI

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] CPU:    0

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] SMP 

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] Oops: 0000 [#1]

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000]        fffff000 00000000 c0174235 00000000 00000000 c0197fbd 00000000 c01989ab 

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000] Call Trace:

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000]  [<f897298a>] do_get_write_access+0x1ca/0x510 [jbd]

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000]  [kmem_cache_alloc+101/112] kmem_cache_alloc+0x65/0x70

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000]  [alloc_buffer_head+13/64] alloc_buffer_head+0xd/0x40

Message from syslogd@myhostname at Wed Nov  5 17:44:31 2008 ...
myhostname kernel: [17997.670000]  [alloc_page_buffers+171/240] alloc_page_buffers+0xab/0xf0

etc : [http://pastebin.com/m3c3eefc1](http://pastebin.com/m3c3eefc1)

How can I go about figuring out who the culprit is that's halting the entire kernel?

---

