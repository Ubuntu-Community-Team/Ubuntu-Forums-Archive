---
title: "How do I convert Intel RAID to unubtu?"
date: 2008-07-29
forum: General Help
---

### Post by rmjohnson144 on 2008-07-29
I have a 3 drive RAID 5 I would like to use in Ubuntu.  Is there an easy way for it to be read?  I would be willing to manually convert it if nothing else.

btw, it is a ICH9R RAID 5.

-=Mark=-

---

### Post by rmjohnson144 on 2008-07-30
I also have an eSATA drive I hooked up and it won't recognize it either.  I think it's on my JMicron controller with a SATA to eSATA PCI-slot adapter.  I think it is also formatted in ide mode or maybe AHCI, but not sure.

I thought this would be easy to setup, but I guess not.  I found a couple articles on creating a RAID volume for install, but I can't remember where I saw it.  It looked quite involved, but if that's what it takes I guess I can do it.

anyway, does anyone have a link to a SIMPLE way to get RAID working and/or eSATA working?

-=Mark=-

---

### Post by rmjohnson144 on 2008-08-02
OK, I'm halfway there with the eSATA drive.  I booted to my Vista drive to check on the eSATA drive and it didn't show up there either.  I check the back of the computer and sure enough the eSATA cable is part way out.  I reboot while making sure both ends were in all the way and power cycled the external eSATA drive.  I then go insto Vista and my eSATA drive shows up fine.  

I rebeoot and go into the BIOS again and tell it to boot from the ununtu drive and viola I see my 500GB drive in "computer" menu, but it won't let me open it.  It asked for permissions and after I put in my password it says can't mount device and the device is busy.

Is this a real error?  Or is the drive unreadale?  It is formatted in NTFS.  Do I need to make it FAT32 or something?  I remember having a utility for formatting USB drives to FAT I think for very large drives beyond the normal FAT limit.  Not sure if it'll hit 500GB for my drive or not.  Now if I can remember the name of the utility.

-=Mark=-

---

### Post by davidw89 on 2008-08-06
Same problem here!

---

### Post by fjgaude on 2008-08-06
The only way to use mainboard raid is to use a program called **dmraid** to read the raid array. The last time I looked dmraid cannot handle raid5, but can raid0 and raid1.

---

### Post by rmjohnson144 on 2008-08-16
> **fjgaude said:**
> The only way to use mainboard raid is to use a program called **dmraid** to read the raid array. The last time I looked dmraid cannot handle raid5, but can raid0 and raid1.

I found a few posts on setting up dmraid but I tried setting up dmraid a couple of times with no luck.

anyone have a good article on setting up dmraid?
--=Mark=-

---

### Post by fjgaude on 2008-08-16
Install dmraid from the repostitories... as said it only works with raid0 and 1, not raid5, at least that is the way it was awhile back.

Once dmraid is installed simply enter:

```
sudo dmraid -ay
```

You mount the array using the /dev/mapper/intel_xxxyyyzzz as the name.

```
sudo mount -t ntfs /dev/maper/intel_xxxyyyzzz /mountpoint
```

No raid5, but you might try it and see if you get an error with your existing array.

Also make sure you have ntfs-3g installed. That permits reading NTFS files created with Windows.

Let us know what happens.

---

