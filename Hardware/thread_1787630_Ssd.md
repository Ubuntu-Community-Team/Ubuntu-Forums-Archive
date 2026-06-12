---
title: "Ssd"
date: 2011-06-21
forum: Hardware
---

### Post by malty on 2011-06-21
Is there a definitive howto for the installation of 11.04 on the latest generation of SSD, regardless of make and including the partitioning and trim setting and SATA information, a pointer in the right direction would be appreciated, have looked in all of the usual places and can only find the usual scattergun selection, much of it too old in any case.
If there ain't one, it's about time there was as SSDs are the coming new black.

---

### Post by u.rusty on 2011-06-21
I'm not sure what you are asking. I'm running Ubuntu 11.04 on an SSD drive, although I subsequently moved the /home directory to a SATA hard disk. The use of a SSD drive is the same for the user as a hard disk drive is, as far as I know.

---

### Post by malty on 2011-06-21
As far as I understand, with a desktop setup, there are issues with SATA3 requiring BIOS modification, also not requiring a swap partition and trim has to be manually set up, so not as simple as you indicate.

---

### Post by KFoder on 2011-06-21
Hi

I do not know of any problems installing on an SSD, I'm running 11.04 on an 128GB SSD without any problems at all :p

I just plugged the disk in, installed and have been running since.

Kim

---

### Post by Keffin on 2011-06-21
To enable trim (assuming you're using ext4), add "discard" to your mount options in /etc/fstab. e.g.
```
/dev/sda4     /home      ext4    defaults,discard        0       2
```I believe recent distro installer partitioners are set up to accomodate SSDs properly, as it does no harm to HDDs to be partitioned like this anyway. So you need to do nothing special here now.

You can google about the kernel io scheduler if you're feeling hardcore. People used to strongly suggest "noop" instead of the default "cfq", but I've seen mention multiple times of the defaults becoming better suited to SSDs as newer kernel versions have been released, so I stick to defaults now. "noop" should still technically be better, but I'd bet money you won't see it in anything like normal use.

I had to google all over the place to get my info, as I wanted to "get things right" when I bought my SSD (~1.5 years ago), but now I think the only useful manual intervention left is enabling trim, so I deleted my links a few months ago.

If you want to try and find more info, the OCZ forums were a very useful source when I was looking, especially if your drive has a Sandforce controller. But even if it's not Sandforce, almost all the info applies equally - the exception potentially being write block sizes, but like I said I think recent partitioners deal with this for you.

---

