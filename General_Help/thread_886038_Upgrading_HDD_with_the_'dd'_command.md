---
title: "Upgrading HDD with the 'dd' command"
date: 2008-08-10
forum: General Help
---

### Post by otheracco on 2008-08-10
Hello and thanks for looking.
I'm trying to upgrade a HDD in a PPC mac and am having a difficult time.
**NOTE: THIS IS ALL DONE ON AN HFS+ FILESYSTEM**

Here's where I am.
I created an image of the 40GB mac install using this command;
'sudo dd if=/dev/hda of=/mnt/sda1/images/mac.img bs=64k'
(note that /dev/hda is the old 40GB hdd)
This created the image.  

I then copied the image onto the new 250GB hard drive with the following command;
'sudo dd if=/mnt/sda1/images/mac.img of=/dev/hda bs=64k'
(note that /dev/hda is now the new 250GB hard drive)

I then installed the new 250GB drive into the mac, hit the power button, and everything is exactly as it was (except it's a lot faster with the new HDD)

The only problem is that when I used the 'dd' commands above, the image only used 40GB of space on new 250GB hard drive (because it's an exact copy), but I want it to use the whole 250GB in one partition.

So then I spent hours trying to get 'parted' to resize it, but it doesn't appear to support PPC HFS+.
I've also tried the OSX 'diskutil resize' command, it also doesn't work.

Is there a way that I can use the 'dd' command to make a 40GB HFS+ image expand onto a 250GB hard drive?

---

