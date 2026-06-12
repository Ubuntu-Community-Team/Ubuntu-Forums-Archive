---
title: "External drive mount order"
date: 2008-11-14
forum: General Help
---

### Post by LisaO on 2008-11-14
Using ubuntu 8.10 

I keep my music on an external drive.
When I boot up sometimes my music shows up on disk, disk-1 or disk-2
If it doesn't mount the external drives in the same order from the last boot, Rhythm Box of course can't find the music and I have to reload it and start over. 

Is there a way to pre-determine the mount order of my three external drives so the music would always show up where it was from last boot?

Thank you,
LisaO

---

### Post by taurus on 2008-11-14
You can modify your /etc/fstab and add some entries for those those drives, using UUID as a device name.

```
sudo blkid
```

---

### Post by LisaO on 2008-11-14
Thank you but I think that may be beyond my current knowledge. I'll search on what you've said and see if I can come up with the way to go about that.
[B]
UPDATED & SOLVED!![/B]

With much searching I've found something to work for me to solve this problem. I labeled my external hard drives thus making the mount point for them my new lables rather than disk  disk-1 disk-2 disk-3 etc. Now RhythmnBox knows exactly where my music file are with each boot no matter what usb port they happen to use. My image organizing program also knows where to find my images which are on another external drive.

I found an excellent HowTo [explaining how to]("https://help.ubuntu.com/community/RenameUSBDrive") do this step by step right in the community Ubuntu Documentation. Imagine that huh? Who would ever think to read the Documentation? *laffin*

---

