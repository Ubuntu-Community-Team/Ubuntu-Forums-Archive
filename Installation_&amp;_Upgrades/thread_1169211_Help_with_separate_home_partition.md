---
title: "Help with separate /home partition"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by LeeU on 2009-05-22
In your "Create a separate home partition" I just had one question before I begin. You mention copy and pasting some of the code. This is probably obvious but I just want to make sure I am clear on this -- I would open a browser with that tutorial while I am doing this rather than printing out the instructions?

Thanks for all your work, BTW. I appreciate it!

---

### Post by aysiu on 2009-05-23
Yes. Web browser open. Terminal open. Copy. Paste.

---

### Post by LeeU on 2009-05-24
Thanks, that's what I figured. Now I have another problem. When I tried to create a new partition, I received an error notice that I can't create more than 4 partitions. I had purchased the computer from Dell and the hard drive looks like the attached graphic. Any ideas what to do here?

---

### Post by Sef on 2009-05-24
> LeeU 	 		 Thanks, that's what I figured. Now I have another problem. When I tried to create a new partition, I received an error notice that I can't create more than 4 partitions. I had purchased the computer from Dell and the hard drive looks like the attached graphic. Any ideas what to do here? 

You cannot create more than 4 primary partitions.   Windows needs to be on the first primary partition.  Put Windows on there, and then create a logical (extended) partition that you can subdivide as much as you want.  For example, on a 100 GB hard drive:  20 gb primary partition for Windows and then the other 80 gb would be an extended partition.

---

### Post by LeeU on 2009-05-25
I don't want Windows on it. I never mentioned Windows. I already figured out I can't  have more than four partitions. I want to create a separate home partition and am trying to figure out how to change the disk so I can do that.

---

