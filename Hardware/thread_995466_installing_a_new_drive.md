---
title: "installing a new drive"
date: 2008-11-27
forum: Hardware
---

### Post by Silvernail on 2008-11-27
I have installed a second drive on my desktop. I have 8.04 on the master drive and all my other stuff I want to bring from my old distribution on the 200 g second drive.

How do I jumper them to be master - slave? ( I guesss that is the correct terminology )

I have searched every combination of words I can think of and google has not been friendly. I did not find it here.

Can someone help?
Dave

---

### Post by taurus on 2008-11-27
The first harddrive where Ubuntu is on should be a master and your new harddrive, second one, should be set as slave.  When you boot up, go into the BIOS to make sure that at least the system detects both harddrives in the right order.  Then, boot Ubuntu and use gparted in System -> Administration (if you don't have it already, install it with System -> Administration -> Synaptic Package Manager) to format the second harddrive with ext3 filesystem.  Then, all you need is to mount it and change the ownership of the mountpoint for that new drive from root to your login name, assuming you want to be able to write to it without using the root privilege.

---

### Post by Silvernail on 2008-11-27
Thanks for confirming what I remembered about the order in the cable.

On the back of each drive is 4 pair of pins, Am I correct, the pair on the left are master?  Which pair is slave? Pair #2 from the left?

The second drive is from another debian distrobution. Linspire 5.??
If I format the drive I will lose all the date. Since it is debian partitioned will it work with Ubuntu?

---

### Post by taurus on 2008-11-27
What manufacturer is your second harddrive?  Some of them would have a diagram about settings (master, slave, & single) on top of the drive.  Otherwise, you can go to their website and type in the model of your drive and look at the manual.

If you format the drive, all data on it will be gone.  So, if you want to copy the data from that second harddrive, then don't format it.  Just mount it before you can access it.

---

