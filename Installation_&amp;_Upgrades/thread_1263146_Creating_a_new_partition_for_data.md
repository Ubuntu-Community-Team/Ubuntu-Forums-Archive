---
title: "Creating a new partition for data"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by alexeix on 2009-09-10
Hi,

I've done a fresh installation of Ubuntu Jaunty and everything's working well so far.

Is there any benefit in creating another partition for storing my music and video files?

Other than making it easier to image my system partition by keeping it relatively small, is there any performance gain?

---

### Post by Partyboi2 on 2009-09-10
An advantage of storing your music and video files on a separate partition is that if you ever need to format your / partition you will not have to backup all your music and video as they are on a separate partition. I wound not think there would be any performance gain.

---

### Post by running_rabbit07 on 2009-09-11
This[ link]("http://www.psychocats.net/ubuntu/separatehome") will teach how to make a /home partition if you want.

---

### Post by alexeix on 2009-09-11
Thanks for the link and advice.

I followed the steps at the link and everything seemed to go fine, but when the resizing of the partition had finished, I was left with two ext3 partitions with used space 5.63GB and 7.07GB respectively.

The problem is that my system partition should have contained roughly 12GB of used space, so I'm concerned that something may have gone wrong.

I haven't yet moved my home directory to the newly created partition.

The 5.63GB used space is on the shrunk partition and the 7.07GB used space is on the new partition (created from the unallocated space).
Make sense?

The new partition is called /dev/sda3, but I didn't manually set that, so Gparted must have.

Is everything okay for me to proceed or has it all gone wrong?!?

---

### Post by alexeix on 2009-09-11
Okay, so I persevered and although I couldn't boot, there were some further instructions to sort that out.

I'm now able to boot into Ubuntu and all looks as it should, with the exception being the actual partitions.

I've attached a screenshot, so please can someone take a look and let me know what they think?

I don't understand why my 'used space' is now split between the first partition and the additional second one which I created.

This is a pure install of Jaunty plus a number of applications loaded, but no music, video, other files as yet.

---

### Post by ezsit on 2009-09-12
Formating a partition always uses some space just for the formatting and the journal. Plus, some of the drive space gets reserved for root. I do not have a partition that large, so I cannot guess at the amount of used space just for formatting, but since your /home partition is empty and its quite large, then 7GB of space is being used by the file system and root's reserved space. When your system consisted of a single partition, this was also the case, but you could not tell the used space in actual files from the file system overhead plus root's reserved space. Make sense?

---

### Post by alexeix on 2009-09-12
What I don't understand is that my used space was 12gb when I had one partition.
I then reduced the size and created a second partition for holding data.
So (1) why is the used space now split between the two partitions when I had not yet moved my /home folder or anything else?
That's what appears to have happened.

For example, if I want to image my Ubuntu installation - just Ubuntu and applications, not data, (2) do I just image 
/dev/sda1?

Also, (3) do you think my system partition is too large?

Sorry if this is a stupid question - this is my first experience of disk formatting in Ubuntu.

Thanks.

---

### Post by Bartender on 2009-09-12
I can't answer your imaging question.

As far as the partitioning goes, I think you should congratulate yourself.  I gave about 27GB to / on my 320 GB laptop drive.  I've added dozens of relatively complex applications such as Cinelerra and Audacity, and the partitioner is reporting 4.29 GiB used, 23.65 GiB unused.  So, yeah, you and I both probably gave more space to / than necessary.
But, you know what?  Who cares?  I'm not worried about it, and you have a larger drive.  Next time you can make / 15 GiB or maybe even 10.
+1 on ezsit's comments.  There will always be some used space showing, even on a brand new partition with "nothing" on it.  We say "nothing" but any usable partition will have some data in place that does the stuff ezsit described.  Your screenshot looks fine.  

Go ahead and enjoy!

---

