---
title: "Problems installing 8.10 and 8.04"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by TAFKARS on 2009-02-10
Hi there

I am attempting to dual boot my Fujitsu laptop with XP and 8.10. The laptop is poor on memory (256MB) but satisfactory otherwise (40GB HD, 2.5 GHz CPU). I have partitioned the HD to yield c.20GB free space for the Ubuntu install.

8.04 failed to get to the Install prompts screens (after hanging for around 2 hours). 8.10 happily gets to the partition bit of the install prompt relatively quickly. 

My problem is whether or not I allow it to resize the partition automatically. In selecting the 'Guided - use the largest continuous free space' option, the graphic indicating how the disk will be partitioned after the install seems to indicate that the WHOLE HD will be consumed by Ubuntu, rather than just the 20GB partition that I have created for it.

The manual option is a possibility, but if I try to change anything here it appears to suggest that it will remove the windows partition.

Not sure how to proceed, would appreciate any advice!

---

### Post by aheckler on 2009-02-10
I would go the "Manual" route just to be sure. Select your empty partition, use ext3, mount it as /, and there you go. :)

---

### Post by TAFKARS on 2009-02-10
> **aheckler said:**
> I would go the "Manual" route just to be sure. Select your empty partition, use ext3, mount it as /, and there you go. :)

Thanks, reply much appreciated. 

Unfortunately, the keyboard fails to function upon getting to stage 4/7, the partition prompt. This is less of a problem as you can use the drop down to size each partition. Imposible to proceed beyond 5/7, however, as here the details regarding username, password etc. are required.

Anyone had/overcome this problem in the past? Clearly nothing actually wrong with the keyboard as I am typing this on it (in windows, regrettably).

---

### Post by aheckler on 2009-02-10
Maybe play around with the keyboard mapping in the first few stages? See if that helps any.

---

### Post by TAFKARS on 2009-02-11
> **aheckler said:**
> Maybe play around with the keyboard mapping in the first few stages? See if that helps any.

Tried this but no success, thanks for the reply though.

I have now tried 2 x 8.04 and 2 x 8.10 disks. The 8.04's just hang and I never get to the install prompt, the 8.10's make the keyboard fail and I am unable to input names & passwords etc.

Unless there are any other suggestions I will have to keep it XP only (a frightening thought).

---

### Post by TAFKARS on 2009-02-11
I have now installed 8.04 via the alternate cd. Whilst it seems to take an age to boot up, I'm putting that down to the low RAM and will upgrade this shortly.

I must admit that I am surprised that this was not suggested to me by other users?

Thanks for the replies that did come, though. :KS

---

### Post by snowpine on 2009-02-11
Hi Tafkars,

Ubuntu minimum system recommendations:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> 
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution 

A ram upgrade would help you immensely; if that is not possible, I would recommend going with a lighter version such as Xubuntu.

---

### Post by TAFKARS on 2009-02-11
Cheers for the advice, using the alternate is clearly designed for folks like me that have low RAM. I will indeed upgrade to 2GB, cheaper than buying a new machine!

Now if I could just figure out how to mark the thread as solved...:confused:

---

