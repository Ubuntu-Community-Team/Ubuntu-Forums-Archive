---
title: "Cant find USB Drive in /dev"
date: 2008-08-21
forum: Hardware
---

### Post by fwre01 on 2008-08-21
I cant find a USB drive i plugged into my server in the /dev dir.
[B]
lsusb shows this...[/B]

```
[root@server backup]# lsusb
Bus 001 Device 001: ID 0000:0000

```

**an fdisk -l show this...**

```

Disk /dev/sda: 36.7 GB, 36778545152 bytes
255 heads, 63 sectors/track, 4471 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825        4461     5116702+  82  Linux swap / Solaris

Disk /dev/sdb: 36.7 GB, 36778545152 bytes
255 heads, 63 sectors/track, 4471 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4471    35913276   fd  Linux raid autodetect

Disk /dev/sdc: 36.7 GB, 36778545152 bytes
255 heads, 63 sectors/track, 4471 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4471    35913276   fd  Linux raid autodetect

Disk /dev/sdd: 36.7 GB, 36778545152 bytes
255 heads, 63 sectors/track, 4471 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4471    35913276   fd  Linux raid autodetect

Disk /dev/md0: 73.5 GB, 73549742080 bytes
2 heads, 4 sectors/track, 17956480 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

```

I have 4  SCSI hard drives and three of them are in a software raid 5 cluster, and is mounted at /vz. The other hard drive is mounted at /. 

**mount show this...**

```
/dev/sda1 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/md0 on /vz type ext3 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)

```

Is there anyother way i can see where my USB drive is appearing? maybe tailing a log file? but i dont seem to have a /var/log/syslog. I know the USB drive hasnt got a partition on it. I was goint to format it but obviously cant because i cant find it.

Anythought?

---

### Post by pytheas22 on 2008-08-21
Maybe something strange is going on.  Put the drive in and then immediately run:
```

dmesg | tail
```

It should hopefully give some clue as to what the system is doing with the device.  Normally Ubuntu would auto-mount USB sticks, but it may be ignoring yours since it has no file system on it--you'd think that it would still be in /dev somewhere, but Ubuntu may be doing something unexpected.

Also are you sure you don't have a /var/log/syslog?  If so there may be issues with your system, like it didn't get installed completely.

---

### Post by fwre01 on 2008-08-21
i dont have a syslog file, i have a dmesg and a messages log file, which i tailed and nothing happened when it was unplugged OR plugged back in again.

Also i did an ls -la /dev > /tmp/output1 when it was unplugged. Then ls -la /dev > /tmp/output2 when it was plugged in and diff'd the two together and there was no difference (except a tty, which i assume is for the ssh session)

Hmmmm...... so im a bit stuck. im not sure what else to look at

---

### Post by pytheas22 on 2008-08-21
That's really strange that you have no syslog.  Is syslogd running?

You may also want to try the USB stick in another machine just to make sure it actually works, if you haven't already.  You could also try formatting it to see if Ubuntu will read it then (didn't it come pre-formated?)

---

### Post by fwre01 on 2008-08-21
Im pretty sure the drive works, iv had it working on a windows box, just before i moved it over to the server i blew the partition away (probably not a smart move) because it was using NTFS. ill have to check to see if syslogd is running. it might not be. Thanks for your help, ill try formatting it then moving it back to the server

---

