---
title: "Hidden windows partition"
date: 2009-03-05
forum: Hardware
---

### Post by mightymouse! on 2009-03-05
I'm relatively new to Linux and trying to set up my families computers to run on Ubuntu. I have set up a dell Inspiron B130 with Intrepid Ibex. Before I did the install I partitioned the 60 GB drive with 15 GB for the current windows system so that it could be dual booted. I installed from a flash stick made with UNetBootin but I never saw an option to install on a certain partition so I assumed Ubuntu overwrote the windows partition. The dual boot was only necessary for Adobe Photoshop but gimp can replace it so now I don't need the windows partition.

The problem I have now is that the 15 GB partition still lingers on hidden somewhere so I'm not sure how I can delete it. I downloaded gparted and it shows only the Ubuntu partition of 60 gigs but when I scan the root file system with filelight I can only only see 45 GB of file space. I've looked in BIOS and could not find any tools to help. I attached screen shots of the gparted and filelight.

Any Ideas?

---

### Post by Therion on 2009-03-05
Well I'm not sure why you're seeing the discrepancy, but I trust gParted implicitly.  It's showing /sda1 as having just under 56GB, which is what I would expect to see for a "60GB" drive.   

More to the matter at hand though, do you want to do a clean install of 8.10 or... What?  If you do, I'd suggest just using the LiveCD to install, and select the option for using the entire drive -- unless of course you want to set up a separate /home partition or something.  Either way though, you can rest assured your missing 15GB partition will be "wiped" and the space put to good use on the fresh install.

---

### Post by theozzlives on 2009-03-05
Some computer manufacturers put hidden partitions so you can restore your HD to factory defaults.

---

### Post by mightymouse! on 2009-03-05
> **Therion said:**
> Well I'm not sure why you're seeing the discrepancy, but I trust gParted implicitly.  It's showing /sda1 as having just under 56GB, which is what I would expect to see for a "60GB" drive.   

More to the matter at hand though, do you want to do a clean install of 8.10 or... What?  If you do, I'd suggest just using the LiveCD to install, and select the option for using the entire drive -- unless of course you want to set up a separate /home partition or something.  Either way though, you can rest assured your missing 15GB partition will be "wiped" and the space put to good use on the fresh install.

It looks like I might be trying to pull nails here, I was hoping that there was a way to restore this partition to the ubuntu root without having to reinstall. 15 gigs is to much to waste, so if it comes down to it I will have to reinstall. I spent a fair bit of time wrestling with the broadcom wireless driver and downloading the media that was on the windows from backup so I would really like to avoid the pain. If gparted is right, then the windows os files and the rest of the free space must be in a superior file hierarchy that also contains root. Is there a tool out there that can look do file analysis of the entire drive and not just the ubuntu directories?

Thanks for all of your help!

---

### Post by Therion on 2009-03-05
> **mightymouse! said:**
> It looks like I might be trying to pull nails here, I was hoping that there was a way to restore this partition to the ubuntu root without having to reinstall. 15 gigs is to much to waste, so if it comes down to it I will have to reinstall. I spent a fair bit of time wrestling with the broadcom wireless driver and downloading the media that was on the windows from backup so I would really like to avoid the pain. If gparted is right, then the windows os files and the rest of the free space must be in a superior file hierarchy that also contains root. Is there a tool out there that can look do file analysis of the entire drive and not just the ubuntu directories?

Thanks for all of your help!
Try using a Parted Magic LiveCD (Parted Magic is the new name for gParted).  It's a tiny download and I'm curious if that will reveal what's going on here.  

It will also allow you to reconfigure your existing partitions "on the fly".

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by mightymouse! on 2009-03-06
> **Therion said:**
> Try using a Parted Magic LiveCD (Parted Magic is the new name for gParted).  It's a tiny download and I'm curious if that will reveal what's going on here.  

It will also allow you to reconfigure your existing partitions "on the fly".

[http://partedmagic.com/](http://partedmagic.com/)

I installed parted magic and after rebooting and running a scan from the live cd it gave me the same output as gparted. There were no other partitions and file analysis only showed ubuntu's root directory. I looked around for non-linux tools that might be able to view the entire drive but couldn't find anything useful. I started ripping the entire root directory apart looking for it, deleting everything I could see from inside ubuntu and still couldn't find any sign of my 15 GB. Eventually I couldn't even manage to boot ubuntu so I just wiped the entire partition and will reinstall, hopefully with the entire drive!

---

