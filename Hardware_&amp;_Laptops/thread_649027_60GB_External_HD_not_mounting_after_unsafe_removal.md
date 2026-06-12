---
title: "60GB External HD not mounting after unsafe removal"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by tweezyturtle on 2007-12-24
Hey, I have a 60GB Western Digital external Hard Drive, and recently I unplugged it without un-mounting it (my fault) but now when I plug it into Ubuntu, it gives me a mount error:
[IMG]http://img139.imageshack.us/img139/6859/ubuntustudio64bittweezyts3.png[/IMG]
I tried reformatting the HD under Ubuntu (using GParted) and under Windows, but neither worked, I still get the same error... what can I do? I am still fairly new to Linux, but I have been using computers for awhile so... Oh, and my windows machine, and my iBook both recognize the drive without any problems... Please help me out, I really need to be able to use this drive on all my computers...

---

### Post by ijason on 2007-12-24
what's the error message you get?

---

### Post by ijason on 2007-12-24
it looks like it's still thinking that the device is mounted. unplug the drive and reboot your ubuntu machine and then open a terminal and  : 
> mount -l
(that's a lower-case L)

what hda/sda drives are listed?

---

### Post by taurus on 2007-12-24
> **ijason said:**
> it looks like it's still thinking that the device is mounted. unplug the drive and reboot your ubuntu machine and then open a terminal and  : 

(that's a lower-case L)

what hda/sda drives are listed?

From the screenshot, error message, it says /dev/sdd1.

---

### Post by taurus on 2007-12-24
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdd1
sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1 -o force
df -h
```

---

### Post by ijason on 2007-12-24
you'll need to chown the new directory to your user, as well as chmod it so that you will have access as a normal user :) but yes, i second taurus' suggestion.

---

