---
title: "Constant HDD activity, even when idle"
date: 2010-10-16
forum: Hardware
---

### Post by markdavidoff on 2010-10-16
I am running Ubuntu 10.10, and have noticed that my HDD is always making a noise as if it's reading/writing data, even when I'm not doing anything.

Is there a program which can tell me which process is accounting for all the activity, or which files, at least are constantly being read/written to?

---

### Post by luvshines on 2010-10-16
Maybe this is not that helpful but you can try to see if any file/folder is being accessed ( I generally do this when it is not able to unmount):
```
lsof /dev/<hdd-partition-name>
```

But it generally works for external drives. I doubt if it works for internal ones

---

### Post by markdavidoff on 2010-10-17
Yeah, this is my boot HDD.

lsof /dev/<hdd-patition-name> renders nothing for any partition.

using sudo results in:

> WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.

any alternative?
If only the system monitor had a HDD activity monitor for each process

---

### Post by markdavidoff on 2010-10-20
This problem is becoming very annoying!
10.04 never used to have this issue.

Does anybody else notice that their HDD is constantly reading/writing on 10.10?

What else can I do to track the cause of this bug?

HDD is always active, even at the login screen! (although, not as much)

---

### Post by utilitytrack on 2010-10-20
> **markdavidoff said:**
> Is there a program which can tell me which process is accounting for all the activity

```
$ sudo aptitude install iotop
$ iotop --delay=1 --only

```

**EDIT:**
Before check that your kernel properly configured:
```
$ cat /boot/config-`uname -r` | grep -e TASK_DELAY_ACCT -e CONFIG_TASKSTATS -e TASK_IO_ACCOUNTING -e CONFIG_VM_EVENT_COUNTERS
```

---

### Post by Unmensch on 2010-10-24
Hi, I'm having that problem on a Maverick netbook installation. Really bad in netbook mode, intermittent on gnome desktop mode. Seems to have something to do with the gnome power manager, but it's sporadic - sometimes starts after a few minutes, sometimes after hours, and I don't know how to check it - once it starts, the system slows down to unusable. It doesn't seem to happen without the gnome power manager, but maybe I haven't left it long enough. I'll try that as soon as the current job has finished.

---

### Post by markdavidoff on 2010-10-30
Turns out it was my mythbackend process (MythTV)

hope this helps anyone with a similar problem

---

