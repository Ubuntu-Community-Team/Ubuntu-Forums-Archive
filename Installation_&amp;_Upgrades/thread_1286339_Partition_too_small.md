---
title: "Partition too small"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by benleedy on 2009-10-08
I installed and upon first bootup it told me I didn't have enough space partitioned. It asked if I wanted to go back to the partitioner and I clicked OK, but it just popped up immediately with the same dialogue box. If I click CANCEL I can finish booting and it seems like I'm good to go, but every time I boot, it gives me the partitioning error. How can I fix this?

---

### Post by Pumalite on 2009-10-08
Boot up your Live CD and post a picture of Gparted

---

### Post by oboedad55 on 2009-10-08
> **benleedy said:**
> I installed and upon first bootup it told me I didn't have enough space partitioned. It asked if I wanted to go back to the partitioner and I clicked OK, but it just popped up immediately with the same dialogue box. If I click CANCEL I can finish booting and it seems like I'm good to go, but every time I boot, it gives me the partitioning error. How can I fix this?

You can boot up with the LiveCD and use the partitioner to resize your partitions. You don't say, but I'm assuming you did a dual boot with Windows. If that's the case then defrag your hard drive before you mess with partitions.

---

### Post by benleedy on 2009-10-08
> **Pumalite said:**
> Boot up your Live CD and post a picture of Gparted

I'm sorry, I have no idea what that means. :confused:

---

### Post by benleedy on 2009-10-08
> **oboedad55 said:**
> You can boot up with the LiveCD and use the partitioner to resize your partitions. You don't say, but I'm assuming you did a dual boot with Windows. If that's the case then defrag your hard drive before you mess with partitions.

Yes, I did dual boot.

How do I boot up with the LiveCD?

---

### Post by Thetherumcompound on 2009-10-08
The CD you installed ubuntu with is your live CD.
Do what you did to install except choose the option that says "try ubuntu with out installing"(or something similar)
Then when ubuntu is booted goto
System--->Administration--->gparted

---

### Post by Daddy1 on 2009-10-08
I have the same problem, Laptop, dual boot with a Fujitsu 160gig drive, Partitions should be even almost but I had moved up from 8.04 to 9.04 and now when I want to do my security updates it says I don't have enough room. Will Partition Magic do the same I do I have to use  the gpart?

---

### Post by benleedy on 2009-10-08
FAIL. I burned the CD as data, not as an image. Let's try again.

---

### Post by oboedad55 on 2009-10-08
> **Daddy1 said:**
> I have the same problem, Laptop, dual boot with a Fujitsu 160gig drive, Partitions should be even almost but I had moved up from 8.04 to 9.04 and now when I want to do my security updates it says I don't have enough room. Will Partition Magic do the same I do I have to use  the gpart?

Windows is stupid. PM won't recognize Linux partitions. OTOH, Gparted or Parted Magic, [http://partedmagic.com/](http://partedmagic.com/), will resize NTFS partitions.

---

### Post by raymondh on 2009-10-08
> **benleedy said:**
> I'm sorry, I have no idea what that means. :confused:

Hello benleedy and welcome to the forums.

When you installed Ubuntu, did you choose "side-by-side"?  Did you use a "slider" to allocate partition sizes between windows and Ubuntu?

Kindly boot into the liveCD and go live session (try ubuntu without changes).  When in live session, access a terminal (applications > accessories).  In a terminal, type 

```
df -h
```

and
```

sudo fdisk -l
```

Kindly post back the results.  Copy/paste works best.

You can also post a screen shot of gparted if you wish.  To do so,

- live session
- access system > admininstratition > partition editor
- when gparted opens, press your 'prntscreen' key.  Save a screenshot to your current live session desktop
- on your next post, click on ATTACH (near the smiley face on top of the post window) > browse to your desktop and select the screenshot > upload

Regards,

---

### Post by benleedy on 2009-10-09
Thanks for the help guys. I re-burned the disk as an image, then re-installed Ubuntu wiping everything else. Works fine now.

---

