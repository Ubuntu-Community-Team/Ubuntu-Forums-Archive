---
title: "problem with my server"
date: 2008-10-10
forum: General Help
---

### Post by hirohitosan on 2008-10-10
Hi there. From some days my server restart very often. I don't know why but after approximately one hour my server restart.
How can I find the problem? There are some logs or something to find what happened before restart?

Thank you.

---

### Post by Calmatory on 2008-10-10
Yes, there are logs. They are located in ```
/var/log/
``` So, to access them you can do ```
nano /var/log/*.log
``` where *.log is your preferred log.

You could also use cat and tail. This way: ```
cat /var/log/kernel.log
``` Prints /var/log/kernel.log to the screen. ```
tail -25 /var/log/kernel.log
``` prints only the last 25 lines.

But to the problem, could you show your kernel.log? Some last 20 lines should be sufficient.

---

### Post by hirohitosan on 2008-10-10
```
tail -25 /var/log/kern.log
Oct 10 09:18:44  kernel: [   51.817321] NET: Registered protocol family 10
Oct 10 09:18:44  kernel: [   51.817479] lo: Disabled Privacy Extensions
Oct 10 09:18:44  kernel: [   51.817736] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 10 09:18:44  kernel: [   51.905635] lp: driver loaded but no devices found
Oct 10 09:18:44  kernel: [   52.009959] Adding 3903784k swap on /dev/sda1.  Priority:-1 extents:1 across:3903784k
Oct 10 09:18:44  kernel: [   52.533724] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX
Oct 10 09:18:44  kernel: [   52.533727] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Oct 10 09:18:44  kernel: [   52.538005] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 10 09:18:44  kernel: [   52.556222] EXT3 FS on sda2, internal journal
Oct 10 09:18:44  kernel: [  345.097759] kjournald starting.  Commit interval 5 seconds
Oct 10 09:18:44  kernel: [  345.097968] EXT3 FS on sda5, internal journal
Oct 10 09:18:44  kernel: [  345.097972] EXT3-fs: mounted filesystem with ordered data mode.
Oct 10 09:18:44  kernel: [  345.874150] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 10 09:18:44  kernel: [  346.411911] No dock devices found.
Oct 10 09:18:48  kernel: [  351.269245] ppdev: user-space parallel port driver
Oct 10 09:18:49  kernel: [  351.818440] audit(1223619529.197:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8024 profile="/usr/sbin/cupsd" namespace="default"
Oct 10 09:18:53  kernel: [  356.064007] Bluetooth: Core ver 2.11
Oct 10 09:18:53  kernel: [  356.064083] NET: Registered protocol family 31
Oct 10 09:18:53  kernel: [  356.064085] Bluetooth: HCI device and connection manager initialized
Oct 10 09:18:53  kernel: [  356.064088] Bluetooth: HCI socket layer initialized
Oct 10 09:18:53  kernel: [  356.118771] Bluetooth: L2CAP ver 2.9
Oct 10 09:18:53  kernel: [  356.118774] Bluetooth: L2CAP socket layer initialized
Oct 10 09:18:53  kernel: [  356.168171] Bluetooth: RFCOMM socket layer initialized
Oct 10 09:18:53  kernel: [  356.168185] Bluetooth: RFCOMM TTY layer initialized
Oct 10 09:18:53  kernel: [  356.168187] Bluetooth: RFCOMM ver 1.8

```

---

### Post by Calmatory on 2008-10-10
Ah, I made a mistake. Of course the log shows the logged info from the boot instead of the crash. My bad. :|

Could you show some last 20 lines of the same log when the machine restarted? ..this in case you know when it happened last time. Another way would be to upload the whole file and attach it to your post.

---

### Post by hirohitosan on 2008-10-10
```
uptime
 09:57:44 up 44 min,  2 users,  load average: 0.00, 0.00, 0.00

```
I suppose it happens 1 hour ago

I attached the kern.log file as kern.txt

---

### Post by Calmatory on 2008-10-10
Hmm. It seems that the machine restarts once a hour for some unknown reason which is not shown in the file. Is this correct?

It is always the same delay between restarts, which is around 60 or 61 minutes.

Anyway, no after-boot signs of anything going wrong, at least not in the kernel log. What kind of server is it? Is it just a ordinary desktop computer being used as a server or is it actually a U* case with actual server hardware? 

When did the restarts start? What was done before them? The only reason I could think of is a cronjob(though I highly doubt it). Does /etc/cron.hourly/ have any files? If so, then which ones and could you provide their contents?

---

### Post by hirohitosan on 2008-10-10
> **Calmatory said:**
> What kind of server is it? Is it just a ordinary desktop computer being used as a server or is it actually a U* case with actual server hardware? 

When did the restarts start? What was done before them? The only reason I could think of is a cronjob(though I highly doubt it). Does /etc/cron.hourly/ have any files? If so, then which ones and could you provide their contents?

I bought it with some special U* case for server.
I really don't know when the restarts starts. I just noticed yesterday and from that moment I checked periodically "uptime" and I just saw that.

I have no idea what to do, maybe to change the plug?
I don't know if its just a software problem or hardware ...

---

### Post by hirohitosan on 2008-10-10
I checked by myself ... it restart after 1 hour. I don't know what to do. It's OK for the computer to be restarted each hour? And during restarting the file system is not cleanly unmounted. I'm thinking to shut down the server but I have no idea hot to repair it.

---

