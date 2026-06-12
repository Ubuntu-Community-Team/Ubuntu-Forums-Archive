---
title: "Do Not Format = wipe?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by bmartin on 2009-04-23
I had separate partitions for / and /home before I installed 9.04.

I marked them both as ext4 in the advanced partition editor; I marked / for format and /home to be left as-is.

The installer formatted my home directory... everything on my computer is gone. It's all recoverable, except my ddclient.conf, apt-cacher settings, etc.

Just thought I'd throw it out there as an issue. Yikes!

---

### Post by Sam Lars on 2009-04-24
Yeah, I had the same situation when I installed Jaunty.  I think I realized it was going to want to reformat the /home if I changed it to ext4, so I converted it later.

---

### Post by bmartin on 2009-04-24
Hmm... but ext4 is backward- and forward-compatible with ext3, so I don't see why it would be necessary.

Well, anyways, I lost a lot of data, but the important stuff was backed up, so I guess I'm fine. I remember unchecking the format box, but upon replaying the incident, after you click "OK", the format box is automatically checked and disabled (even if you unchecked it in the dialog). That was a nasty surprise.

---

### Post by Sam Lars on 2009-04-24
You can mount an ext3 drive as ext4, and it will remain forwards and backwards compatible, using only compatible features of ext4.  You can mount it as ext3 later and it should be fine.
If you format a drive as ext4, though, it will use all ext4 features.  You will need a kernel with ext4 support to read it.

---

### Post by bmartin on 2009-04-24
> **Sam Lars said:**
> You can mount an ext3 drive as ext4, and it will remain forwards and backwards compatible, using only compatible features of ext4.  You can mount it as ext3 later and it should be fine.
If you format a drive as ext4, though, it will use all ext4 features.  You will need a kernel with ext4 support to read it.
I didn't realize there were incompatible features in ext4. Thanks for the info. I guess I'll have access to all of them with my freshly-formatted ext4 partition.

When I upgraded my fiancee's computer, I left the partition settings alone... I'll have to change the mounts to ext4 later. I remember something about update-grub needing to be run afterward, if the kernel resides on an ext4 partition.

---

### Post by graysky on 2009-04-24
As an aside, when you convert ext3-->ext4 you aren't going to benefit from the increases in speed via extents on the existing files; new file will.  You need to format the partition to ext4, then copy over the files.  If you have a dedicated /home partition, this is very easy via tar assuming you have the needed space on another partition.  This should do it:
```
$ sudo tar zcvfp /path/to/backup/partition/home-backup.tar.gz /home
```

Now format your 'old home' partition to ext4 and restore the backup.

Alternatively, you can rsync it.  This should do it:
```
$ cd /
$ sudo rsync -avxu --progress /home /path/to/backup/partition
```

---

### Post by Sam Lars on 2009-04-24
> **graysky said:**
> As an aside, when you convert ext3-->ext4 you aren't going to benefit from the increases in speed via extents on the existing files; new file will.

Are you talking about just mounting an ext3 drive as ext4 or actually converting it?
If converting it to ext4 doesn't do that, what *does* it do that's different from just mounting it as ext4?

---

### Post by graysky on 2009-04-24
> **Sam Lars said:**
> Are you talking about just mounting an ext3 drive as ext4 or actually converting it?
If converting it to ext4 doesn't do that, what *does* it do that's different from just mounting it as ext4?

I dunno about mounting ext3 as ext4... I talking about actually converting the ext3-->ext4.

---

### Post by Sam Lars on 2009-04-24
Ah, I think you're right, converting will only apply to new files, not existing ones.

---

