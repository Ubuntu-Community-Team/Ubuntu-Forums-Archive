---
title: "Unable to mount harddrive due to corrupt windows installation on disk. (SATA)"
date: 2008-07-15
forum: Hardware
---

### Post by pYrO1v1aniac on 2008-07-15
Unable to mount harddrive due to corrupt windows installation on disk. (SATA)

Is there anything that can be done about this? The harddrive itself is dying, however, still pseudo-accessible (windows will attempt to boot, but fail). 

Ubuntu can detect its two partitions but can access neither.

Error message is as such 

"...$logfile indicates unclean shutdown..."
"...operation not supported because NTFS is marked to be in use..."

The two choices it offers are to go into windows and shut down properly (not an option)
Or an alternative for if I don't have windows (a terminal command line which doesn't work)

Then, this error message disappears, and is replaced with 'Opening 56.6gb Media' then-

"Unable to mount location"
"...DBus error org.freedesktop.DBus.Error.NoReply: Did not recieve a reply..."

I only wish to access the drive to retrieve files from it. A recovery command would do.

If it is important, my main harddrive is now a 160gb partitioned USB removable drive, this is what Ubuntu is running from.

Help please.

---

### Post by pYrO1v1aniac on 2008-07-15
Bump. I've tried all the other SATA mount systems suggested in other threads, none of them seem to work.

---

### Post by gpegasus82 on 2008-07-30
I have exactly the same problem :(

and i'm a newbie

---

### Post by evets25 on 2008-07-30
This may help somewhat... I do know that with NTFS partitions, windows MUST be shut down cleanly in order to be able to read the drive properly in linux, or mount it or work with it at all.

---

### Post by Jordanwb on 2008-07-30
In the error message there should be a command that says something like "mount -t ntfs /dev/sda1 /media/disk -o force" prefix that with sudo and the drive will work.

---

