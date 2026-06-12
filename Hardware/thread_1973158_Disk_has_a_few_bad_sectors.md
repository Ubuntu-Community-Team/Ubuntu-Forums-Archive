---
title: "Disk has a few bad sectors"
date: 2012-05-04
forum: Hardware
---

### Post by JeremySchubert on 2012-05-04
Running 12.04 on a refurbished computer I purchased yesterday.  80 GB HD.
After a few reboots, I started getting the message about a sick hard drive.  Turns out it was the system hard drive.
Ran shutdown -rF now and then sudo touch /forcefsck.  
Now disk utility reports "Disk has a few bad sectors".
After clicking on 'view smart data', the two errors reported are:
1.  Read error rate
5.  Reallocated sector count

I'm assuming that this means my hard drive is dying and I should see if the store will swap out the hard drive for a new one (I have a 30 day warranty).  How can I print out the smart data report?

Thanks,
Jeremy

---

### Post by ahallubuntu on 2012-05-04
Install smartmontools and then from a terminal run:

```
sudo smartctl -a /dev/sda
```

assuming sda is your main 80GB drive.

That should show a bunch of S.M.A.R.T. status fields including read error rate and reallocated sector count.  Print out that list, circle those two and take it back.  Yes, definitely get a clean drive that doesn't have such errors.

FYI, you can dig up a handy little Linux distro called Parted Magic that you can use to check S.M.A.R.T. since it has smartmontools (and many other neat utilities) already installed.  Google for Parted Magic and download/burn that to a CD.  Then you can boot it in the store if they let you on your replacement hard drive and click "Smart Control" and make sure the drive is clean.  In the graphics version of Smart Control, make sure there are no Attributes highlighted in red.

---

### Post by JeremySchubert on 2012-05-04
Thank you, will do. 
What is the best way to erase my hard drive before taking it back?

---

### Post by mips on 2012-05-04
> **JeremySchubert said:**
> 
What is the best way to erase my hard drive before taking it back?

[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)
[http://www.ocztechnologyforum.com/forum/showthread.php?76612-Secure-Erase-From-Within-Linux-For-Windows-Users](http://www.ocztechnologyforum.com/forum/showthread.php?76612-Secure-Erase-From-Within-Linux-For-Windows-Users)

A ATA secure erase is the best and fastest option.

---

