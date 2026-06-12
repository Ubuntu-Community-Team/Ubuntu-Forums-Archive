---
title: "Formatting external hard drive?"
date: 2010-04-23
forum: Hardware
---

### Post by 300Z on 2010-04-23
I just reformatted my new 1tb external hdd to ext4fs and only had 870gb available after reformatting it as opposed to ~931.51gb total (like it says on gparted) so I used sudo tune2fs -m 0 to set it to 0% (like described in [this]("http://ubuntuforums.org/showthread.php?t=1433869&highlight=formatting+external+hard+drive") thread) but still I only got 916.70gb while 14.81gb still being used... used by what?

At first I formatted it to XFS but it wouldn't mount on my desktop for some reason... I'm running ubuntu 9.04 on both my laptop and my desktop.

Any suggestions on how to get all my free space?

---

### Post by ajgreeny on 2010-04-23
But is it really a 1TB disk?  Many manufacturers work on 1000 bits being a kilobyte, 1000 kilobytes being a megabyte, 1000 megabytes being a gigabyte, etc etc, so when you compound all those lost 24 bits and bytes, the real size of a drive can show as quite a bit less than you might expect.

---

### Post by 300Z on 2010-04-23
I'm well aware of that and I did mention 931.51gb being the total available size, but my issue is after formatting it as ext4fs it only shows 916gb free while ntfs or XFS would have the whole 931gb free.

---

### Post by srs5694 on 2010-04-23
I'm not positive, but the 15GB size difference is probably just the journal. You could try using tune2fs to disable the journal and observe the effect to test this hypothesis, but then you'd almost certainly want to re-enable it (again, using tune2fs).

---

### Post by 300Z on 2010-04-23
> **srs5694 said:**
>  You could try using tune2fs to disable the journal and observe the effect to test this hypothesis, but then you'd almost certainly want to re-enable it (again, using tune2fs).

Already did, went from 870gb to 916gb, but still 14gb missing... :(

---

### Post by srs5694 on 2010-04-24
Please read the tune2fs man page, or see [this page.](http://www.troubleshooters.com/linux/ext2toext3.htm) You can remove the journal using tune2fs. Note that this is distinct from changing the reserved block percentage, which I fully realize you've already done to get from 870GB to 916GB free.

Be advised, though, that removing the journal on a disk of that size is a Bad Idea. You'll be waiting until the end of the century the next time a disk check runs. (I exaggerate, but it'll *feel* like you're waiting that long!) I only suggest making this change as a test of my hypothesis that it's the journal chewing up that disk space, and restoring the journal afterwards.

---

### Post by 300Z on 2010-04-24
Thank you for the advice, I'll read into it.

I may try reformatting back to xfs tho.

---

### Post by srs5694 on 2010-04-24
Don't get too hung up on available space estimates on "empty" disks, or on differences in these estimates between filesystems. Each filesystem has its own way of allocating space, and a filesystem that claims more free space when it's empty may actually store fewer files than one that claims less free space. The reason is that filesystems vary in how efficiently they pack files together and in how much overhead is required for each file. Short of conducting tests to see how many files you can fit on a disk, you can't really be sure which one will provide the most free space in actual use. Even testing the disk may produce misleading results, since the actual capacity will vary with features like the file sizes. As a general rule, though, ReiserFS is king when it comes to storing small files (those with sizes measured in kilobytes). By the time you get to files with sizes measured in megabytes, I'm not sure there's much difference between filesystems.

---

### Post by 300Z on 2010-04-24
I think I'll just leave it alone as it is, 14gb isn't too bad.

---

