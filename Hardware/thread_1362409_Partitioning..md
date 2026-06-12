---
title: "Partitioning."
date: 2009-12-23
forum: Hardware
---

### Post by Ttrain15 on 2009-12-23
I don't know if I am supposed to post this here, but I can't find where I should post it. I am just wondering how I access the partition device thing so I can create some extra space so I can Dual Boot Vista because I am a gamer and Linux doesn't have very many MMORPG's that I like. Any help would be great!

---

### Post by adam814 on 2009-12-23
Install the gparted package.  Then go to System > Administration > GParted for a graphical partition editor.

A cautionary note: While the GUI is fairly intuitive it is possible to do destructive things with it.  A full system backup first might be a good idea.

---

### Post by James Dee on 2009-12-23
if you want create NTFS partition, you should do it with liveCD.
[http://maketecheasier.com/resize-create-partitions-with-gnome-partition-editor-gparted/2009/01/06](http://maketecheasier.com/resize-create-partitions-with-gnome-partition-editor-gparted/2009/01/06)
or you want to resize windows partition.

---

### Post by Ttrain15 on 2009-12-23
Alright, I don't think I can partition inside the program, so I will use the CD to see if I can't do it. I'll let you know if it works.

---

### Post by adam814 on 2009-12-23
That is correct.  You can't resize a partition if it is mounted and you can't unmount your root partition.  But it should work with the LiveCD.

---

### Post by Ttrain15 on 2009-12-25
Ok, I have put the cd in, but I dont want to create a new partition with Ubuntu on it, so how could I go about getting a new partition thats empty to install Vista?

---

### Post by Fir3chi3f on 2009-12-25
Within the live CD you can just use GParted in System->Admin->GParted.
Its a nice gui interface if you have anymore trouble post back.

---

### Post by Ttrain15 on 2009-12-25
I did that already, and I screwed up Ubuntu so I had to re-install Ubuntu. Unless you can think of how to safely partition it without screwing up Ubuntu?

---

### Post by Fir3chi3f on 2009-12-25
From my understanding, you currently have ubuntu install on your computer and now you want to put windows back on so that you can dual boot both of them? Or you just want to get rid of ubuntu completely and want just windows?

---

### Post by Ttrain15 on 2009-12-25
If I wanted to get rid of Ubuntu, I would have with no problems by now, because its not that hard. I want to put Vista back on so I can play MMORPG's that Linux can't play. I'm thinking that if I want Vista back on I would have to fully install it, and re-install Ubuntu back on after. Is there a way to partition safely within Ubuntu, or should I just wipe Ubuntu and then re-install after I get Vista on here?

---

### Post by SuperSonic4 on 2009-12-25
> **Ttrain15 said:**
> If I wanted to get rid of Ubuntu, I would have with no problems by now, because its not that hard. I want to put Vista back on so I can play MMORPG's that Linux can't play. I'm thinking that if I want Vista back on I would have to fully install it, and re-install Ubuntu back on after. Is there a way to partition safely within Ubuntu, or should I just wipe Ubuntu and then re-install after I get Vista on here?

You can safely install from ubuntu - use  gparted to create a new, empty ntfs partition. Use the CD if you intend to resize the partition with ubuntu on.

You can resize the ubuntu partition and hit apply leaving it there - vista's installer can easily install to the blank partition.

Easiest of all is to delete ubuntu, use vista's partitioner to put windows on and then install ubuntu from the live CD as this will fix grub by itself but data will be lost

---

### Post by Mahngiel on 2009-12-25
yes, you can partition inside of ubuntu. 

assuming you have gparted installed (sudo apt-get install gpared if you do not)

1. 'sudo gparted'
2. if ubuntu uses your entire disk space, you need to back out, and perform this from the liveCD. Don't worry about having to download gparted, it's already on the cd.
    2a. If this is the case, you need to resize ubuntu to the size you desire
3. Create a new partition, format = NTFS, and label it "Vista"
4. Insert Vista CD and when you get to the install sector when you create the partition, you should see the Vista partition with NTFS format. install it here.

Now, you made comment that you had to reinstall ubuntu.  You may wish to install ubuntu **after** vista again, because M$ takes over your bootloader (GRUB).  Either that, or visit [this page.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

