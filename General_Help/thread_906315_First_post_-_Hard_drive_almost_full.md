---
title: "First post - Hard drive almost full"
date: 2008-08-31
forum: General Help
---

### Post by fennosteve on 2008-08-31
Hi. This is my first post, I have just installed Ubuntu HH to check it out. I used Red Hat a few years ago, but I'm mostly new to Linux. I'm 2nd line IT support tech by day, supporting a corporate Windows network. 

I've installed Ubuntu in Vmware server, I chose a 3GB SCSI configuration, and now when I tried to install an ATI driver, it says I only have 50MB free. The only thing I have installed is the Ubuntu recommended updates, which was only 118MB IIRC. 

Another funny thing is that the Disk Usage Analyser says I have a 5.6GB hard drive, with 4.7GB  used.See atachment. Very confusing. any ideas about this discrepancy? Are there size limits on individual folders or administrative areas?

I can start over and choose a bigger partition, but I wouldn't have expected Ubuntu to fill up so quickly out of the box. Am I missing something?

Thanks
steve

---

### Post by pro003 on 2008-08-31
you can try to free some space by deleting var/cashe/apt/archives deb packages
or in terminal:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo localpurge
```

---

### Post by drs305 on 2008-08-31
If what pro003 doesn't work, I've written a tutorial about Trash taking up lots of space and how to find and remove it. The link is in my signature line.

Disk usage analyzer is often confusing, sometimes because it includes the 'g virtual file system - .gvfs. Also because the top level always shows 100% full. That's just how DUA displays things.

You can run this command to get a more accurate accounting of your partition space:
```
df -Th
```

---

