---
title: "[SOLVED] Mount XFS at startup and make it writable"
date: 2008-10-18
forum: General Help
---

### Post by Woody1987 on 2008-10-18
I have just formatted one of my partitions to XFS and im having trouble mounting it properly at boot. I added an entry into fstab:

/dev/sdc2 /media/Recordings xfs defaults 0 0

This mounts the partition to the correct place but i cannot write to it. How do i solve this?

---

### Post by ajmorris on 2008-10-18
> **Woody1987 said:**
> I have just formatted one of my partitions to XFS and im having trouble mounting it properly at boot. I added an entry into fstab:

/dev/sdc2 /media/Recordings xfs defaults 0 0

This mounts the partition to the correct place but i cannot write to it. How do i solve 
this?

hi there,
try this fstab line:

```
/dev/sdc2 /media/Recordings xfs rw,user,auto 0 0
```

if this still doesnt work, you might like to try changing the permissions for user and group to be able to read+write+execute...:

```
sudo chmod ug+rwx /media/Recordings
```
although the above fstab line should make it so that it has read and write.


AJ

---

### Post by Woody1987 on 2008-10-18
Excellent, that worked, thanks

---

### Post by betweenthetines on 2009-05-26
I have a similar issue as the OP. I am running Kubuntu 9.04 on an ext4 partitioned drive and am trying to add a second HDD partitioned xfs. The drive automounts fine but I can only write to it when using dolphin (or konqueror, etc.) as root (kdesudo dolphin, etc.)

I tried ajmorris's solution:

> **ajmorris said:**
> 
try this...

```
/dev/sdc2 /media/Recordings xfs rw,user,auto 0 0
```

```
sudo chmod ug+rwx /media/Recordings
```

although the above fstab line should make it so that it has read and write.


but  still cannot write to the partition (drive) w/o root.

Here is the fstab line I'm using so far.

```

/dev/sdb1       /mnt/Multimedia1     xfs     rw,user,auto 0 0
```

 Have any suggestions? Thanks.

---

### Post by betweenthetines on 2009-05-26
Nevermind. Sometimes the solution is much simpler than the problem...

The above chmod command didn't do the trick, but this one does:

```
sudo chown -R username:username /mnt/Multimedia1
```

with my username replacing "username" in both places above.

---

### Post by banjo man on 2010-02-24
> **ajmorris said:**
> hi there,
try this fstab line:

```
/dev/sdc2 /media/Recordings xfs rw,user,auto 0 0
```


AJ

Just searched through the forums for a few min and found this post. Thought I'd post this for any kind of reference/use it's worth. :)


I was having problems with this as well, running 9.10 32 bit desktop version as a headless server with SSH and Samba and FreeNX server. the above fixed my problems. In fstab I had:```
/dev/sdc1 /media/Overflow500 xfs 0 0
```

Which I had for 2 volumes. I added rw,user,auto and my problems are gone! thanks!

side notes: ~4.75tb in 6 drives jbod-ish. three 500gb, 1x: 750, 1tb, and 1.5tb. The 1.5 is a newer WD green series, with the differently sized sectors, which ext3 didn't seem to like, so I went to xfs. Currently backing up and converting each drive's partitions to xfs.

---

