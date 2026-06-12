---
title: "Updating from 8.04 to 9.04"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Miller9 on 2009-11-03
Hey All,

 I had installed 8.04 last year and want to upgrade to 9.10.
 I have a CD of 9.04, so I want to first upgrade to it and then to 9.10 [through internet].
 My problem is I have some GB of data on my 20GB partition of Ubuntu 8.04. 
 If I boot the 9.04 and install it in the 20GB partition, I ll be losing all my data.
 I want to keep my data and upgrade it to 9.04 through the CD I have.
 How can I do it?

Thanks a lot.

---

### Post by slakkie on 2009-11-03
You can't upgrade via a LiveCD, you need to have the alternate CD for this. See the link in my sig for how you can do this.

TBH, if you want to go from 8.04 to 9.10, you might want to install 9.10 to make use of ext4 and grub2.

---

### Post by Miller9 on 2009-11-03
Thanks Slakkie for your prompt reply.

I may run the bootable 9.04 CD and install it but what about my contents/data already present in my 8.04 Drive.  9.04 'll format the drive before installation right.
Is there a option while installation which can keep my drive contents and install 9.04 on top of it?

---

### Post by raymondh on 2009-11-03
Miller9, 

To retain your settings and files, you need to separate /home (which is where they reside) from root (/) - which is your ubuntu system files.

see this link:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

On installation (assuming this is a liveCD install of 9.04 jaunty), you select manual in step 4.  You then highlight the root partition you want to overwrite > edit > use as > select mountpoint (/) > format ext4 or ext4.  

Next step is to select the existing /home partition > edit > use as > select mountpoint /home > DO NOT FORMAT.  

By doing this, you are telling the installer to overwrite JUST the root partition and mount the existing /home.

Post back if you need clarifications.  As always, have a working back-up of your valuable files.

Was this what you were asking?

---

