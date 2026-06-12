---
title: "Drive Pooling"
date: 2018-05-12
forum: Hardware
---

### Post by zeonotaku on 2018-05-12
I have 2 internal 4TB drives that I'd like to pool together to store my movies among possibly other external 3TB drives into a pool with parity.  I've done RAID's before but my bosses keep telling me about drive pooling.  I was planning on using Windows but unfortunately my key is no good so I'm opting for Ubuntu.

I keep hearing about mergerfs but I don't see it in the software.  Can somebody please help with a quick how-to or something?

---

### Post by TheFu on 2018-05-12
Welcome to the forums.

There are many different solutions, but none of them are really good ideas for a 2 disk set, IMHO.  Using USB storage as part of this is a terrible idea.  USB connectors aren't as solid as people think.  If it is eSATA or Infiniband, great. Those connectors have screws.  I'd also be concerned about 3TB disk. That size and multiples of 3 seem to have 2x the failure rates for other sizes according to Backblaze reports.

For me, all storage design begins with how you will back it up and restore WHEN there is a failure. When, not if. Learned this at my day job.  So, if you have a good way to backup 8TB of storage, then go for it.  If not, please consider using 2 separate disks and letting the media server merge them into the space you want.  Both Kodi and Plex do this already.  I have 4 separate disks logically merged into my "Movies" and "TV" libraries by Plex.  To the OS, they are separate.  This makes backups, restores 100x  easier. Had a 4TB disk fail about a year ago. It was a minor inconvenience, zero data loss.

Ok ... so if you still want to merge the file systems, I'll start with how I'd do it, in my order of preference around how solid each solution is.
1) ZFS - this is what FreeNAS and similar storage-centric distros use). It likes 6 physical disks for pools, but you can use 1 or more.  ZFS is supported on Ubuntu for non-boot storage.  It is the only file system that actually validates what was written to disk actually arrived ON THE DISK.
2) LVM - this has been proven to work by enterprise admins for 20+ yrs. LVM is extremely flexible. You can choose to concatenate or interlace the storage (like RAID0). If 1 disk fails, total data loss.  I use LVM for all my physical disks, but not to merge them together.  LVM (and ZFS) have some advance capabilities that make getting homogeneic data backups from a running system possible, regardless of how busy the DB might be. That is very handy and supports zero downtime backups.
3) all the others ... like let me google ... UnionFS, mhddfs, Aufs, Overlayfs, etc. [https://www.cyberciti.biz/faq/mhddfs-linux-combines-a-several-mount-points-into-single-one/](https://www.cyberciti.biz/faq/mhddfs-linux-combines-a-several-mount-points-into-single-one/) ...

Regardless of which solution you choose, be certain to google for problems. They all have problems and possible data loss.

Regardless, look for how-tos from reputable sources FOR YOUR SPECIFIC release.  I've never heard of mergerfs.

None of these tools are really designed for beginners. I can't tell from what you've written how expert you are.

---

