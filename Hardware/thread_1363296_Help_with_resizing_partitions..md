---
title: "Help with resizing partitions."
date: 2009-12-24
forum: Hardware
---

### Post by HarrisonVR on 2009-12-24
I have downloaded Gparted and tried following a tutorial, but it is not at all like mine is.
The link to the tutorial is here:
**[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)**

The tutorial says that the main drive should be called /dev/hda1, but mine is called /dev/sda2 and /dev/sda1/ and whenever I click on them and try to go to Partition/Move, the button is grayed out and won't work. Here is the link to what my Gparted screen looks like:
**[http://img687.imageshack.us/img687/9198/gpartedhelp.png](http://img687.imageshack.us/img687/9198/gpartedhelp.png)**

If anybody could give me a step by step guide of how to modify my partitions despite the differences to the tutorial, or how to sort my Gparted out so that is is like the tutorial linked above.

Thanks, all help much appreciated.
Harrison.

---

### Post by Grenage on 2009-12-24
Hi there,

hda/sda is merely IDE/SATA|SCSI, so it's just down to the type of drive you have.  You cannot change mounted partitions, so it's generally easiest to boot using a live CD, and run gparted there.

---

### Post by coffeecat on 2009-12-24
@HarrisonVR. First thing is that tutorial is ancient. Yes! Three years ago is ancient history in the Linux world. :p Back in the dim and distant past of 2006, there were separate kernel drivers for ide drives and SATA drives. Ide drives were designated hdx, SATA (and SCSI) sdx. But a newer combined driver was incorporated in the kernel from about 2007 - possibly as far back as 2006 - and IDE, SATA and SCSI drives are all now sdx.

Second thing. MUCH MORE IMPORTANT. You are running Ubuntu in Wubi. The giveaway is the mountpoint = /host in your screenshot. You cannot resize sda2 from within your Wubi-ised Ubuntu, because Ubuntu is running from inside sda2 and has mounted sda2 in /host.

By the way, I'd advise not touching sda1. That looks like some sort of recovery partition.

As the previous poster said, you could resize sda2 from the live CD, but I'd hold back from doing that as well if your version of Windows is Vista or W7. Vista has sometimes been rendered unbootable by resizing the C:\ partition with Gparted. I'll give you more details if you have Vista.

And if you do have Vista (or W7) you could use the resize utility in that to shrink sda2 (C:\).

Why do you want to shrink the partition? What partitions do you want to create?

---

### Post by HarrisonVR on 2009-12-24
Hi CoffeeCat,

First I'd just like to thank you. Your answer was informative and helpful, and can now see what was going wrong. However, there is some more help I would like if you can offer it.

How can I uninstall Ubuntu and then install it without Wubi. I didn't realise that using Wubi was an issue, I just thought it was an install helper.

I am looking to increase my Ubuntu partition because I would like to download and install Steam and my Steam games onto Ubuntu, so that I do not have to switch over to Vista everytime I want to play a game for 5 minutes.

And yes I am using 32-bit Vista.
Can you offer any help?

Thanks
Harrison

---

### Post by HarrisonVR on 2009-12-24
Hi CoffeeCat,

First I'd just like to thank you. Your answer was informative and helpful, and can now see what was going wrong. However, there is some more help I would like if you can offer it.

How can I uninstall Ubuntu and then install it without Wubi. I didn't realise that using Wubi was an issue, I just thought it was an install helper.

I am looking to increase my Ubuntu partition because I would like to download and install Steam and my Steam games onto Ubuntu, so that I do not have to switch over to Vista everytime I want to play a game for 5 minutes.

And yes I am using 32-bit Vista.
Can you offer any help?

Thanks
Harrison

---

### Post by coffeecat on 2009-12-24
You can uninstall a Wubi-ised Ubuntu from the control panel in Vista. Have a look at this link. Scroll down a bit:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Next - be aware that if you set up a conventional dual-boot Vista/Ubuntu, then the Windows mbr will be overwritten by grub stage 1. If you ever decide to abandon Ubuntu and go back to Vista only, then you need to repair the Windows mbr before you delete the Ubuntu partitions, otherwise you'll make Vista unbootable. There are easy ways of doing this. We can come back to that later if you want.

The next thing is that you need to shrink your Vista C: partition to make room for the Ubuntu partitions. The Ubuntu partitioner (Gparted) is quite capable of doing this, and is safe with XP, but there are reports of Vista being made unbootable after a Gparted resize. This is recoverable, but you need a genuine Microsoft Vista DVD with a repair utility for this. Here's an informative link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

If you can shrink the Vista C: partition sufficiently with the Vista utility, all well and good. But if you ever do manage to make Vista unbootable with Gparted and you don't have a Vista DVD, then look here:

[http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/](http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/)

Having said that, I've seen comments that you can avoid this Vista damage business by unticking the 'round to cylinders' box in the Gparted resize utility, but I have no experience of this so I can't advise.

Once you've shrunk your Vista partition with the Vista utility, boot up with the live CD, start the installer from the desktop and, when you get to the partitioning stage, choose the 'guided' option that says something like, "use continuous free space".

Do post back if you need any more information.

**Edit:** re-read your post and saw that you want more room for installing Steam. I believe the virtual partition for Wubi Ubuntu is set at install time - although I could be wrong. Perhaps someone could correct or confirm this point. But another alternative (if I'm right) is to uninstall the Wubi Ubuntu and reinstall, but this time choose a larger installation size. Personally, I'd prefer a standard dual-boot because there are a number of disadvantages to Wubi, but if you want to stick with Wubi, this is a possibility.

---

### Post by bwinfrey on 2009-12-26
You can resize the "partition(s)" with a wubi install.  You can also move portions of the root filesystem to new "partition(s)". -- for instance you can create a seperate filesystem for the home folders. Check the links below.

[resize loop mounted partition]("http://mediakey.dk/~cc/howto-resize-xen-loop-disk-image/")

[wubi_add_virtual_disk]("https://wiki.ubuntu.com/WubiGuide")

---

