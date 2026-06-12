---
title: "What to do with an extra Hard Drive and RAID Questions"
date: 2010-08-24
forum: Hardware
---

### Post by PresenceofMind on 2010-08-24
Hello everyone, 

This is a general hardware question, which has been annoying me for a while now. 

I just finished assembling a PC and now I have ordered an extra hard drive (Seagate 500GB SATA). My master HDD has the OS and it's 250GB (Seagate SATA). 

Can I RAID my hard drives or are there any other ways I can make these two act like one single HDD. I don't want it to be recognised as two separate drives by the OS (Whether it be Ubuntu or Vista 64). My Mobo supports RAID 0, 1, 3, 0+1 and I want the one that will give me the best performance. I heard RAID 0 is fast, but a bit down on reliability.....but can I decrease the chances of data loss with regular back-ups to my external HD? I mean will back-ups work with RAID drives?

Thanks,
PoM

---

### Post by dandnsmith on 2010-08-24
Have a look at [this page](http://en.wikipedia.org/wiki/Standard_RAID_levels) for an account of the various levels of RAID and what they imply.

If you're depending on the mobo, do you need to safeguard against failure of it, as well as a disk?

The ability to have both linux and Windows see the things as on HDD depend on what they perceive the disks as - I'm not sure how you tackle that, but if you have a solution then you can certainly do backups (but to what?)

---

### Post by pricetech on 2010-08-24
Your new drive is twice the size of your original, so you'd only be able to mirror half of it with the original drive.  You could then use the other 250 for an additional partition, but I don't think that's what you're after.

Striping won't let you use all of both drives as one drive either.  I didn't follow the link in the previous post, but I do recommend reading more about RAID before you attempt anything.

Also, be aware that your motherboard may not have a genuine RAID controller.  It might depend upon windows only software to behave like RAID, in which case you'll be unable to use any form of hardware, or pseudo hardware, RAID and will have to go with software RAID.

---

### Post by PresenceofMind on 2010-08-24
Thank you both....

My mobo has an onboard raid controller (NVidia Media-Shield). However, after some research I found that Windows supports something called Dynamic Disks where you can expand a drive to include another separate drive as well so when one disk is used up the OS will switch to another...will this work?

I probably won't go RAID just yet. I just don't know how Linux or Windows would respond to it....

---

### Post by dandnsmith on 2010-08-25
If linux doesn't support Windows Dynamic Disks, then you couldn't use it as a general solution. I haven't any reference, but think I may have seen docs saying it isn't linux accessible.

---

### Post by PresenceofMind on 2010-08-25
Hmmm...ok

I'm thinkin of leaving it as two separate drives then. The only thing is that I heard some programs might not like the fact that the saved data is stored in a separate drive to the one the programs are installed in. Is there really such problems? I plan to have programs in one drive and data in another....

---

### Post by ronparent on 2010-08-25
An nvidia controller supports a spanning raid, however that is defined. You could look into that. It should apply in windows as well.

---

### Post by PresenceofMind on 2010-08-26
> **ronparent said:**
> An nvidia controller supports a spanning raid, however that is defined. You could look into that. It should apply in windows as well.

Spanning RAID would work....if neither of my two drives have Windows or any OS. As I do have an OS in one drive, RAID = Format and start all-over-again. I'll stick to two separate drives.

Thank you all for your assistance.

Have a nice day.

---

