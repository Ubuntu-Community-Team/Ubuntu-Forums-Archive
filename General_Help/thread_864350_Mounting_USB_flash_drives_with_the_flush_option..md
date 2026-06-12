---
title: "Mounting USB flash drives with the flush option."
date: 2008-07-19
forum: General Help
---

### Post by sicofante on 2008-07-19
Hi,

I'm trying to get my USB devices automounted with the flush option.

I've read [this]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149277"), [this]("http://ubuntuforums.org/showthread.php?t=829279") and [this]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-mount.html") and I'm confused.

I'm trying to avoid sync in the ordinary /etc/fstab file, just in case it does any harm to the flash devices (after much reading I'm not so sure that it does, but flush seems to be more efficient and safer).

Now:

1- First of all, I don't know what's all that hal stuff. Up until now I thought everything related to mounting would be in /etc/fstab and the mount command. I've just learned about gnome-mount and honestly I don't know why it even exists. I would much appreciate any link to sources of information on all this.

2- I also would appreciate a step by step HOWTO on setting up my system so USB flash devices are always automatically mounted with the flush option.

(I DO know unmounting before ejecting is what must be done. I'm researching an alternative to this. Thanks.)

---

