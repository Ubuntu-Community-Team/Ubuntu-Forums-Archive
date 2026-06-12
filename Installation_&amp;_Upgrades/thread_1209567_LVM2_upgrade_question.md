---
title: "LVM2 upgrade question"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by dotnick on 2009-07-10
I am getting a new hard drive for my media center, simply because I'm scared that one of my hard drives is on it's way out.  I'm running a MythBuntu install.  1 hard drive is XFS, and the other ext3.  The XFS drive is mostly just recordings from MythTv, but my other drive has all of my other personal files.  I'm hoping to setup a software raid 1 type setup with the new drive with out losing any information.  

My tentative plan was to format the new drive as lvm capable and go through all of the steps to get a working file system on it.  Then to copy *everything* from my other to hdds over to the new LVM drive.

(I'm a little fuzzy on the steps that might need to be taken to boot off of my new drive (which is SATA-2 instead of my current EIDE).  

If i can boot off my new drive, I beleive I could then re-format my other two drives for LVM and then set them up for my software raid-1 configuration.

If this can be pulled off, I think there would be minimal downtime for actual use of the computer.  

Finally, here's my question :) .. Is this even possible and has anyone written a how-to that's even close to this request?  I saw the LVM-1 howto in the "Recipies" section, but I don't know how accurate it is with LVM-2.

Guidance requested,

---

