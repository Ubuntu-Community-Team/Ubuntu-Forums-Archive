---
title: "Hard drive spin-up troubleshooting"
date: 2009-11-12
forum: Hardware
---

### Post by Cr0n_J0b on 2009-11-12
Hi all,

I'm working on a project to spin-down all of my hard drives (except the boot disk) when they aren't accessed.  I'm running a fresh install of 9.10 and I have the following set of drives:

/dev/sda1 -- boot
/dev/sdb1 -- HDS 500GB member of md0 raid 0
/dev/sdc1 -- SEA 500GB member of md0 raid 0
/dev/sdd1 -- MAX 500GB member of md0 raid 0
/dev/sde1 -- SEA 750GB member of md0 raid 0
/dev/sdf1 -- SEA 750GB member of md0 raid 0
/dev/sdg1 -- SEA 750GB member of md0 raid 0
/dev/sdh1 -- WD 1000GB member of md3 raid 5
/dev/sdi1 -- WD 1000GB member of md3 raid 5
/dev/sdj1 -- WD 1000GB member of md3 raid 5
/dev/sdk1 -- WD 1000GB member of md3 raid 5

The raid volumes are all setup with mdadm and they all work just great.

I have all of the drives set to spindown after 30 minutes of non activity.

My issue is that the drives will spin up every 30 minutes or so.  In the case of the md3 volume, I can see a bit of disk I/O activity, and then it will spin up.

In the case of the md0 set, I don't see any disk activity...in fact, I've unmounted the volume to insure that nothing is writing to it, but it's still spinning up.

I have lmsensors loaded and smartctl, but I don't think that there are daemons in either that should be checking the drives.

I'm just not sure how to figure out what is causing this.

I have the following hdparm.conf file.

```

/dev/sdb {
	spindown_time = 241
}
dev/sdc {
	spindown_time = 241
}
dev/sdd {
	spindown_time = 241
}
dev/sde {
	spindown_time = 241
}
dev/sdf {
	spindown_time = 241
}
dev/sdg {
	spindown_time = 241
}
dev/sdh {
	spindown_time = 241
}
dev/sdi {
	spindown_time = 241
}
dev/sdj {
	spindown_time = 241
}
dev/sdk {
	spindown_time = 241
}

```

---

### Post by Cr0n_J0b on 2009-11-13
anybody have a clue on this?

---

### Post by Cr0n_J0b on 2009-11-15
Well, I'm not sure if anyone else is having this issue, but I think I'm the track of figuring it out.  It seems that there is a bug in the libatasmart script that's called by devkit-disks.  It queries the drives for smart information about every 30 mintues and thus spins up the sleeping drives.  It's supposed to query them quietly without waking them, but the bug causes a spin-up event.  Someone put out an patched to the libatasmart package ...  I'm testing this now.  I'll report on my results.

here is the link.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/435190](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/435190)

here is the patched package location.

[https://launchpad.net/~ubuntu-desktop/+archive/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ppa)

here is a link from RedHat following this.

[https://bugzilla.redhat.com/show_bug.cgi?id=491552](https://bugzilla.redhat.com/show_bug.cgi?id=491552)

I have the patch applied and my drives are napping right now.  I'll let you know if they get a rude wakeup call.
:D

---

### Post by Cr0n_J0b on 2009-11-17
For anyone who cares about this.  The patched package above works great and fixed the isse.

---

