---
title: "Drive partitioning jamming at 33% (installation by floppy)"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by FZE on 2009-06-19
I'm attempting to install Ubuntu by way of [this guide]("https://help.ubuntu.com/community/Installation/WithFloppies"), and all is going well enough until I come to the portion in which I partition my hard drive.

I go through Guided Partitioning, selecting to use the entire hard drive as one partition. When I go to write the changes to the drive, it gets to the 'creating ext3 file system' portion, and progresses to 33%. At this point, it hangs for a bit, then returns the error:

"The attempt to mount a file system with type ext3 in IDE1 master partition #1 (hda1) at / failed."

When loading the Partition disks menu, I do receive the error "The current kernel doesn't support the Logical Volume Manager. You may need to load the lvm-mod module."

Is this the source of the problem? If so, how can I load the lvm-mod module?

---

