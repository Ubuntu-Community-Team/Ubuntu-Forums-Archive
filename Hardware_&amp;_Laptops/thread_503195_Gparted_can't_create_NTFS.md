---
title: "Gparted can't create NTFS?"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-07-17
See screen shot.

---

### Post by LaRoza on 2007-07-17
Format it with Windows.

---

### Post by dabl on 2007-07-17
> **LaRoza said:**
> Format it with Windows.

Yep.

But don't try install Linux on it afterward! :)

---

### Post by diablo75 on 2007-07-17
I did this, but for some reason, I can't write to the drive now....

---

### Post by sancho panza on 2007-07-17
You need to install NTFS 3G:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by diablo75 on 2007-07-17
Here's the culprit.  Turns out I had the right NTFS software already installed, but I didn't have this one check box for external device write enabled.

After checking it off, everything worked perfect after a system reboot.

---

### Post by eqo314 on 2007-08-12
Hi,

I have all the check boxes enabled in the ntfs-3g configuration screen and the latest version of ubuntu.  i still am not able to create an ntfs partition.  the choice is grayed out.

---

### Post by merlinus on 2007-08-12
Can you be more specific?  Are you trying to create a new partition?  Re-size an existing one?

ntfs-3g allows you to write to an existing ntfs partition.

-merlin

---

### Post by eqo314 on 2007-08-19
hi,

i got it to work.  also, i just figured out how to find my old posts on this forum.  thanks !!

---

### Post by direwolf08 on 2007-08-19
How did you get it to work eqo?

---

### Post by migla on 2008-02-02
I could *create* an NTFS partition in gparted once I had installed the package **ntfsprogs** aswell. So, to sum up, for someone who wants to create and fiddle around with ntfs partitions:

```
sudo apt-get install gparted ntfs-3g ntfs-config ntfsprogs
```

---

### Post by Pjotrovitz on 2008-02-22
Thanks mister!

I love finding the answers to all my questions just by searching these forums!

---

### Post by charonn0 on 2008-05-01
I had the same problem. Try installing ntfsprogs from the repos.

---

