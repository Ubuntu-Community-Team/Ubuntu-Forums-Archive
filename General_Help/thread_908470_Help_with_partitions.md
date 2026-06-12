---
title: "Help with partitions"
date: 2008-09-02
forum: General Help
---

### Post by TuckLive on 2008-09-02
I just used GParted to shrink my Ubuntu partition to make room for Windows.  After I installed Windows on the unused partition I didn't get the os boot option, it just went straight to Windows.  So I deleted the Windows partition and now when I boot up my computer I get "error loading operating system".  Here is what my partitions look like in GParted:

Partition    filesys      mountpoint                flags
/dev/sda1    ext3         /mediadisk                boot
/dev/sda3    linux-swap 
unallocated

The swap was behind the unallocated, but I moved it behind ext3.  the only way I can access my system now is through the Ubuntu livecd.

Please help:confused:

---

### Post by lisati on 2008-09-02
Windows has a habit of "clobbering" anything you have set up with Grub (which manages the choice of OS's at boot time). One solution commonly offered through these forums is the use of the Supergrub disk.

See [here]("http://www.supergrubdisk.org/") for more information.

I don't see anything that looks like a Windows partition in the list the OP has provided but I'm not sure what to suggest. (Edit: Windows sometimes likes to be first on the disk)

---

### Post by snowpine on 2008-09-02
Windows just isn't designed with dual-booting in mind. I would recommend re-installing Windows to a new partition in your unallocated space, then re-installing Grub (Supergrub is probably easiest, though you can also do it from the Ubuntu Live CD if you know what you're doing). Your Ubuntu install is, most likely, unharmed (except for not booting, obviously).

---

### Post by TuckLive on 2008-09-02
I can still access some of my files from the LiveCD, so my Ubuntu isn't harmed.  I'm going to try the Super Grub boot disk.

---

### Post by dawbomb on 2008-09-04
That's something I've done before, but on two windows installations.  The problem is that when you install windows, the boot loader partition on your hard drive is overwritten.  If you have another windows installation on your hard drive, windows installation picks it up, and appends that to the new boot loader.  However windows doesn't see (or chooses not to see) the Linux partition, and so overwrites it.

What I did last time was to reinstall windows (on the windows partition, DO NOT delete any linux partitions), and then manually edit the boot loader to get it to recognise the other partitions.  In this case you don't want the windows boot loader, so reinstall windows, and then run the recovery tool from the ubuntu cd.  I'm sure the live cd has a recovery option.  I installed using the alternate install cd, but the live cd should have a recovery tool too.  Try get the recovery tool to reinstall the boot loader.  I'm 90% sure that'll allow you to boot both linux and windows from grub.  

Please let me know on this thread if it works, because virtual machines just work for some of the applications which I need for university, and so I'm going to have to reinstall windows XP.  :'(  But I intend on keeping my hardy installation right where it is, and using that primarily!

---

