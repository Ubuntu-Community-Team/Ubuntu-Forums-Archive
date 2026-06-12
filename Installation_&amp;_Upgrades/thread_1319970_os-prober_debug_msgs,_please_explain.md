---
title: "os-prober debug msgs, please explain"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by irishbreakfast on 2009-11-08
I hope it is OK - I've restarted this with a better title

I get error messages on the splash screen that I can't read before they disappear. From what I can read it is about waiting for partitions to mount. I searched /var/log and discovered the output below that seems to fit the problem in messages.1 and user.log.1. I don't know enough about the boot process to know why each partition is being tested.
I have not seen this before with 8.04 or 9.04. The only difference is that during the clean install on 9.10 I changed all partitions (except Vista's) to ext3.
So, can someone explain this? What can I do so I don't get the messages?
Thanx

Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda5
Nov 6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda

---

### Post by irishbreakfast on 2009-11-10
bump

anyone? any ideas where I can learn more about this?

---

### Post by faheyd on 2010-11-06
> **irishbreakfast said:**
> bump

anyone? any ideas where I can learn more about this?

I'm starting to see these now also on 10.4:
Linux matrix-67 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Nov  4 12:46:54 matrix-67 kernel: [83557.526713] udev: starting version 151
Nov  4 12:46:55 matrix-67 kernel: [83558.816844] __ratelimit: 21 callbacks suppressed
Nov  4 12:46:55 matrix-67 kernel: [83558.816848] type=1505 audit(1288900015.627:19):  operation="profile_replace" pid=17411 name="/usr/lib/cups/backend/cups-pdf"
Nov  4 12:46:55 matrix-67 kernel: [83558.817252] type=1505 audit(1288900015.627:20):  operation="profile_replace" pid=17411 name="/usr/sbin/cupsd"
Nov  4 13:12:56 matrix-67 kernel: [85119.554051] JFS: nTxBlock = 8192, nTxLock = 65536
Nov  4 13:12:56 matrix-67 kernel: [85119.610533] NTFS driver 2.1.29 [Flags: R/O MODULE].
Nov  4 13:12:56 matrix-67 kernel: [85119.655400] QNX4 filesystem 0.2.3 registered.
Nov  4 13:12:56 matrix-67 kernel: [85119.736092] Btrfs loaded
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Nov  4 13:12:56 matrix-67 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Nov  4 13:12:56 matrix-67 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Nov  4 13:12:56 matrix-67 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Nov  4 13:12:56 matrix-67 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda6
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda7
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 20microsoft: debug: /dev/sdb1 is not a MS partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 30utility: debug: /dev/sdb1 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdc1
Nov  4 13:12:56 matrix-67 10freedos: debug: /dev/sdc1 is not a FAT partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdc1
Nov  4 13:12:56 matrix-67 10qnx: debug: /dev/sdc1 is not a QNX4 partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdc1
Nov  4 13:12:56 matrix-67 macosx-prober: debug: /dev/sdc1 is not an HFS+ partition: exiting
Nov  4 13:12:56 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 20microsoft: debug: /dev/sdc1 is not a MS partition: exiting
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 30utility: debug: /dev/sdc1 is not a FAT partition: exiting
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdc1
Nov  4 13:12:57 matrix-67 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdc1

---

### Post by Ashrael on 2010-11-21
Two weeks ago...hmmm. I guess that's about when my problems started too...At the time using 10.04, now the same on 10.10... Getting the same messages as you guys. Also my pc spontaniously reboots on irregular intervals. Also getting errors like:


kernel: [ 2030.629800] NVRM: os_raise_smp_barrier(), invalid context!

this one seem to be NVIDIA related...

HTH!

---

