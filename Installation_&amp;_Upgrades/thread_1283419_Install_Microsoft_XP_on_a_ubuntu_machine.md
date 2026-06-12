---
title: "Install Microsoft XP on a ubuntu machine"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-05
Hi,

I want to install windows XP in my machine having Ubuntu 9.04. I am afraid that I might loss my Ubuntu.

Kindly help...............:(

---

### Post by blur xc on 2009-10-05
> **vksingh said:**
> Hi,

I want to install windows XP in my machine having Ubuntu 9.04. I am afraid that I might loss my Ubuntu.

Kindly help...............:(

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I did ti w/ vista- wasn't hard...

you can always run XP inside of Virtualbox, but that's not w/o it's drawbacks.  It depends on what you need xp for.  Itunes runs in vbox just fine, but the sandisk sanza fuse media converter and firmware updater don't.  Also, the lego digital designer my kids like to play with doesn't either.  And neither does Adobe Lightroom (at least not with the catalog file located on a shared folder)...  So, yeah, it's limited, and depends on what you need it to do.

BM

---

### Post by vksingh on 2009-10-05
Thanks for reply. Actually I want to install windows XP and Ubuntu in dual boot mode. I have already Ubuntu in my machine.

I know to install ubuntu on a windows XP machine and both works fine. But, last week when I tried to install windows XP on a Ubuntu Machine, I lost my Ubuntu.

So I want to know , is there any way by which I can install windows XP on Ubuntu machine without loosing present Ubuntu .

Thanks,

Vivek

---

### Post by louieb on 2009-10-05
> is there any way by which I can install windows XP on Ubuntu machine without loosing present Ubuntu .Thats exactly what the link** blur xc   **shows. Short of it is create a primary partition, set its boot flag to on, tell the XP installer to install there, restore GRUB to the MBR, make an entry in the grub menu for XP.

---

### Post by bigboy_pdb on 2009-10-05
You'll probably have to repartition your hard drive using a partitioning program (gParted would probably be best). **Don't change the partitions with Ubuntu booted from the hard drive. Use a live CD which has the partitioning program on it.**

Once you've finished, make certain that the partition doesn't have a file system (or that it has a file system that Windows can read such as FAT32). Then you can install Windows on the partition, but be sure not to install over the Ubuntu partition (since Windows doesn't recognize Linux partitions). If the partitions are different sizes and there are only 2, it should be easy to tell which one is the Ubuntu partition and which is the Windows partition. Otherwise, you'll need to pay attention to the gParted interface, which should indicated where each partition is on the hard disk.

After you've installed Windows you'll need to reinstall GRUB since windows will overwrite the section of the hard disk which is used to boot GRUB. Apparently, this can be done using the live CD if you skip the installation (just do a search on "reinstalling GRUB" in the forums.

There are probably other people who have done some of these tasks more recently and who can provide more help and information, but this will at least give you some direction for now.

**EDIT**: I forgot to mention that you should back up your hard drive contents. External hard disks and rewritable CDs/DVDs are useful for doing this.

**EDIT**: Sorry I hadn't noticed the link that was posted by "blur xc". From a quick glance, it looks like it covers what you'll need to know.

---

### Post by Lars Noodén on 2009-10-05
AFAIK XP and other versions of Windows do that on purpose.  Here is one timely  anecdote on that:
[http://www.birdhouse.org/beos/byte/30-bootloader/](http://www.birdhouse.org/beos/byte/30-bootloader/)
BeOS has been re-done as [Haiku](http://www.haiku-os.org/).

Have you looked at running the left-over applications in [WINE](http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=jaunty&section=all)?  That sometimes even gives a performance boost and it means you only have to maintain one OS.  

Another option is to run XP inside a virtual machine using VirtualBox or Qemu.

---

