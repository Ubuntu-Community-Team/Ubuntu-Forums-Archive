---
title: "Wireless Card Problem"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by ryukocn on 2007-05-22
I encountered a problem with my wireless card in Ubuntu 6.10
Please help.

Here is some information of my system and wireless card.
I want to use Netgear WG511A
I can not find the driver in Ubuntu, so I decide to use ndiswrapper. 

I have installed ndiswrapper by apt-get 
```

apt-get install ndiswrapper-utils
apt-get install ndisgtk

```

Then installed driver of Windows in ndiswrapper.
```

ndiswrapper -i WG511v2.INF
ndiswrapper -l
Installed ndis drivers:
wg511v2 driver present, hardware present 

```
Then I tried to active it, but failed.
```

depmod -a
modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
ndiswrapper -e ndiswrapper.ko
Driver ndiswrapper.ko is not installed. Use -l to list installed drivers
ndiswrapper -e wg511v2
modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

Here is some log.
```

dmesg |grep ndis
[17179933.784000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179933.820000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179933.824000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179941.744000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179941.744000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179941.744000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180048.944000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180048.944000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180048.944000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180082.344000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180082.344000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180082.344000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180260.208000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180260.240000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180260.244000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180797.244000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180797.272000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180797.272000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180875.836000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180875.836000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180875.840000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed


 cat syslog |grep ndis
May 23 00:49:54 u61 kernel: [17179933.784000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 00:49:54 u61 kernel: [17179933.820000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 00:49:54 u61 kernel: [17179933.824000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 00:50:02 u61 kernel: [17179941.744000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 00:50:02 u61 kernel: [17179941.744000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 00:50:02 u61 kernel: [17179941.744000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 00:51:49 u61 kernel: [17180048.944000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 00:51:49 u61 kernel: [17180048.944000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 00:51:49 u61 kernel: [17180048.944000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 00:52:22 u61 kernel: [17180082.344000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 00:52:22 u61 kernel: [17180082.344000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 00:52:22 u61 kernel: [17180082.344000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 00:55:20 u61 kernel: [17180260.208000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 00:55:20 u61 kernel: [17180260.240000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 00:55:20 u61 kernel: [17180260.244000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 01:04:17 u61 kernel: [17180797.244000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 01:04:17 u61 kernel: [17180797.272000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 01:04:17 u61 kernel: [17180797.272000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
May 23 01:05:36 u61 kernel: [17180875.836000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
May 23 01:05:36 u61 kernel: [17180875.836000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
May 23 01:05:36 u61 kernel: [17180875.840000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

```

Any suggestion?

Thanks in advance.

---

### Post by Praill on 2007-05-22
looks like its saying the ndiswrapper module is not on the system. I havent ever used ndiswrapper so I dont really know, but are there any other packages you missed?

you installed ndiswrapper-utils and ndisgtk, which from first glace seem to be a utility package and a gui. Did you miss installing the actual module that makes everything work? Id check but im on a windows machine at work right now.
Anyways, that might be a useless suggestion but no one else has responded yet so I thought id offer my two cents. Ill check this post again when i get home to my ubuntu system.

---

### Post by ryukocn on 2007-05-23
The wireless card works well, in the same laptop under windows xp.
But Ijust use it with the origin driver and application. I can use the origin application to set up wireless network. 

I don't know how to do this in Ubuntu. Anyway , I have not put it activated yet at the first place.

---

