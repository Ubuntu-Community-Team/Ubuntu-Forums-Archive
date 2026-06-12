---
title: "Timed out running command-line mount (floppy)"
date: 2016-07-16
forum: Hardware
---

### Post by humanist2 on 2016-07-16
Lenovo ThinkCentre i386

I hooked up a floppy drive and was successfully accessing floppy disks. The system was mounting and reading information (but couldn't write, but that didn't matter to me). I have a ton of floppy disks I need to access and consolidate files from - I'm moving them all over onto my computer. It was running fine, and then all of a sudden, it wasn't.

After the drive stopped working out of nowhere, it told me that /dev/fd0 was not a valid block device.

The full error message was this: 

Error mounting system-managed device /dev/fd0: Command-line `mount "/media/floppy0"' exited with non-zero exit status 32: mount: /dev/fd0 is not a valid block device

I went there, and the "fd0" file existed, so I looked online for fixes.

[HR][/HR]
```
sudoedit /etc/group
```

On the "floppy" line, I added "user" (my user account name) to ensure I'd have permission to access/mount it. I had access before doing this, and my username wasn't there, but that was a suggestion I found online.

I rebooted, and retried. Now, I instead get the error message: Timed out running command-line `mount "/media/floppy0"'

[HR][/HR]
```
sudoedit /etc/fstab
```

The relevant code is:

```
/dev/fd0  /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0
```

[HR][/HR]
```
lsmod
```

lists "floppy" with a "used by 0".

[HR][/HR]
Using Nautilus and browsing to "floppy 0", right-clicking and choosing "mount" gives the same "timed out" error message.

[HR][/HR]
```
mount -t msdos /dev/fd0 /media/floppy0
```

returns: "/dev/fd0 is not a valid block device"

(that's the same error message I was receiving before adding 'username' to /etc/group)

It is recognized by the BIOS, but no longer by Ubuntu, or by the program GParted. I've attempted mounting the floppy drive both with, and without, a floppy disk inside of it. Neither option works.

---

### Post by humanist2 on 2016-07-17
More stuff to add (yes, I'm still trying to figure it out):

Just booted from grub using the previous kernel version, and that did not solve the problem (by letting me mount the floppy drive / disk) either.

I also loaded the default BIOS settings (just in case an edit to that broke it), yet, nothing.

Finally, I took the floppy drive out, and blew air in an attempt to clean it out.

None of these actions have been useful, either.

Does anyone have any insight? I'm about to reinstall Ubuntu, since nothing's working, but some solutions would be nice, if anyone's got them, as it would be used by others, later. And if someone can figure out a solution, I'll attempt to "break" it again to see if the solution works.

---

### Post by weatherman2 on 2016-07-17
Before you re-install Ubuntu, try booting a live USB of Ubuntu first and try to get the floppy working there again.

If you can't get it working there using the same method that worked before, re-installing Ubuntu won't help.  In that case, the floppy drive may have failed.

---

### Post by humanist2 on 2016-07-18
I got it!! I had to mount with vfat, first, with some of the floppies. If you run into this problem, keep /etc/fstab and /etc/group just as they are (except maybe add your username to /etc/group, after floppy:x:25).

So:
```
sudoedit /etc/group
```
1) Add your username after floppy:x:25 if it's not already there.
2) Press Ctrl+x to exit.
3) Press "Y" for "Yes", and ensure the filename saves to /etc/group instead of that temporary saving spot, and hit Enter, then press "Y" again to overwrite.

```
mount -t vfat /dev/fd0 /media/floppy0
```
Then after it mounts, use Nautilus to navigate to the Floppy Disk folder, and your files should show up.

If the floppy disks aren't mounting, just try mounting with different with different filesystem types.

... I don't know if that was obvious to anyone else, but I didn't get any responses, so maybe it wasn't ...

Yea, if you run into this problem, try mounting with different filesystem types, BEFORE you navigate to the floppy folder.
"mount -t vfat"
"mount -t msdos"
etc...

---

### Post by sudodus on 2016-07-18
Thanks for sharing your solution :KS

---

### Post by humanist2 on 2016-07-19
> **sudodus said:**
> Thanks for sharing your solution :KS

What goes around, comes around. I'll need help in the future, I've been helped before, and the more people who have knowledge, the better it is for all, and all individuals are included in "all".

It's turning out that this works for ALL of the floppies, after all.

Just as an extra suggestion:

1) Mount your floppy, trying varied filesystem types.
2) Pull your data off.
3) Unmount your floppy.
4) ```
mformat a:
``` (formats your floppy to MSDOS)
5) "Enter"

Steps 3-5 wipes the floppy, and allows the floppy to be read quicker, when reusing them in the future.

It ***is*** recognized by Disks.
It ***is not*** recognized by GParted.

That's how it works for me, at least. And they are all working now, so this is a consistently good option.

---

