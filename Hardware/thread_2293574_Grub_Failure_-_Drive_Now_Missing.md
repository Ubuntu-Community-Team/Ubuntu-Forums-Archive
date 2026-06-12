---
title: "Grub Failure - Drive Now Missing"
date: 2015-09-05
forum: Hardware
---

### Post by Glenn_Jarvis on 2015-09-05
Machine is a dual boot Win7/Ubuntu with Ubuntu 14.10 on dev/sdc (E Drive). Never had a problem till today. Rebooted to load Ubuntu and received the following...

error:no such device
8959f11c-0553-4c93-96aa-18275cf0efe4
Entering rescue mode...
grub rescue>

Tried set
ls
set prefix= <as per data needed>
set root= <as per data  needed>
insmod normal

unknown file system

tried grub-install /dev/sdc and received a failure, couldn't find the device

Eventually I loaded my Windows 7 install and ran the repair procedure (bootrec /fixmbr  &&  bootrec /fixboot).
I can now boot up to Windows 7. However, E Drive is still missing. I rebooted with the Ubuntu LiveCD and it couldn't find the drive/device either. I then tried loading GPartition. It could see the drive but no partitions. In fact it claimed there was a 3gb unused partition.  I can't remember the size of the drive now, but it's over 250GB. Not sure what else I can do as the drive had a linux and a windows partition. I really need the Windows partition part back if I can. I noticed in my system bios it now identifies the drive as a ST_M13FQBL  which doesn't seem to be a standard Seagate model number.

Thanks for any suggestions that might work.

---

### Post by Bashing-om on 2015-09-05
Glenn_Jarvis; Hello;

From the liveDVD, let's look at what is on the hard drive(s):
post back - Between code tags, please - the outputs of terminal commands:
```

sudo fdisk -lu
sudo blkid

```

Maybe then, consider installing grub.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by weatherman2 on 2015-09-05
Check the hard drive itself - make sure it isn't failing.  Check S.M.A.R.T.  From an Ubuntu live boot, you can install GSmartControl (enable "Universe" repository first maybe) or grab the free Parted Magic (find the free version from a few years ago on Major Geeks - GSmartControl is pre-installed and called "Disk Health").  Look at the S.M.A.R.T. Attributes in GSmartControl.  Attributes in pink/red are the ones you should be worried about.  Current Pending Sector Count > 0 is bad news usually.

You can also run S.M.A.R.T. tests that way - at least, run the short test, should take only a minute or two.

If the short S.M.A.R.T. test completes successfully and there are no bad Attributes, the drive is probably OK.

At that point, I'd run e2fsck on each Linux partition (except swap) using a Ubuntu live boot.

Finally, re-install Grub from a Ubuntu live boot using the "chroot" method:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

Maybe something just got corrupted if there are no S.M.A.R.T. issues.

---

### Post by Glenn_Jarvis on 2015-09-05
Thanks weatherman2, I've looked at the ST_M13FQBL and apparently when it shows up in the bios, the drive is toasted. This is the third Seagate that has died under Ubuntu. It's weird, but I'll chalk it up as a coincidence. Time to order a new drive.

---

### Post by weatherman2 on 2015-09-05
I've replaced lots of bad hard drives from different manufacturers, not just Seagate.  But, Seagate has had a higher than usual number of failures statistically in certainly classes of drives in the last few years as some recent articles have pointed out.  I always assume any drive I am using will fail at some point so make backups accordingly and plan ahead.

Good luck!

---

