---
title: "&quot;clean install?&quot;"
date: 2008-10-29
forum: General Help
---

### Post by Jim Lewis on 2008-10-29
I just re-installed a Ubuntu-only setup from a dual-boot system.  I had a Feisty Fawn disk, so that's what I'm using.  I see that FF is no longer being supported, and that I should do a "clean install" to version 8.x.

Does "clean install" mean what I think it does -- that I'll have to reinstall Thunderbird, and save and reinstall all of my documents, etc.?  I just went though all of that and the idea doesn't thrill me. 

Pls advise.  And TNX.

---

### Post by tuxxy on 2008-10-29
Move your /home dir over to a seperate partition first, which save all your personal documents/settings.

Now fresh install Hardy or Ibex ;) and make sure you dont install to the /home partition.

This will now prevent you needing to install thunderbird, save documents etc

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Jim Lewis on 2008-10-29
Thanks.  That's a bit more "computerish" than I'd hoped for.  When I installed FF did  the install make more than one partition, or do I have to make one myself, somehow?

I'd hoped there was an install system a bit more similar to Windows Update, but . . . . I guess not.  

Thanks again.

---

### Post by ajgreeny on 2008-10-29
Before you go ahead, unless I'm already too late, let's see the output of ```
sudo fdisk -l
``` which will show if you have a separate /home partition.  If you do have this, it will be easy to reinstall.

---

### Post by Jim Lewis on 2008-10-29
I get:

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23991   192707676   83  Linux
/dev/hda2           23992       24321     2650725    5  Extended
/dev/hda5           23992   


and have NO idea what it means.  :)

---

### Post by ajgreeny on 2008-10-29
> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23991   192707676   83  Linux
/dev/hda2           23992       24321     2650725    5  Extended
/dev/hda5           23992   The first paragraph just shows the disk properties, size, sectors etc etc.
The second paragraph is the interesting one to see what you have installed.  It lloks as if you do not have a separate /home partition, but just two partitions, hda1 which is the root partition, containing the OS and your user files in the /home/username folder.  hda2 is an extended partition which contains hda5, your swap (like a windows page file or virtual memory, as it is called there)  If you look at the start and end points for hda2 and hda5 you will see they are identical.

What this means for you is probably to follow tuxxy's advice and then you will have a separate /home partition, ready for the next time you need to install.  Just make sure you don't install to the partition where you put your files, and also make sure the format button is not checked for that partition when you get to the partitioning stage of installing.

---

### Post by bryonak on 2008-10-29
In this case, it either gets "computerish" or clean install ;)

You can download the [GPartEd liveCD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"), which is, as most people find, surprisingly easy to use.
Boot it and shrink your system partition down to something around 6-10GB (that will take some time), reformat the rest to ext3, then you're done with partitioning.
Now back in Ubuntu, just copy your whole home folder (the folder named after your username itself) to the other partition, so it won't be changed when you clean-install a new OS... which will let you keep all your user settings, since they are stored there.

If you install Ubuntu 8.10 from scratch, you have to select the manual partitioning option when it asks you what partition layout to use. There you can specify the system partition (that one with 6-10GB) to be formated and mounted as root (/) and your other one to be mounted as /home, without checking the format box for the latter.
It's actually even easier than it sounds ;D

---

