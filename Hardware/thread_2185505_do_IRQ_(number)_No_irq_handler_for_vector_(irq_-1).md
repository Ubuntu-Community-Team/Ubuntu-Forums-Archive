---
title: "do_IRQ: (number) No irq handler for vector (irq -1)"
date: 2013-11-02
forum: Hardware
---

### Post by rachel.greenham on 2013-11-02
Referring to old closed thread here: [http://ubuntuforums.org/showthread.php?t=1234983](http://ubuntuforums.org/showthread.php?t=1234983)

I'm suddenly getting this, like four years later, out of the blue:

```
root@twilight:/var/log# grep do_IRQ syslog
Nov  3 01:12:54 twilight kernel: [216399.077945] do_IRQ: 1.84 No irq handler for vector (irq -1)
Nov  3 01:13:44 twilight kernel: [216449.053265] do_IRQ: 2.164 No irq handler for vector (irq -1)
Nov  3 01:14:24 twilight kernel: [216489.033416] do_IRQ: 2.228 No irq handler for vector (irq -1)
Nov  3 01:22:24 twilight kernel: [216968.797607] do_IRQ: 1.168 No irq handler for vector (irq -1)
Nov  3 01:31:14 twilight kernel: [217498.536602] do_IRQ: 1.172 No irq handler for vector (irq -1)
Nov  3 01:34:54 twilight kernel: [217718.428108] do_IRQ: 1.110 No irq handler for vector (irq -1)
Nov  3 01:38:54 twilight kernel: [217958.313152] do_IRQ: 2.96 No irq handler for vector (irq -1)
Nov  3 01:42:04 twilight kernel: [218148.219503] do_IRQ: 1.209 No irq handler for vector (irq -1)
Nov  3 01:44:54 twilight kernel: [218318.132783] do_IRQ: 2.83 No irq handler for vector (irq -1)
Nov  3 02:02:14 twilight kernel: [219357.753440] do_IRQ: 1.91 No irq handler for vector (irq -1)

root@twilight:/var/log# grep do_IRQ syslog.1
root@twilight:/var/log# 


```

OK so it turns out it has been happening before today:

```
root@twilight:/var/log# zgrep do_IRQ syslog.*.gz
syslog.3.gz:Oct 30 22:32:47 twilight kernel: [223139.566758] do_IRQ: 2.49 No irq handler for vector (irq -1)
syslog.4.gz:Oct 29 19:33:07 twilight kernel: [126007.852959] do_IRQ: 3.206 No irq handler for vector (irq -1)
syslog.4.gz:Oct 29 20:48:27 twilight kernel: [130525.727247] do_IRQ: 1.115 No irq handler for vector (irq -1)
syslog.4.gz:Oct 29 21:27:41 twilight kernel: [132877.833660] do_IRQ: 0.37 No irq handler for vector (irq -1)
syslog.4.gz:Oct 29 21:27:51 twilight kernel: [132888.180721] do_IRQ: 1.69 No irq handler for vector (irq -1)
syslog.4.gz:Oct 29 21:35:39 twilight kernel: [133355.815829] do_IRQ: 1.117 No irq handler for vector (irq -1)
syslog.6.gz:Oct 27 22:44:38 twilight kernel: [825014.475192] do_IRQ: 2.101 No irq handler for vector (irq -1)
syslog.7.gz:Oct 26 11:22:45 twilight kernel: [694165.977941] do_IRQ: 0.138 No irq handler for vector (irq -1)
syslog.7.gz:Oct 26 19:27:25 twilight kernel: [723231.278900] do_IRQ: 2.113 No irq handler for vector (irq -1)
root@twilight:/var/log# 

```

So I don't know how long this has been going on, but it is the first time I noticed them; and I've had other reasons to look at the logs before now. (I looked half-expecting to see a failing drive logging sense/IO/reconnect errors and the like, but no sign of that.)

This is an Asus P6X58DE; not a brand new hardware, but running the latest bios for it; but mentioning because the old thread seemed to be linking this to a specific Asus mobo (not this one). Currently running Saucy all up to date, kernel:

```

root@twilight:/var/log# uname -r
3.11.0-12-generic

```

I think it may be related to sustained hard drive activity; and the actual real-world symptom I noticed that got me looking at logs and seeing this happening was an rsync from one (mdadm) raid to another unaccountably slowing down to a crawl, then speeding up again, at irregular but frequent intervals, after running well for some hours.

One of those RAID arrays is on the motherboard's own 6-slot SATA interface configured as AHCI; the other is on a sata_sil24 interface - a port-multiplying eSATA card with a 4-bay JBOD enclosure.

I don't appear to be suffering ill-effects beyond the slow-down in the data transfer rate, so not sure how much to worry. The old thread linked to above suggests a kernel param to add to make the messages go away, but it imparts no understanding about what's actually going wrong here, and whether just 'making the error messages go away' is a sensible thing to do or just an ostrich-head-in-sand thing.

I haven't done it yet because a: i don't know what it really does, or what downsides there might be b: I only just discovered the problem and c: am letting the rsync complete as there's not much longer to go. It's over four years since that thread was posted - and other non-ubuntu-specific search results for the same messages seem to be about that old too; but the motherboard itself isn't from *so* much later (early 2011); so wondering if there's any newer wisdom about this out there?

---

### Post by rachel.greenham on 2013-11-03
update, probably mostly for the sake of future googlers...

I set the kernel parameters as described in the original thread, ie: "pci=nomsi,noaer" and rebooted, and briefly got distracted when shortly afterwards the computer (which I was using remotely) appeared to freeze, but that was a red herring: unrelated whole-network error (I think my powerline ethernet sitting between the wired computers and the wireless ones (and the outer world) is failing). Machine was fine, but by the time I was sure of that I'd already unset those kernel parameters and was rebooting.

And since then, so far at least, I've had no recurrence of the issue. That is, with that kernel parameter NOT set after all.

My final theory, unless and until it raises itself again, is that it was actually a side-effect of certain settings I'd altered to try to speed up a raid reshape a few days earlier. As I hadn't done anything to make them persist beyond reboot, the next reboot, by settings things back to defaults, may have fixed it.

Those settings-changes were culled from [http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html) and were:

```

$ sysctl -w dev.raid.speed_limit_min=100000
$ echo 32768 > /sys/block/md126/md/stripe_cache_size
$ blockdev --setra 65536 /dev/md126
$ for i in sd{a,b,c,d}; do echo 1 > /sys/block/$i/device/queue_depth; done

```

These were all operating on the raid attached to the StarTech sata_sil24-driven eSATA card. (They also didn't even really make a difference; I reckon I was just up against the hardware limits.) My guess is that one of those might have futzed with the interrupt handling in a minor way.

---

