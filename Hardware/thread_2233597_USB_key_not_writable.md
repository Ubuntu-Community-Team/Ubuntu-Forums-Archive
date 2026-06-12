---
title: "USB key not writable"
date: 2014-07-09
forum: Hardware
---

### Post by pierpiotr on 2014-07-09
Hello,
I extracted a USB key out of the computer befor unlmounting it. Now I cannot open the files in the directory I was working on and their names are distorted (no big deal there). The worse is that I cannot use my key to save anymore things on it.
I tried to repartition the stick with the partition manager but it fails.
Maybe if I could chmod it... But I'm kind of a noob.
Here is what it looks like in Dolphin.
[[IMG]http://img11.hostingpics.net/pics/927900USBkRights.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=927900USBkRights.jpg")

---

### Post by sudodus on 2014-07-09
Welcome to the Ubuntu Forums :-)

A. Try to use ***gparted*** to remove the bad partition and create a new partition on the pendrive.

```
sudo apt-get install gparted
```
```
sudo -H gparted
```

If that does not work

B1. Wipe the first megabyte to remove any traces that might create problems using ***mkusb*** according to this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

B2. Try to use ***gparted*** to create a new partition table and a new partiiton on the pendrive.

---

### Post by pierpiotr on 2014-11-11
Hello sudodus,
Maybe I cannot use gparted but here is what I get, which means that one cannot write on the pendrive since it is pen as read only, even when I try to create an extended partition ont the blank partition (non allouée = non-allocated ?).
Also, mkusb failed.
BTW, thank you for your help and I apologize for taking up on the matter so late after your answer. I did not find time before.
[IMG]http://www.pix-host.com/allimages/43717543.jpeg[/IMG]

---

### Post by sudodus on 2014-11-11
There could be more than one reason why it does not work.

1. The pendrive is damanged or failing. Pendrives often start failing by being read-only. The next step is that you cannot read from it, so cannot use it at all.

2. The pendrive is mounted (or more accurately some partition is mounted).

My French is not very good, but it seems that you [try to] create a primary partition, but writing is not allowed. If none of these programs are allowed to write I'm afraid the pendrive is damaged.

-o-

Sometimes pendrives work better with some motherboards and operating systems, and worse with others. It is worth trying in another computer, in different USB ports and with another operating system (Windows or MacOS). I have even found pendrives that work from a USB hub, but not when connected directly into the computer's USB port.

---

### Post by pierpiotr on 2014-11-12
Acording to what you say, I think my pendrive is dead.
We also tried on a windows PC with advanced recovery software, to no avail.
Thank you for your help in any case.
The thread is kinda "solved" albeit in a non satisfactory way...

---

### Post by sudodus on 2014-11-12
I'm sorry, but I have to agree, this thread is kinda "solved" albeit in a non satisfactory way.

I wish you better luck with the next problem you try to solve here at the Ubuntu Forums.

---

