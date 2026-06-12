---
title: "Restore partition formatted by Win7"
date: 2015-03-17
forum: Hardware
---

### Post by shabboleth on 2015-03-17
I searched but I don't see that this question has already been posted. Apologies if it has.

I have been running xubuntu as my only OS for a while with no serious issues but this weekend I decided that I couldn't live without a particular game that doesn't work very well under wine. So I made room on my hard drive and installed windows 7. 

Last night I came up for air from my game and booted from a livecd to fix grub and restore my ability to boot into xubuntu. However, it seems that win7 decided that my sda1 partition wasn't being used and formatted it to ntfs and threw a few system backup files into it. 

Is there any way to restore my ext4 partition or at least recover some files? Most of what I lost was replaceable but a few things were not. I'm fine with reinstalling one or both OS's if necessary. 

Thanks in advance for any ideas.

---

### Post by weatherman2 on 2015-03-17
Windows generally doesn't erase existing partitions unless you tell it to.  The Windows installer should tell you what it's going to do.  Of course, it pretends it cannot see any non-Windows partitions, so it might prompt you to choose a Linux partition as "empty space" in which to install Windows.

(Windows 7 will create a tiny boot loader partition unless you pre-format an NTFS partition for it to install into - so that's why there are probably two Windows partitions now.)

So if you told Windows (without realizing it) to install on top of your Linux partition - it is now gone.

Or, it could be you simply haven't found your old partitions.  Boot a Linux live CD or USB then in a terminal window type:

```
sudo fdisk -l
```

to see what existing partitions you have now.

---

