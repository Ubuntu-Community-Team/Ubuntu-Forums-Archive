---
title: "Slow Boot - &quot;Loading Hardware Drivers&quot;"
date: 2008-05-14
forum: Hardware
---

### Post by romojap on 2008-05-14
I'm experiencing a slow boot time.  bootchart shows modprobe is doing a lot of work, and my "research" has shown that modprobe loads drivers.  Sure enough, when I boot with "quiet" disabled, a lot of time is spent on "Loading Hardware Drivers."  I'm not sure where to start... :(

---

### Post by steveneddy on 2008-05-31
I am having the same issue, but I can't seem to be able to pinpoint it.

I can't even get bootchart to install and run in Hardy 64 bit.

kernel=2.6.24-17-generic

I think after I installed ardour just to check it out, but I can't remember when exactly the boot issue started.

Any help appreciated.

---

### Post by crispinb on 2008-06-01
My machine  (using Hardy) is also booting very slowly. The odd thing is that this has only recently started (not sure exactly when because I don't reboot that often). 

The appearance of the boot process has also changed: it runs for 10 seconds or so at the splash, with the progress indicator going. The the progress indicator stops, and nothing happens for up to a minute. Then the splash disappears and I get the console, starting at "Reading from files needed to boot...", and all's OK from there.

Anyone know why the slowdown? And why the apparent minute-long freeze?

---

### Post by steveneddy on 2008-06-01
I even turned off the usplash, did the hpet time fix and maybe one other that i can't remember.

None if this has helped me.

My boot hangs on "Loading Hardware Drivers".

Hardy 8.04, 2.6.24-17-generic 64 bit

Intel Core 2 Duo

---

### Post by crispinb on 2008-06-01
OK, my problem's fixed. I think it's different from what you other guys are experiencing. The key diagnostic for my problem was a non-quiet boot hanging for over a minute at "Waiting for resume device".

In case anyone else has this problem:

It's related to this bug: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358)

Essentially, the swap partition's UUID has changed, and initram is holding up the boot process waiting for the swap partition identified by the non-existent UUID.

The fix is:
- do a mkswap on the desired swap partition, and record the UUID that mkswap outputs
- replace the old UUID with this new one in fstab and /etc/initramfs-tools/conf.d/resume
- update initramfs (sudo update-initramfs -u)
Reboot and all should be OK (reduced my boot time from 2.5 mins to about 40s)

---

### Post by steveneddy on 2008-06-01
> **crispinb said:**
> OK, my problem's fixed. I think it's different from what you other guys are experiencing. The key diagnostic for my problem was a non-quiet boot hanging for over a minute at "Waiting for resume device".

In case anyone else has this problem:

It's related to this bug: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358)

Essentially, the swap partition's UUID has changed, and initram is holding up the boot process waiting for the swap partition identified by the non-existent UUID.

The fix is:
- do a mkswap on the desired swap partition, and record the UUID that mkswap outputs
- replace the old UUID with this new one in fstab and /etc/initramfs-tools/conf.d/resume
- update initramfs (sudo update-initramfs -u)
Reboot and all should be OK (reduced my boot time from 2.5 mins to about 40s)

How do I tell if this is my issue?

I'm interested and really want to try it, but I would like a test or qualifier so I can finally pin point the issue to address my concern.

---

### Post by crispinb on 2008-06-01
> **steveneddy said:**
> How do I tell if this is my issue?

I'm interested and really want to try it, but I would like a test or qualifier so I can finally pin point the issue to address my concern.

I'm not an expert, but it seems to me that if your boot really is stopping or slowing on "Loading Hardware Drivers", then yours must be a different issue, so it wouldn't be worth trying this fix.

Mine was stalling at "waiting for resume device", which makes sense given the bug report I linked to.

---

