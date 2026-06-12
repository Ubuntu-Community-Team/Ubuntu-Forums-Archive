---
title: "Making an external file system"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2008-02-15
Hi forum, &#9786;

I have a one terabyte external hard disk that is going to be mounted on my Debian system and used for storing multimedia, and a backup of my home folder. (As individual files.)

Please help me fill in the two red questionmarks below.

**# [mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3) -m [color=red]?[/color] -O dir_index,has_journal,sparse_super -T [color=red]?[/color] -L "Terabyte storage" /dev/sdb1**

First question mark: Do I need to reserve any or how many percentage of an one terabyte drive for the root user?
Second question mark: What file system type would my usage be grouped under? The various options did not make any sense to me.

Anything else I should specify for my usage?

---

### Post by kidders on 2008-02-17
Hi there,

You don't ever *need* to reserve any space on an Extended filesystem. It's standard practice to reserve 5%, but I would question the wisdom of that on a filesystem that isn't going to be mounted someplace like / or /var. Typical reasons for reserving space are...[LIST]
[*]To reduce fragmentation caused by small but continuous writes to files by the root user, and
[*]To allow privileged processes to continue to function after a filesystem runs out of space.
[/LIST]

If you leave the "-m" option out, 5% of your new filesystem will be reserved automatically. Normally, people only use it to set the amount of reserved space to zero ... something you might want to do in your case. Formatting your _root_ filesystem in this way could seriously degrade its long-term performance though.

As for the "-T" option, it controls the default values of mkfs.ext3's arguments. It allows you to set up filesystem "profiles", and reproduce specially tuned filesystems again and again, by specifying "-T profile_name" in the mkfs command.

1TiB is quite a lot of disk space ... imagine you were going to use it to log SMS messages from a commercial gateway. After a while, two things would happen...[LIST]
[*]Using typical default options, an Extended filesystem would allocate blocks in 4k chunks. Since text messages wouldn't really exceed 200 bytes in length, this would result in massive disk space wastage. Theoretically, the maximum number of messages you could store under those circumstances would be 268,000,000 ... despite the fact that an entire terabyte of disk space *should* allow you to store about 5.5 billion of them.
[*]On top of that, the usual inode density for an Extended filesystem is 1:8k. Basically, this implies an average file size of 2 blocks. Were the average file size to drop below that (which it would in my example), the filesystem would lose the ability to allocate new files after about 120 million messages, wasting almost 98% of the available disk space.
[/LIST]

As you can imagine, the more disk space you have, the more important it becomes to optimise it correctly. If, for example, you were able to say "None (or *almost* none) of the files on my backup/media disk will be less than 1MiB in size", it might be appropriate to use the default "largefile" filesystem profile, which would result in a noticeable performance boost. The trade-off is that if you were to later discover that you'd made a mistake, you'd have no option but to reformat the filesystem, to recover all the storage capacity you'd have wasted by storing small files.

This post is getting quite long-winded, so I'll finish with a quick question ...

Have you considered filesystems other than Ext3, or have you chosen it on purpose?

---

