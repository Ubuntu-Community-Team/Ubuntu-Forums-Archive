---
title: "Can I install on a disk with bad sectors?"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by skullmunky on 2008-12-29
Ubuntu 8.10, Sony Vaio Laptop VGN-FZ180E, currently w/ Windows Vista.

The installer can't resize the windows partition, because it says there are bad sectors.  Ahah, perhaps that is why this laptop has been running so poorly in the first place!  

We went back to windows and ran CHKDSK /f /r on the drive.  Chkdsk found some bad sectors, and claims to have repaired everything successfully.  

However, GParted still shows bad sectors and won't allow us to resize the partition.

1. I know one bad sector often begets more, and is a sign of a dying drive; but other times it's just one or two bad ones, and the rest of the drive works fine for quite a while still.  Given that, if Chkdsk (which I assume is something like fsck and badblocks?  ) passes, should the drive appear clean enough to GParted or will GParted never allow me to resize it once there are some bad bocks?

2. GParted says I can run give ntfsresize a flag to force it to resize a partition even if it has bad blocks.  Can that be done from inside GParted or does it have to be done manually from the terminal?  

3. If so, can someone point me to some good, clear instructions on how to resize an ntfs filesystem and partition from the command line?  the man pages are ok but I want to make sure I don't destroy this drive, since it's not mine.

thanks!

---

### Post by tommcd on 2008-12-29
Vista has it's own partitioning utilty. Give that a try and see if you can partition the drive:
[http://articles.techrepublic.com.com/5100-10878_11-6170510.html](http://articles.techrepublic.com.com/5100-10878_11-6170510.html)

---

### Post by skullmunky on 2008-12-30
Yeah, we tried that, but ran into the same problem as the author of the article - the available shrink space was tiny (around 400MB) even with 60GB free, the drive defragged, and with paging, snapshots, etc. disabled.  I'm amazed that they have the cajones to let you resize your boot partition while it's mounted, but I guess if Vista can stitch together panoramic photos it can do anything! :) 

Meanwhile that laptop seems to be getting sicker: longer and longer boots, more freezes, slower file access ... we're going to just put a new hard drive in and go from there.

---

### Post by stderr on 2008-12-30
I feel awful recommending a proprietary tool, but Spinrite has always served me well in the past in terms of handling bad sectors etc. One should pay for it, though - so unless you're regularly playing around with HDDs, it may well be cheaper & easier to get a new drive. Of course, there are free ways to acquire that software, but we couldn't condone those methods.

---

