---
title: "Moving to new pc"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by AceMilo on 2009-04-21
About 4 months ago I switched to ubuntu full time off windows and love it.  I am now thinking of building a new pc and want to move my installation to it.  I have spent a lot of time installing apps and getting everything just the way I like it and would rather not go through it again if I don't have to.  I know how to clone the partition, which I have done for backup, but I don't want to move this installation so much as just have all my settings and programs and everything copy over.  I backup my home dir every night via rsync to a freenas box, so that is always backed up, and I've heard that just copying that back over to the new install will do some of it but I don't know how much.  So, basically I just need to know how to get my new machine to match my current install.

TIA, you guys rock

---

### Post by darthv3gan on 2009-04-21
You could try using Remastersys. I think that's what you're looking for. Here's a tutorial. :popcorn:

[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22#more-1686](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22#more-1686)

---

### Post by BkkBonanza on 2009-04-21
I think the easy way is to just copy the partition.

But if you want to try the long way and get a fresh install then I guess you could make a list of packages. There's probably a nice automated way to create a package manifest. I think this will work,

sudo dpkg-query -W --showformat='${Package}\n' > manifest

You could then run a small script to read the manifest and install them all. Or just browse it by eye and make sure you got what you wanted.

Something like, 
[B]#!/bin/bash
while read pkg
do
  apt-get --dry-run install $pkg
done < manifest[/B]
(note, remove --dry-run if it appears to work - I just wrote this and didn't test it)

After installing all packages you could copy over your home directory and see if it all plays nice together. I think it should but it wouldn't surprise me if some things act up. For example, firefox and thunderbird will create new user directories that have coded names and you would have to swap in the content underneath for them to work.

Edit - just saw the post about remastersys while I wrote this - that looks cool and easy too.

---

### Post by KyleBrandt on 2009-04-22
For copying user settings, rsync -av /home/myuser/ newpc:/home/myuser/ has always worked fine for me (even if the versions are different. Just make sure the users have the same uid.

-Kyle

---

### Post by mbonig on 2009-05-21
This remastersys tool seems to be just for backing up an existing system and restoring that to the same hardware.

I have the same problem as the original poster. I have setup a Ubuntu server machine and all is running very well on it. However, I need to repurpose the hardware. The new machine I'm moving too has some different hardware on it (different intel processor, different mobo and video card).  So, is this even wise? If I do move it over (image the hard drive and restore it to the new one) is it even likely to boot considering some significant hardware differences? 

Thanks

---

### Post by KyleBrandt on 2009-05-21
I don't think you will run into any problems with the CPU / MotherBoard / Processor that you would not also happen with a fresh install.  I am not sure if it will boot when you image the disk to a different drive ( assuming it is not the same model), but You can probably get around this just by using restore mode to repair grub.

I have never tried this method, because you can just copy over all the files ...

This might be helpful: [http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/](http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/)

---

