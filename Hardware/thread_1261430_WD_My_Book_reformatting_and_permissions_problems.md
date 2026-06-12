---
title: "WD My Book reformatting and permissions problems"
date: 2009-09-08
forum: Hardware
---

### Post by pikeman47 on 2009-09-08
I bought a WD My Book 'for mac' and formatted it from hsf+ to ext4 for use on my ubuntu desktop. Now that I've done that, the drive no longer shows up in the usual place for mounting under Places and the only way I've found to be able to mount it is by going into GParted and mounting through there. Once it's mounted, when I try to drag anything into it, it says I don't have permission to do so. In the best of all possible worlds, I would want for this hard drive to automount on boot, use ext3 or ext4 as the filesystem and obviously be readable/writable. Help please.

---

### Post by SoftwareExplorer on 2009-09-08
Could you post the output of ```
sudo blkid
``` and tell me which one is the drive you are trying to set up?

---

### Post by pikeman47 on 2009-09-09
the output of sudo blkid looks like:

```
/dev/sda1: UUID="1c515482-7ef0-4040-859e-983644f3a828" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c935e399-2d63-4930-be0f-d6b5db2f2e3f" 
/dev/sdb1: UUID="44940896-6ac8-457d-a035-8a75811dacbe" TYPE="ext3" 
/dev/sda3: UUID="98386b0e-ba8e-410c-abfb-1e14bb65a9b3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="89221f89-daba-40fd-bbd3-11cd052e1961" TYPE="ext4" 
```

and i'm trying to set up /dev/sdc1

---

### Post by pikeman47 on 2009-09-09
Well, it seems to be automounting now and I figured out the permissions issue I was having. My only question now is why on my desktop it is displayed as '1000.2 GB Media' yet when I right click and go to Properties, it displays the total capacity as 916.9 GB? On top of that, I've begun putting files in it and it says that the contents are: 3,582 items, totalling 20.0 GB but when I look at the pie chart that graphically describes the disk usage, it says 66.8 GB used out of the 916.9 GB. Any ideas on what those 46.8 missing gigs are?

---

### Post by SoftwareExplorer on 2009-09-10
> **pikeman47 said:**
> Well, it seems to be automounting now and I figured out the permissions issue I was having. My only question now is why on my desktop it is displayed as '1000.2 GB Media' yet when I right click and go to Properties, it displays the total capacity as 916.9 GB? On top of that, I've begun putting files in it and it says that the contents are: 3,582 items, totalling 20.0 GB but when I look at the pie chart that graphically describes the disk usage, it says 66.8 GB used out of the 916.9 GB. Any ideas on what those 46.8 missing gigs are?
One idea: Do you have your trash emptied? Another thing is that some theres confusion about weather a gigabyte is 1024 MB or just 1000 MB. If you are getting frustrated, you might also [check this out.]("http://xkcd.com/394/") :)

---

