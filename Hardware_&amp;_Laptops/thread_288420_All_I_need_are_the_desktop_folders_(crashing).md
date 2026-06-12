---
title: "All I need are the desktop folders (crashing)"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by kmull on 2006-10-29
Last night I did apt-get update/upgrade/dist-upgrade/dist-update and thought I was getting edgy.

Everything was cruising along fine, until I restarted my laptop today. Now it says X isn't loading correctly and send me to a text login. I don't care about the rest of the data on the computer, I have no problem downloading Edgy onto a CD and reloading (in fact, I've wasted 2 CDs burning a bad ISO to do just that).

However, I REALLY would like to get the folders that are on the Desktop. One is called "Engagement Photos" and the other is "Flash backup".

Is there anyway I can navigate via the command line to copy these folders from the desktop to my USB thumb drive?

Or, if I put a Live CD in, can I access them that way somehow?

Please help! About to hit the road for a week on business...

---

### Post by kmull on 2006-10-29
Anyone? I really need to get these folders off. I can navigate in the restore option, but I can't seem to copy the directory to my USB drive.

---

### Post by kmull on 2006-11-06
So much for forum help... :(

I was able to get some of the files off using:
sudo mount /dev/sda1 /mnt/tmp
cp -R /home /mnt/tmp
sudo umount /mnt/tmp (or /dev/sda1, can't remember)

however, I then ran into the issue of not having a large enough USB drive to fit the whole folder. I'm having to go through and file by file remove each file (rm x.doc). Is there an easier way to do this? I also couldn't get sudo to accept my password tonight... no idea why?

If I install Ubuntu over this current installation, is there any way that my desktop folders or home folders would be saved?

Thanks...

---

