---
title: "hard drive not recognised"
date: 2014-10-13
forum: Hardware
---

### Post by jak_amneziak on 2014-10-13
Good evening. 

I am running linux ubuntu 10.4 (most recent one) and have found something amiss.

Upon accessing the computer menu I find onky one hard drive avaialbae with 500GB (this size is correct for the drive). I do however have another 2TB drive which for some reason does not shwo up on the computer files menu. Is there a way of getting ubuntu to recognise the 2TB drive?

---

### Post by yancek on 2014-10-13
> I am running linux ubuntu 10.4 (most recent one) and have found something amiss.

Is that a typo?  The most recent one should be 14.04.  Look under the /media/username directory and you should see each partition for an external drive available with a uuid which is a combination of numbers/letter, very long.  That's if you are actually using 14.04.

---

### Post by jak_amneziak on 2014-10-14
yancek - it is a typo, I apologise. 14.04 is the version I am using. where would I find the media/username directory? (I am new to Linux so please bear with me)

---

### Post by yancek on 2014-10-14
The /media directory is in the root of the filesystem so using a terminal:  ls /media  should show the contents.  Alternatively, use the file manager, the file cabinet icon on the left panel and use the up/back arrows to navigate to the /media directory.

---

### Post by jak_amneziak on 2014-10-17
good morning. I have been away for a couple of days on work duty. Having checked the file system, it only shows one 500GB hard drive. All connections in the computer are correct (and presumed to be working). Any ideas why the 2TB slave drive is not showing up?

---

### Post by Bucky Ball on 2014-10-17
It may be in the /mnt directory, but it should be in the left pane of the file manager if it is plugged in and switched on. Try:

```
dir /mnt
```

Is it there? You can also navigate to /mnt in the file manager.

You have a 2Tb external drive that is not showing up if I'm reading this correctly. How is it plugged in? USB, SATA, Firewire, or something else?

---

### Post by jak_amneziak on 2014-10-17
The 2TB hard drive is an internal drive with SATA 3 connection. 

mnt file is empty. 

Dir/mnt (I assume that is to be put into terminal as a commadn prompt) has come up with nothing. This is not as easy as first thought.

---

### Post by Bucky Ball on 2014-10-17
This:

```
Dir/mnt
```

Will not show anything. It is:

```

dir /mnt
```

... in a terminal, exactly as it is above. 

But before any of that, open Gparted and see if it appears in there. Depending on how many drives you have in the box (and out of it) it will be sda, sdb,sdc, etc. Check in the drop down list in the top right corner of Gparted. If it appears there, take note of what sd* it is. If there are no partitions on it, create some by right clicking on the drive. 

It should just be a matter of mounting the partitions. We can do that manually, if it works, we can make that permanent mounting at boot. ;)

---

