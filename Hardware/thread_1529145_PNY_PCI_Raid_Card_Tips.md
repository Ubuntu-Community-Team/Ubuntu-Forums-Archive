---
title: "PNY PCI Raid Card Tips?"
date: 2010-07-11
forum: Hardware
---

### Post by SuperLou on 2010-07-11
So, many years (I think 5) ago I made a media and backups server with the OS (Win XP) on one drive, and then a pair of HDs in raid 1 for the media/backups.  The raid was via a PNY SATA PCI raid card, and what I thought was hardware raid.  It did come with a drivers CD, which I should have set off a warning bell at the time.

Now, the server is going to become my main PC (after a snazzy CPU/mobo/graphics card upgrade) and I'm moving it to Ubuntu.  I noticed ubuntu sees the raid 1 configuration as 2 drives, which suggests it was software raid with some fancy Bios configuration options.

So, my question is, what's the best way to handle this PCI "RAID" controller?  I'd really like to use it in a way so that I can transfer the drives to a new PC if my mobo/cpu ever die, but I don't know if this is a pipe dream.  Can raid 1 drives be read without a raid controller?  I've read about configuring software RAID in Ubuntu and it's a bit easier in my case since I don't plan on booting from the RAID'ed drives.  Is software raid via Ubuntu the best plan?  Is there any real reason to use the PCI RAID card?

---

### Post by cj.surrusco on 2010-07-11
Ubuntu can be configured to use Software RAID, which is almost equivalent to fakeraid, which is what you most likely have. You can create a RAID setup using mdadm, which is the Linux program that controls the RAID setup.

You are probably better off using mdadm because Linux has little support for fakeraid cards. I use software RAID 5 for my Ubuntu installation, and I have had no problems after a few weeks.

---

### Post by SuperLou on 2010-07-12
Is there any disadvantage to doing fake raid through the fakeraid card then?  If I reinstall ubuntu, will I still be able to access the data on the softraid or is it similar to RAID where if the controller dies, you're out of luck?

---

### Post by cj.surrusco on 2010-07-12
Well I don't know about fakeraid since I've never used it. I'm not sure if you would be able to recover the data if the controller dies. But if you are using software raid, then there is no controller that can die. Therefore, the only thing you have to worry about is multiple drive failures (or a single drive failure in RAID 0).

---

### Post by SuperLou on 2010-07-12
I think as far as Ubuntu is concerned, the "RAID" card simply presents an IDE/SATA bus.  I'd rather not risk it doing something funny, so it sounds like the safest idea would be to just put the drives on the motherboard SATA ports and use software RAID.

If I understand you right, than if I were to put the drives on a linux box without any software RAID configured, once I reconfigured the RAID, I would be able to access the files again?

---

### Post by cj.surrusco on 2010-07-12
> **SuperLou said:**
> I think as far as Ubuntu is concerned, the "RAID" card simply presents an IDE/SATA bus.  I'd rather not risk it doing something funny, so it sounds like the safest idea would be to just put the drives on the motherboard SATA ports and use software RAID.

If I understand you right, than if I were to put the drives on a linux box without any software RAID configured, once I reconfigured the RAID, I would be able to access the files again?

That is correct. You would need to install mdadm and such, but you would be able to mount the RAID array just as it was.

---

### Post by SuperLou on 2010-07-12
Sounds good to me.  /dev/md0 is on its way to sinking :)

Thanks!

---

