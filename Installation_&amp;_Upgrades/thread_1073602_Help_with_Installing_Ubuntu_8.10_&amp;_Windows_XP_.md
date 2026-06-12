---
title: "Help with Installing Ubuntu 8.10 &amp; Windows XP on Dell Latitude D600"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Desady on 2009-02-18
Hello friends & colleagues!

I installed Ubuntu 8.10 on my DELL latitude D600 about two days ago & it has been a great experience for me. I was initially using Win XP before getting to ubuntu. Now, I want to keep both of my favourite operating systems on my Dell Latitude D600.
I would be grateful if I can get a step-by-step guide in carrying out this task. Below is some information about my hard drive and partitions:

Main drive: 160 GB

Partition 1: 30 GB
Partition 2: 30 GB
Partition 3: 50 GB
Partition 4: 50 GB

I hope this little info can aid someone help me out.
Thanks for your help!

---

### Post by SunnyRabbiera on 2009-02-18
I suggest just having 2 partitions to start off with, you have to give XP breathing room as with updates and data collection XP can be a real space taker.
Just half the drive between XP and ubuntu.

---

### Post by whoop on 2009-02-18
So are you gonna start from scratch? If you are I advise the following approach:

Determine what size you want for you xp and what size you want for ubuntu. Once you got that figured out install windows xp on the unpartitioned drive (windows will take up the entire drive.
Once you are done boot the ubuntu live-cd; go to terminal and type:
```

sudo gparted

```
In gparted resize the windows partition to make room for ubuntu.
Now you have a windows partition and some unpartitioned space.
Do a (optional) reboot to check if windows xp is still working (just to feel secure)
Now boot the live-cd again and start installing ubuntu. When you get to partitioning just tell it to use the unpartitioned space.

That's it.

---

