---
title: "Compaq Recovery CDs"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by nmaster on 2009-06-07
Hi all.  I am very new to ubuntu (I still use wubi), but am thinking about switching from Vista.  

If I completely remove Vista, will the recovery cds I made still work?  If at some point in the future, I want to return my laptop to its original factory settings (like if I were selling it), would I be able to?  I'm not sure how recovery cds work and I've never had to use them before. 

Thanks!

---

### Post by presence1960 on 2009-06-07
yes they will work because they are bootable. But I would not trust my OS to CDs/DVDs. I would **_also_** make a backup of the recovery partition to a usb drive. If you ever want to recover Vista you can try the CDs/DVDs or you can always create a partition with the Live CD and put the recovery partition data on it. Then all you need to do is add an entry in menu.lst for the recovery partition just like you would for Windows. Reboot & choose that menu entry and your recovery process will begin.

---

### Post by nmaster on 2009-06-07
That sounds like a really good idea.  Thanks, I appreciate the help.

---

### Post by nmaster on 2009-06-07
Do you know where I could find more information (perhaps a guide) on how to create that partition and entry to menu.lst?

---

### Post by presence1960 on 2009-06-07
> **neal.m.master said:**
> That sounds like a really good idea.  Thanks, I appreciate the help.

You should still have the recovery partition on your hard disk unless you already deleted it. If so you are in good shape. I would back it up first to a usb drive. Then boot the Live Ubuntu CD. When the menu comes up first choose "Check CD for defects". If that goes ok then choose "Install Ubuntu". When you get to the partitioner screen titled Prepare disk space choose the manual option. You want to install Ubuntu to your Vista partition. Be careful to not choose the recovery partition. It will be easy to tell because there will be such a huge difference in size. The Vista partition is many times larger than the recovery partition. If you want to wipe Vista this will do it & you will have your recovery partition intact (and backed up) and Ubuntu installed. When GRUB installs during the installation it should detect your recovery patition and have an entry in menu.lst. If it doesn't just post back here that is such an easy fix.

If you want to dual boot Vista & Ubuntu then you need different instructions. I would recommend a dual boot for the simple fact that Linux  is not Windows. There will be a steep learning curve. How fast you learn is up to you. Until you feel you have mastered Ubuntu sufficiently to be confident you can ditch Windows it is nice to have a safety net to fall back onto when you get in a jam.

---

### Post by nmaster on 2009-06-07
Yeah I agree with your suggestions about dual-booting.  That's why I'm going to stick with wubi for a while; it allows me to dual boot without having to go through the steps of setting up partitions and I can easily uninstall it.  I think that at the end of the summer I'll be ready to use Jaunty fully.  Thanks for the help.

---

### Post by presence1960 on 2009-06-07
sounds like a plan. here is some reading to do so you will have a jump on things when you are ready.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Download in pdf format this Ubuntu guide : [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

It is best to be well informed and sure of what you are going to do if you are going to put Ubuntu on a partition. This will be a very good start by reading these.

---

### Post by nmaster on 2009-06-08
Thanks for the links.  I like to read up on this kind of stuff.  Are these sites any good? They were the first ones that I looked at, but it would be good to have your input on their quality.

[http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by presence1960 on 2009-06-08
> **neal.m.master said:**
> Thanks for the links.  I like to read up on this kind of stuff.  Are these sites any good? They were the first ones that I looked at, but it would be good to have your input on their quality.

[http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

psychocats.net is an excellent source of info. Although I do sometimes use web pages other than from the Ubuntu community, I try to mostly stick with that. I know nothing about tomshardware site.

---