### Post by Return Privacy on 2010-09-08
Hi cj.surrusco,
I read your post here, and you seem to know how to setup and configure Raid on Ubuntu 10.04, so I figured I would learn from someone who has already done this.
I just did a new install of Ubuntu 10.04 on a Dell Optiplex desktop, it's only a P4, but it really runs great. I have Ubuntu OS installed on a 40gb ide hard drive, and there are 2 available sata ports on the motherboard. I did install a 500gb sata drive on one of the ports just to test if they work, and it works fine. I want to set up a Raid 5 to be for files and backups from other 3 computers on the network. Since I will need 3 or 4 drives for Raid 5, I figured I could get a pci sata 4 port card. I want to use 4 - 1.5tb or 2tb sata drives for this. My questions are, what pci 4 port sata card will work with Ubuntu 10.04, and how do I setup Raid 5? I am a beginner, for sure. I'm sure the software raid that comes on Ubuntu 10.04 will be fine for my purposes, unless you advise otherwise? If you can help me, please remember I am new. I was able to learn from articles on here how to add a second drive to the Ubuntu computer, and I got it formatted as ext3, and partitioned as one partition by downloading and using Gparted. (that's how I tested one of the sata ports on the motherboard)

---

### Post by cj.surrusco on 2010-09-08
> **Return Privacy said:**
> Hi cj.surrusco,
I read your post here, and you seem to know how to setup and configure Raid on Ubuntu 10.04, so I figured I would learn from someone who has already done this.
I just did a new install of Ubuntu 10.04 on a Dell Optiplex desktop, it's only a P4, but it really runs great. I have Ubuntu OS installed on a 40gb ide hard drive, and there are 2 available sata ports on the motherboard. I did install a 500gb sata drive on one of the ports just to test if they work, and it works fine. I want to set up a Raid 5 to be for files and backups from other 3 computers on the network. Since I will need 3 or 4 drives for Raid 5, I figured I could get a pci sata 4 port card. I want to use 4 - 1.5tb or 2tb sata drives for this. My questions are, what pci 4 port sata card will work with Ubuntu 10.04, and how do I setup Raid 5? I am a beginner, for sure. I'm sure the software raid that comes on Ubuntu 10.04 will be fine for my purposes, unless you advise otherwise? If you can help me, please remember I am new. I was able to learn from articles on here how to add a second drive to the Ubuntu computer, and I got it formatted as ext3, and partitioned as one partition by downloading and using Gparted. (that's how I tested one of the sata ports on the motherboard)

Yes, I would still recommend using software RAID in your situation. 

As far as the RAID card, I have found one that may suit your needs. It can be found on newegg.com [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816102065"). It has four sata ports, 3 gigabit speed, and Linux support (The reviews confirm the support), and is decently priced.

If you do decide to go with this option, you would want to set up the RAID using mdadm. First, install mdadm:
```
sudo apt-get install mdadm
```
Then you would want to prepare the partitions. Go into GParted, or a similar partition editor, and create a partition on each of the drives that you want to add to the RAID (Format doesn't matter). The partitions would have to all be the same size. 

Then, you would want to create the array
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3  /dev/sda1 /dev/sdb1 /dev/sdc1
```

*That is just an example, if you were to use 3 drives and the partitions were /dev/sda1 /dev/sdb1 and /dev/sdc1. Your RAID partitions may be different. If you are using 4 drives, then you would use "--raid-devices=4" instead of "--raid-devices=3", and you would add a third partition on the end of the command. You can post the command on this thread for myself or someone else to check. If you choose the wrong partition, you could lose data. 

Once you're done creating it, you would want to choose a mount point. The drive name will be /dev/md0, and you would put it in the fstab like any other drive. See [here]("http://ubuntuforums.org/showthread.php?t=283131") for fstab info. 

Well, that should be it for now. Let me know if you have any more questions.

---

### Post by Return Privacy on 2010-09-10
Hi cj.surrusco,
Thank you very much for your detailed explanation. I will get that sata card and try to set it up. I'm going on a trip, so I'll have to try it in a couple of weeks. Again, THANK YOU very much for your help!

---

### Post by cj.surrusco on 2010-09-10
> **Return Privacy said:**
> Hi cj.surrusco,
Thank you very much for your detailed explanation. I will get that sata card and try to set it up. I'm going on a trip, so I'll have to try it in a couple of weeks. Again, THANK YOU very much for your help!

You're welcome. Have a nice trip!

---

