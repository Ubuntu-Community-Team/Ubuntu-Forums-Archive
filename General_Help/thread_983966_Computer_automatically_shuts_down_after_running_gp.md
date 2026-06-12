---
title: "Computer automatically shuts down after running gparted"
date: 2008-11-16
forum: General Help
---

### Post by peterdm on 2008-11-16
I use gparted sometimes to partition external (usb-2) hard disks. However, since I upgraded to intrepid, after running gparted, my computer automatically shuts down. I mean not *immediately* after, but after leaving it unattended for a couple of minutes or so.

Reproducible scenario:
```

. Attach an external hdd to the usb-2 port
. Start up gparted
. Remove and create a new partition on the external hdd (/dev/sdb in my case)
. Exit gparted
. Leave the system unattended for several minutes, it will shut down

```

/var/log/messages contains the following around the time of shutdown:

```

Nov 16 13:49:41 cheetah kernel: [ 2632.119708] sd 16:0:0:0: [sdb] Attached SCSI disk
Nov 16 13:49:41 cheetah kernel: [ 2632.119822] sd 16:0:0:0: Attached scsi generic sg2 type 0
Nov 16 13:49:59 cheetah kernel: [ 2650.738569] usb 7-6: USB disconnect, address 11
Nov 16 13:53:12 cheetah bonobo-activation-server (peter-9468): could not associate with desktop session: Failed to connect to socket /tmp/dbus-YrJRGeQz2B: Connection refused
Nov 16 13:53:16 cheetah bonobo-activation-server (peter-9680): could not associate with desktop session: Failed to connect to socket /tmp/dbus-YrJRGeQz2B: Connection refused
Nov 16 13:53:17 cheetah kernel: [ 2848.700419] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 13:53:19 cheetah pcscd: pcscdaemon.c:563:signal_trap() Preparing for suicide
Nov 16 13:53:20 cheetah pcscd: readerfactory.c:1348:RFCleanupReaders() entering cleaning function
Nov 16 13:53:20 cheetah pcscd: pcscdaemon.c:523:at_exit() cleaning /var/run/pcscd
Nov 16 13:53:20 cheetah kernel: [ 2851.393250] nfsd: last server has exited, flushing export cache
Nov 16 13:53:20 cheetah exiting on signal 15
Nov 16 13:54:55 cheetah syslogd 1.5.0#2ubuntu6: restart.
Nov 16 13:54:55 cheetah kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov 16 13:54:55 cheetah kernel: Cannot find map file.
Nov 16 13:54:55 cheetah kernel: Loaded 68675 symbols from 87 modules.
Nov 16 13:54:55 cheetah kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 16 13:54:55 cheetah kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 16 13:54:55 cheetah kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-g
eneric)
Nov 16 13:54:55 cheetah kernel: [    0.000000] Command line: root=UUID=bad28c50-7da1-495a-b98c-58b8f6e591f6 ro quiet splash 
Nov 16 13:54:55 cheetah kernel: [    0.000000] KERNEL supported cpus:
Nov 16 13:54:55 cheetah kernel: [    0.000000]   Intel GenuineIntel
Nov 16 13:54:55 cheetah kernel: [    0.000000]   AMD AuthenticAMD
Nov 16 13:54:55 cheetah kernel: [    0.000000]   Centaur CentaurHauls

```

I have an x86_64 system, although I don't think that has anything to do with it.

Suggestions?

Peter

---

