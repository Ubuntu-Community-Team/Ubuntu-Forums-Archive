---
title: "Broken Update Manager/Synatic Package Manager"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by ronparent on 2009-03-27
Just now downloaded latest updates. Now both the subject packages crash when I try to run them. I tried all the my limited usual terminal fixes with no results. I get the following results with sudo apt-get upgrade.

ron@ron-LR:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%

What now? Appreciate any enlightment.

---

### Post by bapoumba on 2009-03-27
Please try:
```
sudo dpkg --configure -a
```
and run the upgrade again.

If it does not work: [http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

---

### Post by Godly on 2009-03-27
I didn't see anything in the link provided.
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

---

### Post by bapoumba on 2009-03-27
> **Godly said:**
> I didn't see anything in the link provided.
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

Here: [http://ubuntuforums.org/showpost.php?p=110354&postcount=2](http://ubuntuforums.org/showpost.php?p=110354&postcount=2)
```
sudo rm /var/cache/apt/*.bin
```
but I am quite surprised this error is seen, unless there is some HD problem :/

---

### Post by ronparent on 2009-03-27
Great:popcorn:! Mark as solved.

sudo rm /var/cache/apt/*.bin did the job. Updaters work fine now. I'll have to add that to my many notes of fixes.

Many thanks. ron

---

### Post by bapoumba on 2009-03-27
Nice, happy to see it worked!

I have added a solved tag to the thread. Anyone can :)

---

