---
title: "harddisk accessing problem"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2008-12-30
i had windows XP installed on my 60GB harddisk.i recently installed hardy on my machine using "install in windows" option in the c: drive which occuped 15GB.i was hoping to see the remaining 45GB accessible to both OS.however after installation the ubuntu OS shows only 5GB free and no partitions in filesystem/media.how can i gain access to my 80% harddisk?


during the process of installation it never prompted for any darddisk patition specifications.
what should i do?

---

### Post by taurus on 2008-12-30
You can try to config your ntfs partition with ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by stderr on 2008-12-30
I seem to recall that under Wubi, the rest of the drive you installed Ubuntu to (C: in your case) is visible under /host.

---

### Post by abhinav.p on 2008-12-31
no the rest host folder has only 2.7GB free.ant the output for sudo apt-get update is


E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by stderr on 2009-01-01
You're probably running Synaptic or the Update Manager at the same time. Only one app can access apt's caches etc at any one time.

You say that /host does exist? What do you mean by only having 2.7G free?

---

### Post by abhinav.p on 2009-01-01
i meant that host folder has only 2.7 GB free.the remaining part of hard disk is not visible in it...

---

### Post by doglover56 on 2009-01-01
This might be to your advantage. Are you sure you want Ubuntu messing around with your host operating system partition? That kind of stuff always makes me nervous. Make sure you have an air tight backup of your host partition and your data!

IMF

---

### Post by abhinav.p on 2009-01-01
> **taurus said:**
> You can try to config your ntfs partition with ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

ok i installed it.then what should i do?

---

### Post by stderr on 2009-01-01
Well all you do is run it as taurus suggested 

```
gksudo ntfs-config
```

and enable write support for, say, internal drives (or both).

I never found I needed to do this though to get NTFS support... but heck, it may help

---

### Post by abhinav.p on 2009-01-02
yes i checked the option write enable to both the devices.but the problem is i cannot find the device other than the c: drive where hardy was installed using Wubi.wheres the other part of the drive?

---

