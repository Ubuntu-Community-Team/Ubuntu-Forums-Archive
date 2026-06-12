---
title: "really messed up my Ubuntu"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by saskatchewan on 2009-05-13
Ok, I really messed up my computer.

I have a Asus EEE 1000 and I installed easy peasy ubuntu 8.10.  Then for some stupid reason I tired updating to Ubuntu 9.04.  Things crashed really badly.
Now I am trying to do a reinstall from my USB (that has Ubuntu 8.10) but, when I reach the partioning screen neither of the partitions show up. It says that "No Root File has been Defined. Please correct from the partitioning menu."

But when I try to go to the Partition Editor, it will not open.

Can anyone help me or suggest how I can fix this?

---

### Post by pastalavista on 2009-05-13
That means you forgot to label a '/' partition, I think. Boot the CD in the live "try it" mode and use the Partition Editor in System > Administration menu before you try to install. It will give you a better look at what you have to do.

---

### Post by saskatchewan on 2009-05-13
I am not sure how to do that.

I have no cd drive, just USB.  I have figured out how to access the Partician Editor but still don't know how to set things up so it will recognize which particians to boot from.

---

### Post by pastalavista on 2009-05-13
You just have to tell it which drive to install on. If it can't find a boot sector, it will make a new one on the root '/' partition. If you're going to reformat the entire drive and start over, just enter / in the first partiton selection. It will take care of everything else. If you need to save part of your files you'll need to resize/shrink the drive and make room for a new / partition. You'll need the Partition Editor to do that.

---

### Post by saskatchewan on 2009-05-13
That is the thing.  When I try to tell it which partician to install on, none of the particians show up
I don't know how to get it to detect them

---

### Post by 3startuna on 2009-05-13
Yeah it sounds like you forgot to set a drive to "/" The problem is Ubuntu shouldnt allow you to continue installing without that defined.

I got that same error when I was doing my initial install all I had to do was specify one of the partitions as root. The partition you select as "/" will be where ubuntu will install the file system.

Ok I re read here's what I understand

You installed 8.10 it worked fine, you tried to update to 9.04 from Synaptec and It crashed on you 
So your trying to reinstall and now its not showing up your partitions

Correct? 

When the partioner screen comes up go to "Advanced" or Guided something like that, I dont remember what the actual option name was but it should be the last option.

Ubuntu gives you 1 option to use the entire disk.  The second option it finds some free space on your disc and installs there

and the third option the one you want allows you to pick a specific partition to install it on.

You should see this

I think what your looking at is option 1 "use entire disk" 

That option will display just 1 solid "blue" (or green I dont remember) bar.

Click the third option and if the partition exists it will come up.

Keep us posted.

---

### Post by saskatchewan on 2009-05-13
Yes, the I did screw up and try to install 9.04 and that is when my troubles began.

When I do the set up, when I reach the part to select which drive/partition to select, there are no drives to select.

If I had the option of selecting the entire 40 Gigs of flash I would use it.

So, I am going to have to think on this for a while.  

Can I format the partitions such that they will be boot drives?

---

### Post by saskatchewan on 2009-05-13
Thanks for your help but I am going to have to get away from this for a bit.  I have been looking at it for hours and am getting impatient.

I will have to leave it until later.

---

### Post by 3startuna on 2009-05-13
> **saskatchewan said:**
> Yes, the I did screw up and try to install 9.04 and that is when my troubles began.

When I do the set up, when I reach the part to select which drive/partition to select, there are no drives to select.

If I had the option of selecting the entire 40 Gigs of flash I would use it.

So, I am going to have to think on this for a while.  

Can I format the partitions such that they will be boot drives?

It sounds like your computer isnt even detecting the hard drive very weird.

check if your seeing it in your bios.

---

