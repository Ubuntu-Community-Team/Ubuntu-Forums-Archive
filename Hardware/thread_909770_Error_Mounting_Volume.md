---
title: "Error Mounting Volume"
date: 2008-09-03
forum: Hardware
---

### Post by gutsy galt on 2008-09-03
I'm running Hardy and am receiving an error message when trying to mount a volume that was previously working fine.  It's a second internal hard drive, mount point /media/disk.  Status displays as unmounted after restart.  I attempt to mount and get this error message:

Cannot mount volume.
Unable to mount the volume.
Details
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)


This was working fine before. However, error message leads me to think I need to re-define the mount point somehow?

Any ideas?

---

### Post by Mister.Vash on 2008-09-03
Take a look at this link, they have the solution in the comments
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

---

### Post by gutsy galt on 2008-09-07
Thanks, Mr. Vash.

That worked, although as a novice it was quite a rabbit hole for me to follow.  Interesting that my drive is an internal hard drive but exhibits the same problem as if it were external.

Thanks again
--g galt

---

