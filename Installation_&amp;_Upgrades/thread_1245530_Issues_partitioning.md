---
title: "Issues partitioning"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2009-08-20
Hey, the ubuntu liveCD was 100% compatible with my laptop so I decided to go ahead with the install.
My laptop has vista and the factory restore partiton (roughly 8 gig)

So C: and D: I know that C: has about 10GB free space (what I was going to use to install ubuntu), IN gparted, the drive has a orange triangle with an exclamation mark in it? Used and Unused values show: --- 
And it wont let me make the drive any smaller to make way for an ubuntu partition. Please help
Thanks

---

### Post by Colo2 on 2009-08-20
No one able to help me on this?

---

### Post by Bartender on 2009-08-20
Colo -
Plug in a thumb drive when you get to the LiveCD desktop, then go to the partitioner.  When you've got the partitioner up, go to Applications>Accessories>Screenshot.  Take a screenshot, but make sure to save it to the thumb drive.  
Then get out of the LiveCD and get back to Windows, to this thread, and attach the screenshot that's on the thumbdrive.

---

### Post by raymondh on 2009-08-20
> **Colo2 said:**
> Hey, the ubuntu liveCD was 100% compatible with my laptop so I decided to go ahead with the install.
My laptop has vista and the factory restore partiton (roughly 8 gig)

So C: and D: I know that C: has about 10GB free space (what I was going to use to install ubuntu), IN gparted, the drive has a orange triangle with an exclamation mark in it? Used and Unused values show: --- 
And it wont let me make the drive any smaller to make way for an ubuntu partition. Please help
Thanks

Were you trying to use gparted to shrink and create a space/partition and then install Ubuntu?  Gparted will not work on any partition that is mounted.  If you were using gparted from the liveCD,  also select swapoff for swap.

I would suggest (after backing up your files) :

1.  Defrag c drive.  2x if you have the time.
2.  Use Vista's disk management tool to resize C: and create free/unallocated space. 
3.  Then boot into the liveCD and install.  You can either choose "install in largest continous space' (something to that effect).

* as you may know, you always have the option to back-out until step 7 of the installer.

---

### Post by Colo2 on 2009-08-20
thank you for your kind replies, I will check this out tomorrow morning :)

---

### Post by presence1960 on 2009-08-20
> **Colo2 said:**
> Hey, the ubuntu liveCD was 100% compatible with my laptop so I decided to go ahead with the install.
My laptop has vista and the factory restore partiton (roughly 8 gig)

So C: and D: I know that C: has about 10GB free space (what I was going to use to install ubuntu),

if all you have is about 10GB free on Vista's partition you are really going to be cutting it close on your Vista partition. You really shouldn't run a partition at close to full capacity.

---

### Post by louieb on 2009-08-20
> **presence1960 said:**
> if all you have is about 10GB free on Vista's partition you are really going to be cutting it close on your Vista partition. You really shouldn't run a partition at close to full capacity.

+1 I agree.  My rule of thumb is once a partition gets 80% full its time get more space from somewhere - even if it means a larger hard drive.

---

