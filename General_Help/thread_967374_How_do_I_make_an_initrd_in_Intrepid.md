---
title: "How do I make an initrd in Intrepid?"
date: 2008-11-02
forum: General Help
---

### Post by mjpatey on 2008-11-02
Hi, all-  I'm currently booting from an Intrepid live CD because my installation of Intrepid has failed with a Kernel Panic:  > [    1.008228] VFS: Cannot open root device &quot;UUID=2214c5bf-50a0-42b68a76-5ebe204a800b&quot; or unknown-block(0,0) [    1.008369] Please append a correct &quot;root=&quot; boot option; here are the available partitions: [    1.008572] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)  I searched a bit, and it seems I have no &quot;initrd&quot;, which may explain the problem.  Does anybody know how to create a new initrd?  I've read of a script called &quot;mkinitrd&quot; but can't find a version for Ubuntu, and when looking at package &quot;initramfs-tools&quot; in Synaptic, I can't make heads or tails of which part of the package would apply to me.  If you have any idea what any of this means, I'd appreciate any insight you can impart!  Thanks,  -Mark

---

### Post by vincent_fil on 2008-11-24
Hi,

I'm façing the same problem (can't found mkinitrd)
and after a little googling, I think the yaird package is the solution:

[http://packages.ubuntu.com/intrepid/yaird](http://packages.ubuntu.com/intrepid/yaird)

Some information can also be found on the following page:
[http://wiki.debian.org/InitrdReplacementOptions](http://wiki.debian.org/InitrdReplacementOptions).

Cheers,
Vincent

---

### Post by ibutho on 2008-11-24
Try mkinitramfs. It seems like most Debian based distros now use this tool instead of mkinitrd.

---

### Post by vincent_fil on 2008-11-24
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=610660](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=610660)

the following command (with your specific version) should do the trick:

```

update-initramfs -c -k 2.6.28-rc6

```

---

