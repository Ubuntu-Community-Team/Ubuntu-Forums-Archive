---
title: "Unable to partition because of a bad sector"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by 2Perfect on 2007-10-23
Same as [this problem](http://ubuntuforums.org/showthread.php?t=187469) and [this problem](http://ubuntuforums.org/showthread.php?t=397619) and [this problem](http://ubuntuforums.org/showthread.php?t=379346). Doesn't seem to have a solution.
---
Basically I can't resize the NTFS partition using the Ubuntu installer nor GParted (through the System Rescue CD).

From the Ubuntu installer I don't get an error. I just don't get the "Guided - Resize main disk" option or the resize option in manual (I can still resize an existing FAT32 partition that contains recovery). GParted says there is at least 1 bad sector, and told me to run check disk twice (chkdsk /f /r). I did. An "unspecified error" came up right at the end, then it proceeded to boot Windows XP normally. From what I've read, this means there's a bad sector, which people have said to mean that the hard disk is nearing failure. And I'm guessing check disk is not / can not repair that.

Is it impossible to install Ubuntu anyway? I'll probably get a new laptop for my important data, then just use this old one to learn different distros of linux. **Is it possible to still partition a drive with bad sectors?**

**GParted mentioned something about bad-sector mode or something? Does that mean it will partition and ignore the bad sectors? How would I enter this mode?**

Thanks in advance!

---

### Post by 2Perfect on 2007-10-24
I figured out that GParted was talking about *ntfsresize*'s -b option, which ignores bad sectors or something.

I resized my drive that way but I think there might be something else I have to do. On My Computer in Windows XP, it shows up as the new size. On Computer Management -> Disk Management (winXP), it shows up as the old size. On GParted, it shows up as the old size, and still wont let me partition in.

On ntfsresize, it shows up as:
volume size: new size
device size: old size

So I'm guessing the "volume" was resized but the device wasn't? What exactly does this mean? I don't want to just lose 10GB of my hard disk if I do something wrong ahaha :P ntfsresize also mentioned fdisk to resize my device, but I can't figure out how to resize it using fdisk.

Any help is appreciated!

I've ran chkdsk like 3 more times today :S It's getting really annoying. In the end of chkdsk it says there's 4KB in bad sectors, which is pretty much nothing, so I don't know why ubuntu can't just ignore that :P

---

### Post by 2Perfect on 2007-10-24
bump

---

### Post by 2Perfect on 2007-10-24
PLEASE HELP! I'm very determined to install ubuntu coz I want to start learning/getting familiar with Linux. I tried before but gave up right away without even trying to install it because wireless wouldn't work, but this time I would do anything (that doesn't cost money or data) to get ubuntu working!!!

PLEASE HELP!

---

