---
title: "gparted doesn't see /dev/mapper devices in 10.04"
date: 2010-11-04
forum: Hardware
---

### Post by fermulator on 2010-11-04
I'm not sure when this started to not work, anyone have any insight?

I have "motherboard software raid" (which uses dmraid).
> fermulator@fermmy:~$ dpkg --list | grep dmraid
ii  dmraid                                1.0.0.rc16-3ubuntu2                             Device-Mapper Software RAID support tool
ii  libdmraid1.0.0.rc16                   1.0.0.rc16-3ubuntu2                             Device-Mapper Software RAID support tool - s

/dev/mapper:
> fermulator@fermmy:/dev/mapper$ ls
control               isw_dihagdeiig_RAID01  isw_dihagdeiig_RAID03  isw_dihagdeiig_RAID06  isw_fegbaeadg_RAID0_SSD   isw_fegbaeadg_RAID0_SSD2
isw_dihagdeiig_RAID0  isw_dihagdeiig_RAID02  isw_dihagdeiig_RAID05  isw_dihagdeiig_RAID07  isw_fegbaeadg_RAID0_SSD1  isw_fegbaeadg_RAID0_SSD3


When I open gparted though, it doesn't show any of the /dev/mapper devices (so the partitions it sees are useless -- it sees /dev/sda, /dev/sdb, etc., but we can't play with these physical devices because they're part of the RAID0 arrays)

gparted says that it's version "GParted 0.5.1"

Bwah?

---

### Post by ronparent on 2010-11-05
Install kpartx. It's needed for gparted to see fakeraid partitions.

---

### Post by fermulator on 2010-11-05
That did the trick.

Does a bug exist?

Either:
 A) kpartx needs to be a requirement for gparted (although I realize this doesn't make a whole lot of sense because not everyone uses dmraid...)
or,
 B) gparted needs to be able to detect that dmraid is installed, and there are /dev/mapper devices, and should notify the user upon launch that "kpartx is required, should I install it for you?"

---

### Post by IcarusR on 2010-11-05
Suggest you ask the question on the gparted forum as the developers will be in a much better position to answer your questions & maybe act on your request.

[http://gparted-forum.surf4.info/]("http://gparted-forum.surf4.info/")

Can you please mark the thread as solved, it helps others searching for similar topics.

---

### Post by ronparent on 2010-11-05
I reported as a bug [bug 600729] for 10.04 and it was supposedly fixed. But from time to time I see it reappear as a problem in this forum - most often associated with an inability to install.

---

### Post by fermulator on 2010-11-07
Thanks all.  Marked as [SOLVED], and submitted on gparted forums for further input from development: [http://gparted-forum.surf4.info/viewtopic.php?id=14405](http://gparted-forum.surf4.info/viewtopic.php?id=14405)

---

### Post by psusi on 2010-11-07
It has been fixed upstream since 10.10 was released.  Hopefully it will work without kpartx in 11.04.

---

