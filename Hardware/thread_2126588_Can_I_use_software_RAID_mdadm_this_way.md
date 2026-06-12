---
title: "Can I use software RAID mdadm this way?"
date: 2013-03-17
forum: Hardware
---

### Post by whitefish10 on 2013-03-17
Hi guys, I have three hard drives a 1.5 GB and two 500 GB. I have arranged the following as this :-

1 - 1.5 TB = two partitions one is root (\) and the other is \home.
2 - 500 GB = free
3 - 500 GB = free

Basicly I want to use the two 500 GB as my RAID 1 to backup my most important data. So far I have Ubuntu 12.10 installed and configured on the 1.5TB. Can I install mdadm and use it to make the two other drives as RAID 1 without effecting my Ubuntu installation?

I am still new to linux and I am looking throw google on how to do this (dont know how to use mdadm yet), so if you have any advise please let me know.


Note : I dont need the raid for my \home partition.


thanks,

---

### Post by I8NY on 2013-03-17
Assuming that I used mdadm during my install of Ubuntu 12.04, then yes. I have 2 HDD each with 2 500GB partitions. From that, I was able to raid one partition from each physical drive and create two raids on half of each HDD. It works fine so there should be no reason why you can't raid just your 500GB HDDs without affecting your current installation. I don't know how to raid with mdadm, it will be easier if you just did a reinstall and setup the raid then (unless you find a really good guide online). You will need the [**alternative**]("http://www.ubuntu.com/download/desktop/alternative-downloads") version of Ubuntu to be able to setup raid during the installation.

---

### Post by steeldriver on 2013-03-17
There's really no need to reinstall if you're leaving your system intact on the current non-RAID volume and just want to add a RAID storage volume

What you're describing is essentially how I have my mythbuntu box set up - I did a complete install (on an SSD fwiw), then added 2 big disks for data, created the RAID on them with the filesystem of choice, and mounted it at /storage/mythtv (with a bind mount back to /var/lib/mythtv). You can directly mount it somewhere in the existing filesystem, or use a bind mount or symlink.

---

