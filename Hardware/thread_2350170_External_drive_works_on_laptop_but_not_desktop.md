---
title: "External drive works on laptop but not desktop"
date: 2017-01-21
forum: Hardware
---

### Post by jlarsson89 on 2017-01-21
Hi,<br>
<br>
I bought a Seagate Backup Plus Slim 2 TB USB 3.0 Portable 2.5 inch External Hard Drive over Christmas to replace my old external that has broken sectors, and while it works fine with my laptop(running Xubuntu 16.04), it refuses to even connect to my desktop running the same system. I set it to run ext4 instead of the default ntfs, perhaps that was a bad idea?<br>
<br>
Anyway, this is what journalctl tells me when I try to plug it in to my desktop.<br>
```
Jan 21 23:18:00 oxford kernel: sd 6:0:0:0: [sdc] Spinning up disk...<br>
Jan 21 23:18:04 oxford colord-sane[10307]: io/hpmud/pp.c 627: unable to read device-id ret=-1<br>
Jan 21 23:18:20 oxford kernel: ....................<br>
Jan 21 23:18:20 oxford kernel: usb 3-12.1: USB disconnect, device number 6<br>
Jan 21 23:18:21 oxford kernel: .ready<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Sense not available.<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Sense not available.<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Write Protect is off<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Asking for cache data failed<br>
Jan 21 23:18:21 oxford kernel: sd 6:0:0:0: [sdc] Assuming drive cache: write through<br>
Jan 21 23:18:22 oxford kernel: sd 6:0:0:0: [sdc] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK<br>
Jan 21 23:18:22 oxford kernel: sd 6:0:0:0: [sdc] Sense not available.<br>
Jan 21 23:18:22 oxford kernel: sd 6:0:0:0: [sdc] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK<br>
Jan 21 23:18:22 oxford kernel: sd 6:0:0:0: [sdc] Sense not available.<br>
Jan 21 23:18:22 oxford kernel: sd 6:0:0:0: [sdc] Attached SCSI disk<br>
Jan 21 23:18:22 oxford systemd-udevd[10320]: inotify_add_watch(9, /dev/sdc, 10) failed: No such file or directory<br>
Jan 21 23:18:26 oxford colord-sane[10316]: io/hpmud/pp.c 627: unable to read device-id ret=-1<br>
Jan 21 23:25:01 oxford CRON[10534]: pam_unix(cron:session): session opened for user root by (uid=0)<br>
Jan 21 23:25:01 oxford CRON[10535]: (root) CMD (command -v debian-sa1 &gt; /dev/null &amp;&amp; debian-sa1 1 1)<br>
Jan 21 23:25:01 oxford CRON[10534]: pam_unix(cron:session): session closed for user root<br>

```Any ideas as to why this is happening?

---

### Post by QIII on 2017-01-21
Duplicate of [https://ubuntuforums.org/showthread.php?t=2350166](https://ubuntuforums.org/showthread.php?t=2350166)

Closed.

---

