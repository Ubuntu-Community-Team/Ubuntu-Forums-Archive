---
title: "HDD upgrade on a dual boot system"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by gardara on 2007-08-06
I am thinking about upgrading the hdd on my laptop to a 250 or 300gb one and I was thinking about just taking a ghost copy of my current disk and then putting it on the new hdd.
But as I have a dual boot system with 3 partitions (actually 4 if I count swap) I was wondering what would happen to the new space? Would the partitions get more space each or would I end up with the new space as a new partition or as a unpartitioned space? Or maby something else?

---

### Post by kidders on 2007-08-09
Hi there,

> **gardara said:**
> Would the partitions get more space eachDefinitely not. As you suggested, you'd probably end up with a chunk of unallocated space at one end of the new disk, but since there will be four partitions on it, you may or may not be in a position to use it, depending on your current partitioning scheme.

The approach I would take depends on what else is on your laptop besides Ubuntu. For instance, if it's MacOS or maybe more Linux, I would be tempted to create giant tarballs of the three useful filesystems & copy them somewhere else, giving you free rein over the partitioning scheme on the new hard disk. On the other hand, Windows would almost certainly object to being manhandled like that.

---

### Post by gardara on 2007-08-12
What I have is a ubuntu setup with three partitions...  ubuntu, swap, home. And then I have one partition for windows.
My ubuntu setup is just like I want to have it, and I really don't have the time setting it up like this again... But the windows setup I really don't care much about... I can just install it again if that is any better...

What do you recommend I do?

---

### Post by kidders on 2007-08-12
I'm not altogether sure what I would do in your situation. Having a laptop kinda eliminates some of the nicer, quicker options that involve plugging both of the hard disks in at the same time. Having said that, I'm very sympathetic to your objection to reinstalling your Linux from scratch ... once you've got everything working just the way you like it, having to start all over again would be depressing.

Assuming you have enough external storage, and some time on your hands, I would probably suggest dividing your filesystems up in your head into, say, DVD-sized chunks, and creating a small collection of gzipped tarballs. Be *really* careful to preserve all permissions, symlink structures, and so on, when formulating your "tar ..." commands. Once you're done, you can ...[LIST]
[*]Boot from a Linux LiveCD or something similar.
[*]Create yourself a nice new partitioning scheme with cfdisk, or something.
[*]Use mkfs & mkswap to set up some filesystems.
[*]Unpack your tarballs into the new filesystem structure.
[*]Read your /etc/fstab carefully, making certain that it still accurately reflects your disk layout.
[*]Reinstall your bootloader & reboot.[/LIST]Although it's a bit more convoluted than methods that involve disk dumps & similar imaging techniques, such an approach has a few advantages...[LIST]
[*]You get to choose the sizes of your new partitions without having to expose yourself to the risks involved in resizing.
[*]You give yourself the freedom to try out new filesystem types, in the event you haven't been liking your original choices ... or to choose new configuration options, such as block sizes.
[*]Although most Linux filesystems are quite resistant to fragmentation anyway, tarballing & untarballing would have the effect of defragmenting your system ... which is no bad thing.[/LIST]Another option I would consider involves connecting your laptop to another computer via a firewire cable, placing one of them in target disk mode, mounting one computer's filesystems on the other & copying your Linux system directly, without the intermediate DVDs/etc ... which would be significantly faster.

Still further, you may have a 3.5" adapter, which you could use to plug one or both of your laptop hard disks into a desktop PC & perform a direct copy. Whatever option you go for, remember that it is absolutely critical that filesystem structures such as symbolic links, ownership & permissions remain exactly preserved, to avoid unpredictable behaviour & security problems.

Also, it's worth pointing out that, in the event you *have* to opt for something involving ghosting, and you wind up with large chunks of unallocated space on your new hard drive, that's not a major problem. You could, for instance, choose to mount the extra space somewhere like /usr, so you can make full use of it.

I hope that's of some help.

---

