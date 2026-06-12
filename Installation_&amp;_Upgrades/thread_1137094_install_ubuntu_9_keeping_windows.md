---
title: "install ubuntu 9 keeping windows"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by registeredtwice4servererr on 2009-04-25
I don't know so much of how Linux works so I would like to keep running Windows Vista as well on my laptop computer.
When I am installing ubuntu 9 I can't find the way how to resize my actual partition and create a partiton for the operating system keeping an NTFS one for Windows.

I am looking for information on the support website, under documentation specific for V.9.04
[https://help.ubuntu.com/9.04/switching/dualboot-procedure.html](https://help.ubuntu.com/9.04/switching/dualboot-procedure.html)
the documentation seems to refer to anything but not what I can visualize on the screen
I don't have any "resize" option, I don't have any "new size" field....
plus I have a "mount" field which I really don't know what I should select through the various different options

---

### Post by ajgreeny on 2009-04-25
I was under the impression that Vista needs partition resizing from the windows disk management tools and not with the ubuntu gparted.  I may be wrong, but it will certainly not cause any problems if you do it the windows way.  I have not used Vista so can not tell you anything about how to do this part of the procedure I'm afraid.  Gparted was fine for XP (it's what I used to shrink mine) but for Vista, perhaps not.

After shrinking the windows partition, install Ubuntu.  Choose manual when you get to that part.  Choose the unallocated space on your disk, and install into a minimum of two new partitions that you make on that.  The first should be the root partition (/) and the second a small (1GB?) swap partition.  Give it a try but come back here if you are uncertain at any point.  You can do that whilst setting up the partitions, but before you actually commit to the hard disk, by using Firefox in the live CD.

It sounds complicated, but it is not really too much of a problem, and you should find it relatively easy to do.

---

### Post by registeredtwice4servererr on 2009-04-27
And your impression was correct. It was very simple to resize my partition via Windows and then during the instal Ubuntu detected without problems the available space. 
Thank you very much!

---

### Post by ajgreeny on 2009-04-27
My pleasure.  Enjoy!

---

