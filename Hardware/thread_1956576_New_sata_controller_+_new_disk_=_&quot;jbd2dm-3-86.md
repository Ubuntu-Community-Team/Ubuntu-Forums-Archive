---
title: "New sata controller + new disk = &quot;jbd2/dm-3-8:656 blocked for more than 120 seconds&quot;"
date: 2012-04-11
forum: Hardware
---

### Post by klausmedk on 2012-04-11
Hello

On my Ubuntu server 11.10 I've installed a PCI SATA controller along with an old disk.

When I do an rsync (or any other operation that accesses the new disk) from an existing disk to the new disk it never completes.

In the syslog I get error messages like you see below.

[ 8760.644068] INFO: task jbd2/dm-3-8:656 blocked for more than 120 seconds.
[ 8760.644182] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8760.644302] jbd2/dm-3-8     D ffffffff81805120     0   656      2 0x00000000
[ 8760.644313]  ffff880125f21ad0 0000000000000046 ffff880125f21a80 ffff880125f21a80
[ 8760.644322]  ffff880125f21fd8 ffff880125f21fd8 ffff880125f21fd8 0000000000012a40
[ 8760.644331]  ffffffff81c0b020 ffff880128432e40 ffff88012ffce268 ffff88012fc132c0
[ 8760.644340] Call Trace:
[ 8760.644354]  [<ffffffff81108fe0>] ? __lock_page+0x70/0x70
[ 8760.644363]  [<ffffffff815fc9ef>] io_schedule+0x8f/0xd0
[ 8760.644371]  [<ffffffff81108fee>] sleep_on_page+0xe/0x20
...

Can anybody help me get to the bottom of this problem?
How do I determine whether this is a problem with the controller or the disk?

The disk is a WD green disk that had run smoothly on another Ubuntu system prior to being installed on this new system.

The SATA controller is a Silicon Image, SiI 3512 SATA 150 Controller

Any help is appreciated.

//Klaus

---

