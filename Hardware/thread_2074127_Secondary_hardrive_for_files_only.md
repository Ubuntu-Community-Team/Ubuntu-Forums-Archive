---
title: "Secondary hardrive for files only"
date: 2012-10-21
forum: Hardware
---

### Post by xtiano77 on 2012-10-21
System:

Intel quad core: 2.4 GHz
4GB RAM
60GB SSD drive
500GB Mechanical drive

I am trying to configure the 500GB drive to store files only. I want to map that drive to /home. Right now the partition point of that drive is "sdb1" and the mounting point is /media/administrator/3f4b7182-e65c-4179-9309-bc12c9f4fcd5. I used to have Kubuntu installed in this machine and so I tried the same settings from Kubuntu and it didn't work. Can someone shed some light on how to do this? Thanks in advance.

---

### Post by varunendra on 2012-10-21
The best place for you : **[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")** *by bodhi.zazen*

In short, create a folder named "Data" (or whatever name you like) in your home for mount-point, then add a suitable entry in fstab, preferably based on the UUID of your target partition.

If you need specific help, please post output of:
```
sudo blkid
```

---

### Post by xtiano77 on 2012-10-21
[FONT="Arial"]&#65279;varunendra,

Thanks for your reply. I did read most of the information on the links you provided and after trying for hours and getting many error messages I finally figured it out. The &#8220;/etc/fstab&#8221; line was not that much different from the one I used in Kubuntu, it just needed an extra &#8220;/&#8221;. I did use the UUID instead of the old path, for example:

Kubuntu
/dev/sdb1 /home ext4 defaults 0 0

Xubuntu
UUID=9c224c52-9f24-4fee-89cb-26cf8596d76a /home/ ext4 defaults 0 0

Again, thanks for your help.[/FONT]

---

### Post by oldfred on 2012-10-21
Now that you have it mounted you need to link or bind folders from that partition back into /home.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

