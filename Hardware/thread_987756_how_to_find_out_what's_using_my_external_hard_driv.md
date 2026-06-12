---
title: "how to find out what's using my external hard drive"
date: 2008-11-19
forum: Hardware
---

### Post by faust99 on 2008-11-19
Does anyone know how to determine which process is using my external hard drive, so I can kill the process and unmount?

Every now and then I need to unmount my hard drive in the middle of a backup, but using kill to stop the sbackup process does not seem to work, as when I go to unmount, I get an error telling me that the hard drive is being used by some process. Unfortunately I don't know which process. Inevitably I end up rebooting, which is not the ideal method.

Either I am using kill incorrectly or there are other process that need to be killed of which I am unaware.:confused:

---

### Post by cariboo on 2008-11-19
Linux doesn't always write data to the hard drive at the time you are doing something. It delays the file write some times. You have to wait until the write is finished before you can unmount the drive.

To find out if you are killing sbackup completely open up a Applications-->Accessories-->Terminal and type:

```
ps ax | grep sbackup
```

This will show you if an sbackup process is still running.

Jim

---

### Post by faust99 on 2008-11-20
> **cariboo907 said:**
> Linux doesn't always write data to the hard drive at the time you are doing something. It delays the file write some times. You have to wait until the write is finished before you can unmount the drive.

Yes I know but I don't think that is the issue because I can leave it for a long time after (apparently) killing the process, and it still won't let me unmount.

> **cariboo907 said:**
> To find out if you are killing sbackup completely open up a Applications-->Accessories-->Terminal and type:

```
ps ax | grep sbackup
```

This will show you if an sbackup process is still running.

Jim

Thank you, I'll try it next time.

---

