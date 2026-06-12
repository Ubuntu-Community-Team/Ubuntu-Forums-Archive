---
title: "Will I be able to keep the files on my second hard drive?"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by mtsbspidey on 2009-10-17
I'm planning to make the switch completely. No dual boot, or Windows partition or anything like that. The thing is, the way I have my computer set up now all my programs are on one hard drive with the OS and all my files are on a second one. I understand that the programs are gone when I reformat and install the new OS, which is fine as most of them have Linux equivalents. 

But, will the second hard drive still work or will that have to be formatted as well? Will I lose everything?

---

### Post by amingv on 2009-10-17
You don't have to format it, but that space won't be used natively by Linux. You will be able to access everything on it though, as long as you format the right partition, leaving the other intact.

If you'd accept a recommendation from me, though, I'd suggest to make a backup of all the files and then format the other partition too and mount it on /home. Everything will work on it's natural way and you won't have to be messing around fstab or having to authorize every time the partition is mounted. But which option works better for you is entirely at your discretion.

---

### Post by oldfred on 2009-10-17
I like having a separate /data partition for data. I have mine mounted in my /home. I did not think creating a mount point and editing fstab was terrible difficult but I go back to the days of doing everything in CP/M and DOS.:)

You can also download from synaptic Storage Device Manager that will use a gui to create a mount and edit fstab in the background. If you drive has FAT or NTFS partition(s) all permissions (rights in windows) are given at the time of mounting. Linux ext3 or ext4 permisions can be changed after mounting.

---

### Post by mtsbspidey on 2009-10-17
So, my best bet would probably be to move everything to an eternal hard drive, reformat both internal drives to Ubuntu, then put the files back? It's a bit more time consuming, but it certainly does seem safer.

---

### Post by amingv on 2009-10-17
> **mtsbspidey said:**
> So, my best bet would probably be to move everything to an eternal hard drive, reformat both internal drives to Ubuntu, then put the files back? It's a bit more time consuming, but it certainly does seem safer.

Yes, that's what I'd recommend. Certainly better on the long run if you're going Ubuntu only.

---

### Post by mtsbspidey on 2009-10-17
[Hmmm]("http://officemax.shoplocal.com/officemax/Default.aspx?action=browsepagedetail&storeid=2420130&rapid=756899&listingid=-2088951312&pretailerid=-99861"), and I do have a $10 off coupon. Looks like I'm going on a field trip today.

---

### Post by oldfred on 2009-10-17
> So, my best bet would probably be to move everything to an eternal hard drive

I did not know they had developed eternal drives yet?:P I want one and yes that will be a lot safer.

---

