---
title: "How do I make SATA Drive Primary (ie &quot;sda&quot;), not IDE?"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2008-03-17
Not having had a SATA drive before, I've just noticed that my main drive with Ubuntu and Windows XP has become **sdb**, though when I installed it (prior to slipping in one of my IDE drives) it was **sda**. I only noticed coz I couldn't get my **fstab** entries working, and was fooled by my Windows partition being mounted as **/dev/sda1** (I now realise this is just the mount point Ubuntu automatically created for it, hehe).

Now, Ubuntu loads quite fine and all, and in **fstab** sure enough my Windows and Ubuntu partitions are listed as being on **sdb**, so no nightmare non-booting drama, but I was wondering how I can force my system to make the SATA drive **sda** again. I'm very familiar with the old Master/Slave Primary/Secondary routine for IDE drives, but am new to SATA, as I said.

With my new motherboard (and all new ones it seems), there is only one IDE channel for 2 devices, so figured the SATA drives take preference (ie: the 1st SATA drive becomes the "Primary" or sda in Linux terms). What also helped me come to this conclusion is that when I slip in the IDE drives, it doesn't even matter if they are set to Master or Slave (via the jumpers, of course). So I figured SATA now rules, and my IDE drives are like "Secondary" backup drives.

But doing an** fdisk -l** and looking into Gparted showed me this assumption was wrong, which cleared up why **fstab** wasn't mounting the partitions on the IDE (ie: I had to change all the **sdb** entries to **sda**).

So how do I rectify this? I would have assumed the BIOS, but the SATA is already set as the 1st boot device, and I can't even choose the IDE. I am also pretty sure I plugged the SATA into the #1 slot, if that is at all a factor.

While everything is being mounted fine, and adding the IDE for the first time after installation of Ubuntu didn't stop the system from booting, I ask (besides the fact I like to know these things, hehe) because should I stick in another IDE drive, I am not sure if Ubuntu will cope with the SATA suddenly becoming **sdc** (or more likely **sdd**, if the DVD drive takes **sdc**).

Any pointers on this situation would be welcome. Cheers

---

### Post by Rocket2DMn on 2008-03-18
The only thing I can think of is for you to change your fstab to use UUIDs rather than sd* entries.  Here is a quick way to see the sd* and UUID entries side by side:
```
ls -l /dev/disk/by-uuid/
```
There was a sweeter way to do that, but it has skipped my mind.  ^ that works :)
Then you can plug in and remove drives to your heart's desire without screwing up your fstab and mount points.

---

### Post by OzzyFrank on 2008-03-18
That's probably the best bet, as now my IDE is back to sdb, which sort of makes my fstab entries useless, hehe! I had worked around the fact that I'd be switching the IDE with others by creating multiple entries for sda, which didn't cause any problems, and worked. So, it would look for both ext3 and ntfs on sda1 for example, and mount the one it found and ignore the other. Except now of course it going back to sdb makes that impossible.

My Ubuntu and Windows XP x64 partitions on the SATA drive have in fact been added to fstab as UUIDs, which I assume is standard with an Ubuntu install these days, probably so when sda becomes sdb etc, people can still boot up. I remember this was a big problem for new users back in Edgy (and a hassle for experiences Linux users too). I got that happening a few times after the first couple of kernel updates to Feisty... I knew how to fix it but it was a pain to do so.

UUIDs are the way to go, as it doesn't look like this sort of thing (drives playing musical chairs) is going to stop soon (but hey, at least the "main" drive stays where it is and Ubuntu boots, and GRUB isn't useless).

What I reckon would be a good tool for an upcoming version would be one that adds fstab entries based on UUIDs with the click of a button. So if you add another drive that will be used as another removable storage device, it will be mounted upon the next boot.

Thanks for your suggestion. I'll fix up my fstab accordingly. Cheers

---

### Post by Rocket2DMn on 2008-03-18
I've actually been throwing around the idea of programming up a simple GUI for editing fstab.  If I get around to it, I'll be sure to add the ability to use UUIDs (or even use them by default).

---

### Post by OzzyFrank on 2008-03-29
Hey, can you let us all know when you make that app, as it sounds great! Cheers

---

