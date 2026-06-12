---
title: "Upgrading to 9.04, need help transfering 'Home'"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Admiral Yi on 2009-09-12
Hello,
I would like to upgrade from 8.10 to 9.04. I would like to wipe my root partition and start over, but I would like to keep home. The main issue here is: I don't have a home partition. I know its stupid, but when I first set up my system I really didn't know what I was doing (I used ext2 when I should have used ext4...). 

So basically, what I need to know is:
1) How can I copy my home to a new install (the new install will have a partition for home on it)?
2) Will this keep my stuff (desktop layout, files, saved settings, etc)?

---

### Post by Partyboi2 on 2009-09-12
> 1) How can I copy my home to a new install (the new install will have a partition for home on it)?You can move your /home folder to its own partition by following the link below
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
>  2) Will this keep my stuff (desktop layout, files, saved settings, etc)?     It will keep everything that is currently in your /home folder eg. videos, photos, data, user settings etc.

---

### Post by Bartender on 2009-09-12
Partyboi's recommendation makes sense to me.  Create the /home partition now, then reinstall.
When you have the Ubuntu LiveCD spinning and are ready to reinstall, I think you'll have to go to Manual (Advanced) option in step 5.  Click on the existing / partition, tell partitioner to use the partition, set the file system as ext3 or 4, mount it as /, and make sure to tell it to format.
JUST AS IMPORTANT, click on your new /home partition, and make sure that you tell the installer NOT to format.  Apparently you can make / ext4, and /home ext3, so don't fret too much about whether they're the same file structure or not.

Also, use the same username that you're using now, or the installer will create a second /home partition inside the / partition.

Or, if you have the hardware to do so, you could just back up your /home partition data, install Ubuntu however you want, and copy the data back to the /home partition.  I'm sure there are ways to *apply* all the settings in the backed up data, but I don't know how.  For a basic Linux user like myself, I'm thinking more along the lines of you'd have to configure your settings and themes and such by hand, but you could copy your .jpg's and .odt's and music files and etc. right back into their respective places in the new /home folder.

---

### Post by Admiral Yi on 2009-09-13
Thanks for that guide, it looks fairly easy and seems to do what I want. Ill probably try it out on a VM first though, just to be safe.

---

### Post by Admiral Yi on 2009-09-14
Another quick question: 

I'm currently running a 32 bit OS. I want to use a 64 Bit (my computer can support it). If I install 64 bit Ubuntu 9.04, will it still work with the new /home?

---

