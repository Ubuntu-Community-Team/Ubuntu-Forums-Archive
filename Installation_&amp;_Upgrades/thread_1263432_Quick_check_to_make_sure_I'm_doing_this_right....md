---
title: "Quick check to make sure I'm doing this right..."
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by chessnerd on 2009-09-11
Alright, I'm finally installing Ubuntu on my laptop. I'm in the LiveCD right now and I'm ready to install, however, I need my 3 NTFS partitions to stay intact (two have Windows OSs (Vista and 7) and one has the backup files for making a Vista re-install disk). I did the manual partition preparation and just I want to make sure that what I did will install Ubuntu, with the grub bootloader, on the pre-prepared ext3 partition and while not touching the other ones.

All I did was choose the ext3 partition and then chose "/" as the mount point (as opposed to /boot, /home, etc.). I have a screenshot of the setup.

Sorry if this seems like a noobish question. I'm 90% sure I got this right, but that 10% is saying that if I don't make sure I could regret it... :P

---

### Post by Cheezespread on 2009-09-11
I dont see a swap assigned in the screenshot.

---

### Post by chessnerd on 2009-09-11
> **Cheezespread said:**
> I dont see a swap assigned in the screenshot.

When I've installed Ubuntu before I think it set up a swap partition automatically. Is that not usually how it works?

---

### Post by Mr Swillis on 2009-09-11
Yep, no swap there my fried. Looks like 4 primary partitions, so you're maxed out on that disk. HOWEVER, you don't really need a swap "partition". You can create a swap "file" instead after you have installed everything. 

Instead of having its own partition, the machine will swap out to this pre-allocated file within the / filesystem instead. The older geeks and performance nerds will tell you that a swap file isn't a good option and will perform slower than a swap partition, but if you're machine is good enough to run Vista, then it's good enough that you won't be able to tell one bit of difference in performance between the two.

If you decide to go the route of a swap file, then your current setup is fine and should not destroy your Windows partitions. The key ingredient, is the little checkbox next to "format". As long as you see your NTFS partitions all there and they are NOT checked, you are clear for takeoff. 

Oh yeah... and you may be asking "how do I create a swap file?". After you have installed the system, fire up the command prompt and do this:

```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1024000 
mkswap /swapfile
swapon /swapfile
```

NOTE: This will make a swap file of about 1GB. This is what I recommend from several years supporting Linux servers and running Linux desktops at home. If you want to make it bigger than 1GB, feel free, but it really isn't necessary. To change the size, just increment that "count=1024000" line by increments of 1024 for each MB you wish to add.

To have it enable on boot, add this line to the bottom of /etc/fstab:
```

/swapfile          swap             swap    defaults     0 0
```


Hopefully that helps you out (and hopefully I don't get flamed for recommending a swap file). Bottom line, your current setup should NOT fry your existing NTFS partitions, and you don't really need a swap partition (can't have one in that setup anyway unless you have another physical disk).

Swill

---

### Post by Cheezespread on 2009-09-11
> **chessnerd said:**
> When I've installed Ubuntu before I think it set up a swap partition automatically. Is that not usually how it works?

I believe you are still in the Live CD doing the partitioning . You could very well edit the partition space required for "/" and add a space equialent to twice your RAM ( Safest ) for swap.

---

### Post by chessnerd on 2009-09-11
Alright then, swapfile it is (I'm guessing this is pretty much identical to the "pagefile" in Windows). It seems to me the one big advantage of a swap partition is that, if you have multiple Linux OSs installed they can all use the same swap, which saves you disk space. Also, with a swap partition, Live CDs can use swap space, which is nice if you are testing it out on a slower system. However, as you noted, I'm maxed out with partitions so I couldn't have a second Linux OS unless I removed Vista or 7 (or got rid of the "Vista restore" partition) and I have plenty of RAM to test out distros on this thing sans swap.

Thanks for the help.

---

### Post by chessnerd on 2009-09-11
Thanks for the help Mr Swillis, I've got the swapfile up and running.

One thing I need to say: Man, compared to Vista, Ubuntu is like lightning! (with the emphasis on "light" :)).

---

### Post by Ptero-4 on 2011-09-19
> **Cheezespread said:**
> I believe you are still in the Live CD doing the partitioning . You could very well edit the partition space required for "/" and add a space equialent to twice your RAM ( Safest ) for swap.
Cheezespread. If you look at the OP's screenshot you'll notice that the OP's 3 malware collections + the ubuntu's "/" partition add's up to the 4 primary partitions that the mbr disklabel have as limit. Hence why he can't add the swap partition (at least without blowing some of his malware).

---

