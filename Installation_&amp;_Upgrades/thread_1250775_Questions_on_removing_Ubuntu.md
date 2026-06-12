---
title: "Questions on removing Ubuntu"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by skytreader on 2009-08-26
Hello. I'm planning to dual-boot my laptop sometime soon (WinXP + Ubuntu). However, I am not entirely sure if I will be comfortable with Ubuntu. With this, before installing anything, I have looked over some of the threads (specifically this: [http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)) (and also this webpage: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)). Both sources speak of fixing the mbr by running the fixmbr command from my Windows Boot CD.

Fine with that. However, checking for my Windows CD, I found out that its underside (the one receving all the laser) is pretty fogged and I am not sure if it will still run well should I decide to fixmbr. So, my question is _will I still be able to run WindowsXP even if I have only removed Ubuntu and its partition but not GRUB? Will this affect Windows in any way (just in case I cannot run fixmbr due to the fogged CD)?_

(And some after thought:

Will partitioning slow down my computer? Isn't it that, to speed things up, CPU's use part of the hard drive's memory to temporarily store some data? I am having some doubts if partitioning will affect this process.

What is the ideal partition size for Ubuntu? I won't be using it much. Mostly only for experience and some beginner assembly programming [I find gcc -s pretty neat]. I am planning on giving Ubuntu around 20G and Windows will have something like 80G. [Just some info, out of my 100G, unpartitioned HD, I am using only around 15G].
)

Thanks a lot. :)

---

### Post by stlsaint on 2009-08-26
ok ill try and hit all of them as i know them...now you didnt explain what was the issue with your Grub but here it goes...
1. yes you will be able to boot into xp if you remove Grub...without Grub on MBR...MBR should look to the boot sector and all it should see is windows left...
2. im not 100% sure about the facts of a hdd on this topic but i dont think that it would slow down your drive by partitioning it...also 20 will be plenty if all your doing is testing...also i would recommend wubi if all your doing is testing...
hope i helped some...post if you need more!!

---

### Post by raymondh on 2009-08-26
> **skytreader said:**
> Hello. I'm planning to dual-boot my laptop sometime soon (WinXP + Ubuntu). However, I am not entirely sure if I will be comfortable with Ubuntu. With this, before installing anything, I have looked over some of the threads (specifically this: [http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)) (and also this webpage: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)). Both sources speak of fixing the mbr by running the fixmbr command from my Windows Boot CD.

Fine with that. However, checking for my Windows CD, I found out that its underside (the one receving all the laser) is pretty fogged and I am not sure if it will still run well should I decide to fixmbr. So, my question is _will I still be able to run WindowsXP even if I have only removed Ubuntu and its partition but not GRUB? Will this affect Windows in any way (just in case I cannot run fixmbr due to the fogged CD)?_

(And some after thought:

Will partitioning slow down my computer? Isn't it that, to speed things up, CPU's use part of the hard drive's memory to temporarily store some data? I am having some doubts if partitioning will affect this process.

What is the ideal partition size for Ubuntu? I won't be using it much. Mostly only for experience and some beginner assembly programming [I find gcc -s pretty neat]. I am planning on giving Ubuntu around 20G and Windows will have something like 80G. [Just some info, out of my 100G, unpartitioned HD, I am using only around 15G].
)

Thanks a lot. :)

If you're doubting the reliability/integrity of your current XP install disc, why not test it?  See if you can (at least) access a command prompt.

If you want to test ubuntu and have the ability to uninstall without the need to fixmbr or fixboot, you can try a WUBI installed ubuntu.  Thru wubi, ubuntu will reside inside windows hence removal is thru add/remove (just like any window app).  Note that should windows crash, ubuntu crashes as well.  Also, the performance of Ubuntu is degraded and is subject to the same issues as windows.

Personally, I prefer to install Ubuntu in it's own partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

EDIT:  There's also this CD [(Hiren's)]("http://www.hiren.info/pages/bootcd") for recovery tools, etc.

---

### Post by oboedad55 on 2009-08-27
> **raymondhenson said:**
> If you're doubting the reliability/integrity of your current XP install disc, why not test it?  See if you can (at least) access a command prompt.

If you want to test ubuntu and have the ability to uninstall without the need to fixmbr or fixboot, you can try a WUBI installed ubuntu.  Thru wubi, ubuntu will reside inside windows hence removal is thru add/remove (just like any window app).  Note that should windows crash, ubuntu crashes as well.  Also, the performance of Ubuntu is degraded and is subject to the same issues as windows.

Personally, I prefer to install Ubuntu in it's own partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

EDIT:  There's also this CD [(Hiren's)]("http://www.hiren.info/pages/bootcd") for recovery tools, etc.

I was able to make a copy of my Windows XP CD, so that's a possibility if your CD is still readable.

---

### Post by skytreader on 2009-08-27
> **stlsaint said:**
> ok ill try and hit all of them as i know them...now you didnt explain what was the issue with your Grub but here it goes...
1. yes you will be able to boot into xp if you remove Grub...without Grub on MBR...MBR should look to the boot sector and all it should see is windows left...
2. im not 100% sure about the facts of a hdd on this topic but i dont think that it would slow down your drive by partitioning it...also 20 will be plenty if all your doing is testing...also i would recommend wubi if all your doing is testing...
hope i helped some...post if you need more!!

Hey thanks. But I don't think we are quite settled with my GRUB issue. My apologies if the question sentence is so long that the GRUB issue has been overshadowed by length.

Let me rephrase my question...

In the event that I am _able to_ remove the Ubuntu installation, merge the partitions again, etc. but _not able_ to remove GRUB, will Windows XP still load?

Hey I know that's still pretty long but I hope it sounds better and is way clearer this time around.

@raymondhenson (and everyone else recommending WUBI):

Thanks but I've already considered that option. However, I haven't enough RAM to do that. Or, maybe I'll be able to but I won't be really able to test Ubuntu and I think a divided RAM is the last thing I need when doing assembly. Thanks for the suggestion anyway. :)

---

### Post by oldos2er on 2009-08-27
> **skytreader said:**
> In the event that I am _able to_ remove the Ubuntu installation, merge the partitions again, etc. but _not able_ to remove GRUB, will Windows XP still load?


 No. Grub is stored in two places in a default install; part of it is in the MBR, the MBR then looks to /boot for the rest of its configuration files. If you remove Ubuntu, you remove those files, ergo nothing will boot. The first thing you should do when restoring Windows and removing Ubuntu (in my opinion) is to restore Windows' MBR. Then you can boot Win* and safely remove Ubuntu from there.

 What is "divided RAM"?

---

### Post by skytreader on 2009-08-28
> **oldos2er said:**
> 
 What is "divided RAM"?

If I install Ubuntu via WUBI, my RAM will be divided right? Part of the RAM is minding XP, part of it is minding Ubuntu.

---

### Post by zvacet on 2009-08-28
Before you install it read [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe") I think it is better to install it on separate partition.
1. root  10GB                 mountpoint /        ext3
2.home   all free space except      mountpoint /home    ext3
3. swap 2GB

---

### Post by skytreader on 2009-08-28
Hey hey zvacet...looks like that's what I precisely need :). Great. Thanks a lot.

I now consider this thread close. Thank you everyone :)

---

