---
title: "Newbie intallation question"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by mattypants on 2009-09-21
I have an older dell laptop which I think got a virus and now all I am getting when I try to boot is a blue screen. I only use this laptop for browsing and think it is the perfect opp to get working with ubuntu. Here is my questions>

Will the intallation wipe out the old windows operating system and start me with a clean slate?

What should I watch out for?

---

### Post by FlyingBuzz on 2009-09-21
During the installation (from CD or Flash-drive) you will be able to edit your hard disk partitions. So, there're two ways for you:
1) Completely remove all windows partitions and get only Ubuntu cleanly installed.
For example:
[_ mountpoint: / _][_ mountpoint: /home _][ ....
2) Leave windows partitions as is and then be able to read neccessary files from them (if any).
Example [_ Windows C: drive _][_ Windows D: drive _][_ mountpoint: / _][ ....

---

### Post by blackmail on 2009-09-21
If you still have not made the transition to Ubuntu, please consider downloading and installing Partition Magic 8, and partition your drives to ext3, it should be able to make this whitout deleting your files, don't know how i did it but i did it once, and then if you want to you can just format your partition on which windows resided, and install an ubuntu, and make a little swap also from it, 10 GB should be enough for you ubuntu installation, even if you are a kind of power user.

---

### Post by Bucky Ball on 2009-09-21
Welcome. You might like to check the HOWTO out my [NEVER TRIED LINUX? ]("http://ubuntuforums.org/showthread.php?p=7922209#post7922209")HOWTO ... You will be able to find the info you are looking for or links to it. There are a number of ways you can use the Ubuntu partitioner during install.

Use whole disk automatically
Use uninterrupted free space automatically
Manually partition

And I think another option. If you manually partition (if you feel comfy but there's lot's of tutorials) you will see your windows partition. Just don't touch it. The Ubuntu install will pick up a Windows partition and perhaps fix the boot when it installs the Grub boot menu. Probably just your MBR which can be fixed with 'Repair' if you have a windows install disk by running these commands:

chkdisk
fixboot
fixmbr

If it is your boot sector that should fix it.

---

### Post by jerrrys on 2009-09-21
here's a step by step

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by chrisinspace on 2009-09-21
The Ubuntu installer has all of the partitioning tools you need to set your computer up in a single- or dual-boot configuration.  If you don't need to recover anything from your Windows installation, I'd say just delete the partition and give all of the space to Ubuntu.  You can have the installer automatically create the appropriate partitions for you.  If you want to try to salvage any of your old files, then you should probably preserve your old partition and let Ubuntu use your available space.

---

### Post by raymondh on 2009-09-21
and before you install ... do try a live session from the liveCD (try Ubuntu without any changes).  That'll give you an indicator of things to come; how your system reacts to ubuntu's requirements, etc.

I say this because you mentioned "an older" laptop.  Here are the [minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").  Note that in the minimum RAM requirement, some of it will be used by the graphic card.  The more, the better.

Good luck and welcome to ubuntu.

---

