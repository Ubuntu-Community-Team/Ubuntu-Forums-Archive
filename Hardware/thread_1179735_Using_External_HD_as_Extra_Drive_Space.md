---
title: "Using External HD as Extra Drive Space"
date: 2009-06-06
forum: Hardware
---

### Post by X96 Design on 2009-06-06
I have a 640 GB external HD, and was wondering if there's a way I can "add" it into my storage space...

Basically, the two HD's (External+Internal) act as one, and my Internal 80 gig gets 640 gigs added onto it... [IMG]http://www.dynamicdrive.com/forums/images/smilies/smile.gif[/IMG]

Is this possible? If so, how?

Thanks
X96 D

---

### Post by kidders on 2009-06-07
Hi there,

It's possible, but not necessarily advisable. Theoretically, the resulting filesystem would be twice as likely to fail as your current one. (In practice, the failure probability would be much higher because one of the devices is external.) In a high percentage of cases, any data loss would be total. You'd also need to have enough alternative storage to back the contents of your internal hard disk up before you started.

You basically want to set up a RAID 0 array. Here are some pointers ...[LIST]
[*]You don't *have* to use all of the space on both disks for the array if you don't want to. You might, for example, want to set part of the external disk aside for some other purpose, or put your /boot on part of the internal drive that isn't striped.
[*]It's very important to consider your RAID stripe width (chunk size) and filesystem block size carefully. If your chunk size is too large, you'll be throwing away an opportunity to (often quite dramatically) increase I/O performance. Similarly, if your filesystem blocks don't align properly with the underlying stripes, you'll wind up creating a whole other performance problem.
[*]If you don't already do so, you'll _have_ to start making regular backups of your data, due to the significantly increased failure risk.
[/LIST]

Properly configuring a RAID array is a little complicated, but well worth taking some time over. Because they tend to be comparatively large (obviously!), re-creating them can be a major headache ... so it pays to get it right first time.

There are two other options that you might not have considered though ...

**Alternative I**

You could divide your current filesystem up into critical & non-critical chunks. For example, "critical" might include /boot, most of /usr, /etc, and so on. Non-critical might include /home, /usr/local, /var/www, and a few things like that. The point would be that large, non-critical parts of your filesystem could be moved onto your external disk, which would have certain advantages over RAID 0 ...[LIST]
[*]You wouldn't have to re-format your entire system ... you could just bolt the external hard disk onto it.
[*]If, for some reason, your external disk became unavailable while your system was running (eg due to cable failure), it would most likely continue to function, because all critical components of the OS would be stored on the internal one.
[*]If you were to drop/corrupt/break the external device somehow, your OS would still boot, and be at least basically functional.
[*]You would be able to use the external disk with more than one computer.
[*]You could use a different (ie better optimised for purpose) filesystem type on your external device that you might not normally choose to put your entire system on.
[/LIST]

Say your external disk was mounted at /mnt/external. You could move reasonably self-contained bits of your internal filesystem onto it (eg /opt or /home) like this ...

```
lsof | grep /home
(make sure you're not about to move something that's in active use)

cp -dpR /home /mnt/external
(copy, not move ... just in case!)

mv /home /home.old
( ... or you may prefer ... )
rm -Rf /home

ln -s /mnt/external/home /home
(symlink the external copy to the internal filesystem)
```

*Dis*advantages of this approach over RAID 0 are ...[LIST]
[*]Having bits of another filesystem symlinked to your root makes it (very slightly) more complicated to share files over NFS, because NFS is designed not to cross filesystems.
[*]Copying data between the internal & external filesystems will take time. For example, something like **mv /usr/something_big /home/stuff** would be instant right now (and would still be instant if you used RAID 0), because the data doesn't actually have to be moved ... it just has to be re-labelled.
[/LIST]


**Alternative II**

The internal hard disk represents just over 11% of your total available disk space. Arguably, there's not a lot to be lost by simply discarding it. You could move your entire system onto the external device, leaving nothing but /boot and some swap space on the internal one. Conceptually, this option might be a bit easier to set up, run & debug, but your computer would not boot without access to the external hard disk.

In failure terms, this option is probably the best of the three. Unfortunately, it may well be the worst performer, depending on how your external disk connects to your motherboard.

Anyhow, I hope that helps. The short answer to your question is "try RAID 0" ... assuming you don't prefer one of my alternative suggestions!

---

