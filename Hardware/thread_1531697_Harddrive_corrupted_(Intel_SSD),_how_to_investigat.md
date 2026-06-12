---
title: "Harddrive corrupted (Intel SSD), how to investigate?"
date: 2010-07-15
forum: Hardware
---

### Post by martinseebach on 2010-07-15
Hi,

Earlier today, my computer started acting strange, and I noticed that the hard drive (160 GB Intel SSD X25-M 2G, ext4, mounted on /) had been re-mounted in read-only mode. I booted to a rescue-CD and ran fsck.ext3 which fixed a large amount of issues on the volume. I tried to reboot, but unsuccessfully, which I could trace to my /var being completely gone.

I'm backed up and have a spare bootable drive, so I was relatively quickly up and running, but still.

So how do I investigate this? I have two main suspects, the SSD and ext4. I got the SSD in march and installed the beta of 10.04 on the computer (which is a MacBook from 2007). Both SSD and ext4 are new to me, but I've run Ubuntu and Linux for years on regular disks, usually using ext2 or ext3.

After a few weeks, my computer had it's root partition remounted in read-only, and I had to boot to a CD and do the fsck (as I did today). Then, the computer booted fine and I couldn't determine any corruption, so I decided to give it another chance (checking that my backups are working).

This time, I'm not likely to do that. Is there any way I can tell if my SSD is corrupting data in any determinate way, so I can return it?

Thanks,
Martin

---

### Post by AltomineUK on 2010-07-15
I think the running self testing features under Smart Data in the disk utility tells you if you have got any errors and such things in your storage medium....

---

