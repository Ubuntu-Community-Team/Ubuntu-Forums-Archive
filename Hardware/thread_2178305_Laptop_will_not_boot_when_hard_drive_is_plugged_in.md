---
title: "Laptop will not boot when hard drive is plugged in"
date: 2013-10-02
forum: Hardware
---

### Post by nick34 on 2013-10-02
Hi,

I just acquired an Asus laptop. It came with windows 7, which I replaced with Mint 15. The problem began after I decided to re-install my own Windows 7 license. The installation froze at the partitioner when I clicked 'Delete' for my linux partition, so I did a hard reboot and here is where I am at:

-When the hard drive is plugged in, the laptop will not will not boot past the first "Asus" screen. I cannot even access the BIOS, it just hangs there and gives no messages. 
-If I remove the hard drive, I can boot from a LiveCD or other media fine. 
-The laptop will boot with the hard drive from my other laptop in it and recognize the new one in the BIOS. 
-If I plug the Asus drive into my other laptop, the computer will boot and the drive recognized in the bios. (I can also hear/feel it spinning.)
-The Asus has an efi option: I have tried enabling and disabling it both (I think I may have accidently changed it once before the win 7 install and I'm not sure what the original setting was). 
- The Asus model # is UL80J. The drive is a Seagate 5400.6 (500gb) 


I'm really stumped with this. I can't think of any reason for this behavior. 

Thanks in advance!

---

### Post by Thee on 2013-10-03
This most likely means that the HDD is going to die... I could be wrong tho...
If the HDD is recognized in other computer, can you access its data too? Did you try to format the HDD while its in your other computer?

---

### Post by mkmanifesto on 2013-10-03
If the system posts without the hard drive plugged in than that more or less means you need to replace the hard drive. Like Thee suggested try accessing the HDD from another computer and if possible try to blast the hard drive with Mengis Boot 98 if you can find a copy. Also you can make an UBCD and try to run a few HDD diagnositc tools.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by oldfred on 2013-10-03
From other computer what does Smart Data show on drive. It can run lots of tests, but all I really know is passed is ok and warning or failing is bad.
You can access Smart data easily from Disks or Disk Utility with Ubuntu or liveCD. Just click on drive in left panel and Smart Data is on right.

 smartctl and smartd
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T)
      
 Disk Utility screen shots
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

### Post by Yellow Pasque on 2013-10-03
> If I plug the Asus drive into my other laptop, the computer will boot and the drive recognized in the bios. (I can also hear/feel it spinning.)
Can you boot a LiveUSB/CD with it plugged in? If so, I would do that, run gparted, and create a new partition table on the drive (will erase everything).

---

