---
title: "Incorrect partition size"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ddollas on 2009-04-27
I was wondering if anyone here could offer me some advice on how to correct an issue I caused for myself.  

I just installed a partition for 9.04 on my machine alongside windows vista.  The problem is that when I selected the side-by-side option for installing the OS so that I wouldn't wipe my Vista install, it only allocated 121 MB to Ubuntu.  That isn't even enough space to download all the updates.  I attempted to clear the partition with Vista's disk manager, but it won't let me delete it.  :/  

Any suggestions for how I can get rid of this messed up install and try again?  

(Ubuntu installed fine, I just need to banish this one mistake.)

Thanks!

---

### Post by aikiwolfie on 2009-04-27
[list=1]
[*]Back up all your important data and the installers for any downloaded programs you don't want to lose.


[*]Next boot from the Ubuntu Live CD.


[*]Open Gparted from **System > Administration > Partition Editor**. This should show you the lay out of the partitions on the disk.


[*]Select the **Vista** or **NTFS** partition and click **Resize** on the menu bar at the top. If it's greyed out, **right click** the partition and select **Unmount**. Then try the resize button again.


[*]Repeat the last step for all other partitions you wish to resize or you can simply delete your Ubuntu partition and start the installation from scratch.
[/list]

Edit: You may wish to check you actually have enough free space to begin with. Otherwise if 121MB was the most Ubuntu could free up resizing your Vista partition will mean the lose of data. It is also a good idea to defrag your Vista partition before doing any of this.

---

### Post by ddollas on 2009-04-27
Thanks for the info.  I have to chalk this up to it being late and I just wasn't paying attention, I have 300 gigs of free space, and another hard drive with 400.  (the latter being the location I wanted to place Ubuntu in the first place.)  

Again thanks much!  :)

---

### Post by old_geekster on 2009-04-27
> **ddollas said:**
> I was wondering if anyone here could offer me some advice on how to correct an issue I caused for myself.  

I just installed a partition for 9.04 on my machine alongside windows vista.  The problem is that when I selected the side-by-side option for installing the OS so that I wouldn't wipe my Vista install, it only allocated 121 MB to Ubuntu.  That isn't even enough space to download all the updates.  I attempted to clear the partition with Vista's disk manager, but it won't let me delete it.  :/  

Any suggestions for how I can get rid of this messed up install and try again?  

(Ubuntu installed fine, I just need to banish this one mistake.)

Thanks!

If you are using two separate hard drives, then don't select the side-by-side option.  You can simply install JJ on the second drive and GRUB will allow you access either OS.  I have been doing this for years with XP Pro and Ubuntu.

---

