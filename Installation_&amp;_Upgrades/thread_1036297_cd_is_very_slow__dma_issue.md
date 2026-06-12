---
title: "cd is very slow / dma issue"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ajaygautam on 2009-01-10
My question: How do I get this to work with latest 8.10 approved kernel (2.6.27-9-generic)

Workaround: boot into an older kernel (2.6.24-22-generic works). Read on for more technical details.

Upgraded to 8.10 a few days ago. Started some cd work today, and found that the CD is extremely slow and is bogging down the whole system.

<rant>
This reminded me of using Linux decades ago, when one was forced to manually set DMA on each of his drives. I thought those days were gone. Alas... NOT!... sigh. In a modern operating system, one expects basic hardware stuff (like cd drives) to work out of the box.
</rant>

Now that, thats out of the way...

First, grip complained: "Unable to initalize /dev/cdrom". I checked and found that /dev/cdrom is missing, and /dev/cdrom1 and /dev/cdrw1 are poiting to /dev/scd0 (VERY strange. These should be pointing to /dev/hdd). Any-hoo, I symliked /dev/cdrom to /dev/scd0

Remembering DMA issues, I checked with hdparm. My output is similar to [this post]("http://ubuntuforums.org/showthread.php?t=479996"). I will copy / paste from there for convienence (of not having to reboot my system)

```

# hdparm /dev/scd0

/dev/scd0:
IO_support = 0 (default 16-bit)
readonly = 0 (off)
readahead = 256 (on)
HDIO_GETGEO failed: Inappropriate ioctl for device

```

After lots of banging-head-at-google (and ubuntu forums), I began to suspect IDE / SCSI collaborative workings, and checked for kernel module ide_cd. And found it missing (!!??) for my current kernel: 2.6.27-9-generic, but found it in 2.6.24-22-generic.

Then I check grub.menu.lst and found 8.10 with 2.6.24-22 and re-booted with this kernel.

Sure enough, cd problems went away. Found /dev/cdrom (correctly) auto-linked to /dev/hdd. hdparm verified DMA is set. Verified ide_cd is loaded as a module. Grip works fine. System does not get bogged down!

So... how do I get this working with the latest approved kernel?

(PS: I switched from gentoo to ubuntu because I got tired of re-compiling my kernel - So don't ask me to do that).

---

