---
title: "Mounting LDM arrays (Dynamic Disks) the right way"
date: 2009-05-08
forum: Hardware
---

### Post by FuriousGeorge on 2009-05-08
If I currently want to mount my windows partition, I need to do this:

mdadm --stop /dev/md3 (I must have screwed something up during setup, because /dev/md3 is already in my mdadm.conf)

mdadm **--build** -l 0 -n 2 **-c 64** /dev/md3 /dev/sda3 /dev/sdb3

mount -t ntfs-3g /dev/md3 /media/X

That's easy enough, I just need to specify "build" instead of "assemble" and specify a chunk size of 64.  Now what if I wanted it to happen automagically?

I tried adding chunk=64 to mdadm.conf, despite not seeing that in the mdadm.conf man page, and naturally that didn't work.  I'm assuming that if I put the right thing in mdadm.conf, then I could just mount it with that UUID in /etc/fstab.

Does anyone know how to do this?  I've googled near and far, and I just can't find it.

---

### Post by FuriousGeorge on 2009-05-13
Perhaps there is no way to mount LDM partitions in mdadm.conf.  I've been over the man page time and again, and I'm just not seeing it there or on the internets.

So I guess I can just manually work it into my startup then.  I was thinking of just making a simple sh script and sticking it in some appropriate start up script.

Does that sound good, or does someone have a better suggestion?

---

### Post by FuriousGeorge on 2009-05-13
bump?  This is the busiest topic I've seen in my life.  10 hours, four pages

---

