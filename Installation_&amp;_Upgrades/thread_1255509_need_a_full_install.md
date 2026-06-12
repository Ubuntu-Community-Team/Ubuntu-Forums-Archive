---
title: "need a full install"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by fletcher08 on 2009-09-01
I installed Ubuntu from Wubi the other day, to try it out. I love it! Ubuntu is much better than Windows. But now I want a full version, not the basically trial mode from Wubi. 

I have a couple questions about installing from a disk or a USB (which is what I plan to use). 

First, if I do an install of a full Ubuntu, will it be clear how to create a partition for Ubuntu (or will it just use the one Wubi created)?

If I install Ubuntu from the USB, will it integarte into the Wubi install and copy the files that are on my current Ubuntu? I don't want to lose the stuff I did before I found out that Wubi installs only a limited size Ubuntu. I moved some music, documents, and bookmarks over from WIndows, for instance. Do I need to move them back before I install Ubuntu or will they be safely copied?

I am not quite ready to get rid of Windows, although that is my goal. I want to make sure I get everything onto my new OS first, and get used to Ubuntu/Linux, be sure I know how to use it, etc.

Any help I could get would be greatly appreciated.

---

### Post by QIII on 2009-09-01
First --

BACK UP all the files you want to keep to some sort of removable media.  I believe getting rid of your Wubi install is much like uninstalling anything else from Windows... you'll lose anything in the folder.  Wubi doesn't create a partition, it just sets up a folder for Windows to use.

Back up BOTH your important Windows files and the files you have in your Wubi version.  Mistakes happen.

Again:  BACK UP!

Then, if you want to dual-boot, carefully follow the instructions here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by lackhand on 2009-09-01
Last I checked, the installer for Ubuntu can use an existing partition, but if you don't already have one on your hard drive, creating one is not a good idea.  You're very likely to mess up data that's already on there.  If you're not quite ready to give up Windows, you're probably better off with Wubi for now.  

You would need a new partition - it will not install into the same space currently being used for Wubi.  You would also need to transfer all your files back over, or put them on a USB drive or other storage device.

---

### Post by Mark Phelps on 2009-09-01
Two comments ...

First, if you're running Vista, use the Disk Management utility to shrink the Vista OS partition to make room for Ubuntu.  That may be hampered by the fact that you installed Wubi if you used the Vista partition for it.

Second, you can move the Wubi install to its own partition using the instuctions in the Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by fletcher08 on 2009-09-01
Thanks all for your help and advice. 

I went to [https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?) and got the program they recommended to move Wubi into its own partition and have a full Ubuntu OS. But I am unsure which partition to put it in. I am going to move all of my files over to Ubuntu, so the Vista will not take up a lot of space. But I don't want to move Ubuntu into the wrong partition.

The program tells me that my root is in one partition, so are all of the others safe? Or is there a chance that I will accidently overwrite my Windows?

Thanks for any and all advice.

---

### Post by earthpigg on 2009-09-01
> Or is there a chance that I will accidently overwrite my Windows?

yes, there is a chance you can make a typo or misread something and wipe windows. there is also a chance that family emergency or tornado or earthquake or power outage or cat-jumping-on-the-keyboard will occur during this procedure and mess things up.

fortunately, you have a good backup, right? ergo, nothing to worry about. :D

the easiest way to keep track of partitions when moving between windows and linux is to just look at the partition sizes and ignore the c:\ and /dev/sda1 stuff. you created the partitions, so that makes it easy to keep track. that should prevent you from picking the wrong one when it comes time to choose.

this command may help you out by showing you the partitions, and what ubuntu is calling them:

> df -Th -x tmpfs

:)

---

### Post by fletcher08 on 2009-09-03
I find that partition sda5 is the static data portion, with only 300 or so megs. All that is on there is recycle bin, so that seems a good place to move my Ubuntu install.

Am I right? Or am I missing something or just being naive?

---

