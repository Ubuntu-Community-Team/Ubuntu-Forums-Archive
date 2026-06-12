---
title: "Assembling RAID arrays.... failed"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by ittiam on 2007-03-05
During the boot up sequence, i get

Assembling RAID arrays.... failed

But everything works fine in my edgy. Anyone has any idea what is causing this and how to fix it?

And also before that i have
 Loading Hardware drivers ...failed....this i know is because of my intel i810 graphics card! But RAID i dont have any reason

---

### Post by segflaunt on 2007-03-06
Probably the same problem I have.

My imperfect understanding of the problem is that udev does not properly create SCSI/libata device nodes, and tries to assemble the array[s], and fails.

[https://launchpad.net/ubuntu/+bug/86384]("https://launchpad.net/ubuntu/+bug/86384")
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=403136]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=403136")

According to the debian bug, the fix is to upgrade udev. I'm hoping they decide to include a newer udev in feisty final. I think this breaks a lot of peoples' systems.

If you're desperate, you can boot with "break=premount", and you're in a shell in the initramfs. Start the udev stuff manually, then try to unbreak things. I have about an 85% success ratio.

(not sure if all the sourcing is necessary)
. /conf/arch.conf
. /conf/initramfs.conf
. /scripts/functions
/scripts/init-premount/udev
mdadm -S /dev/md?
mdadm -A --scan

...and if that works, exit the shell, and the boot sequence will continue.

---

### Post by arcterex on 2007-03-09
Hey, thanks for the tip, confirmed it works for me as well (vmware herd5 install, 3 drives, raid1 /boot raid5 /).

Is there a bug in this that's posted?  This seems a pretty major thing to not have fixed before release, and this is a pretty core component that'll need testing, and april isn't that far off....

---

### Post by segflaunt on 2007-03-10
I'm trying my best to get it addressed through the bug system, but I don't know what's going on.

Hopefully someone responds sometime.

---

### Post by segflaunt on 2007-03-27
The fact that I have been able to boot twice since yesterday's updates is tacit confirmation that something got either mitigated or fixed, and I believe it to have been a bit of a reorganization of the scripting ubuntu uses to help udev initialize things.

I noticed an initramfs-tools update just as I was going to test a udev-105 ubuntu .deb, so I applied that update, and have been able to boot since then.

---

