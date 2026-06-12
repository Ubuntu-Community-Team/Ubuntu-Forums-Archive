---
title: "Installation of Ubuntu 9.04 Jaunty"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by atish.sihi on 2009-06-07
Hi,

   I am using ubuntu 8.04 hardy heron. I want to upgrade the OS with Ubuntu 9.04 jaunty. Kindly let me know how I can install it without losing any data. Kindly let me know the exact process.Can I over write the OS?

Regards,
Atish Sihi

---

### Post by hal8000 on 2009-06-07
Personally, I would never upgrade as it takes sometimes 2 or 3 times as long to solve all dependencies and you are upgrading two verions 8.04-8.10-9.04

Safest is to backup all your user data, bookmarks, work, downloaded files etc and install Jaunty. You installed 8.04 so its the same for installing Jaunty.

---

### Post by atish.sihi on 2009-06-07
Thanks for the reply. There are four partitions in my hard disk. Should I only format the partition which contains the OS? I hope I will not lose data from the other 3 partitions. So I can keep all my bakc ups in those 3 partition. Kindly let me know what should I do?

---

### Post by Partyboi2 on 2009-06-07
Format your / partition, you can do this by choosing "manual" partitioning when installing 9.04 and selecting the option to format / as well as reset the mount point back to / for that partition. 
Remember to backup your stuff before working on partitions.

---

### Post by ugm6hr on 2009-06-07
Using the 9.04 LiveCD, select the "Manual" installation option.

Ensure you identify your current / partition (for your OS), and mark that to be formatted, with a mount point of "/"

**Ensure no other partitions are marked to be formatted**, and are not marked with any mount points.

The rest should be straightforward.

---

### Post by raymondvillain on 2009-06-07
I have the same problem as atish.sihi, but how does one identify the / partition?

And if I do identify that, how do I mark it to be formatted?

I can easily get to that point in the installation procedure where I choose manual partitioning, but going forward from there it gets scary.

Any and all suggestions would be greatly appreciated.

I tried to upgrade to Jaunty and this resulted in LOTS of problems, so now I want to install 9.04 on top of itself without losing anything.

---

### Post by ugm6hr on 2009-06-07
> **raymondvillain said:**
> I have the same problem as atish.sihi, but how does one identify the / partition?

And if I do identify that, how do I mark it to be formatted?

You need to know where you installed it.  We may be able to guess from the output of:
```
sudo fdisk -l
```

However, only the person who installed it will know for certain.

You could use a LiveCD to try and locate the installation on your HD.

On the manual installation screen, there is a box next to each partition that you click on to put a tick into.

---

### Post by raymondvillain on 2009-06-07
Thanks, Ugm6hr.  sudo fdisk -l gives me the sizes of the partitions.

Using Applications>accessories>disk usage analyzer I can see the size of / and from that guess that it is a certain /dev/sdc6 (the size of which is given from the command sudo fdisk -l), but this seems risky to me.

On the other hand, when I tried installing from the live CD, the partition screen showed one partition (/dev/sdc12) with the label "Ubuntu 9.04". I imagine that must be because Jaunty already resides on my system. Does this mean that this is the / partition? The one labeled Ubuntu 9.04?

---

### Post by raymondvillain on 2009-06-07
Howdy folks!

To find which partitions are on which devices, open a terminal and use the df command!

I found that bit of advice in the "Teach Yourself Unix in 24 hours" book.

What luck.  Hope this helps some other lost souls.

---

### Post by atish.sihi on 2009-06-07
thanks a lot for the active cooperation.....

---

### Post by ugm6hr on 2009-06-07
> **raymondvillain said:**
> Does this mean that this is the / partition? The one labeled Ubuntu 9.04?

I am afraid I have no idea.  As I said, only the person who installed it can tell you for certain.

The partition with directories /boot, /var, /opt etc from the LiveCD is likely to be an existing Linux installation, but again none of this is 100% reliable.

EDIT:
Of course, ***df -h*** will identify the current active partition!

---

### Post by utnubuuser on 2009-06-07
yeah -  nice - re "teach yourself linux in 24..." MSWidows format?

---

