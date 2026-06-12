---
title: "Ssd+hdd"
date: 2016-06-07
forum: Hardware
---

### Post by canhoto on 2016-06-07
Hi.
I'm running Ubuntu 15.10 on my new laptop which has a SSD drive. I'm running Linux Mint on my desktop with a HDD. My laptop is incredibly faster, just because of the SSD (the other hardware features are not so different), especially on boot

So, I would like to install Ubuntu on my desktop with a combination of a (new) SSD and an HDD. SDD much more for reading, booting, etc (all that requires speed). and the HDD for writing, etc. I looked for a tutorial on how to do that from scratch (partitioning, etc), but I can't find a good one.

Any help?

Thanks

---

### Post by oldfred on 2016-06-07
Is system UEFI or BIOS?
Is current drive gpt partitioned?
Post this:
sudo parted -l

I use a smaller system partition for Ubuntu of 25 or 30GB on SSD and have all data in /mnt/data on HDD with all folders normally in /home linked to my /home. This works well if you have multiple installs as then you can have same data in all installs. If only wanting one install, you can just put /home on HDD with system on HDD, but your user settings in /home are on slower drive. 
But with Linux speed with SSD is only on initial loading as Linux caches recent activity in RAM which is even faster than SSD.

Some examples.
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) [http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

Also lots of data in link below in my signature.

---

