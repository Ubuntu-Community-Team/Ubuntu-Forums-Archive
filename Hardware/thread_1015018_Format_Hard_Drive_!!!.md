---
title: "Format Hard Drive !!!"
date: 2008-12-18
forum: Hardware
---

### Post by warzt on 2008-12-18
I decided reinstall Ubuntu. Before it, I want to format all my hard drive. I mean delete every thing, EVERY THING in hard drive ,then i will reinstall ubuntu. 
I did try gparted but I can't delete some file in /dev.

---

### Post by taurus on 2008-12-18
You have to use gparted from the LiveCD since you cannot delete partition(s) that you are using.

---

### Post by danielpalos on 2008-12-18
If you think you may be having hard drive issues, you may want to download the utility from the hard drive manufacturer.  You can probably also use the latest Maxtor utility since it works with many drives.

Hard drive issues can be reviewed from a "clean boot" that is OS independent.

---

### Post by mªrty on 2008-12-18
Taurus is right; boot to a livecd and then format the drive using Gparted.

---

### Post by vanadium on 2008-12-18
The easiest and most foolproof way is to launch the installation CD, start the Ubuntu installation program and have it use the entire disk.

---

### Post by SuperSonic4 on 2008-12-18
Depends what the OP wants, while that way is best for new users I find a separate /home is essential

---

### Post by warzt on 2008-12-18
> **mªrty said:**
> boot to a livecd and then format the drive using Gparted.
How can I boot it to a live cd :-/

---

### Post by xjcannonx on 2008-12-18
to boot from the live cd is easy, just download gparted live version and burn the iso to a disc(at slow speed) and restart your computer(you may need to hit one of the F keys or DEL or whatever so you can set your computer to boot from cd first...nice thing about gparted is that it doesnt even need an OS to work

---

### Post by warzt on 2008-12-18
hehe i got it thank you very much

---

### Post by vanadium on 2008-12-19
> Depends what the OP wants, while that way is best for new users I find a separate /home is essential
I don't. I find a very good backup of your user data on an external disk essential. From that, it is easy enough to reinstall a system from scratch and put the data back if the need arises.
_

---

