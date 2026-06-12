---
title: "Not enough space to update?"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by ddalley on 2009-10-26
I've done my limited best to figure this problem out, but I'm stuck.

I've got a USB stick with just over 400Mb free and there are four kernal related files that won't update because the update manager thinks there isn't enough room free. These files add up to a total of 25Mb, at most.

The manager wants a minimum of 203Mb free and I've deleted just about all I really want to to increase the amount of free space (there is already double that amount), but it is never enough.

How do I solve this dilemma?

---

### Post by arrange on 2009-10-26
Have you tried updating via the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)? You can [copy](https://help.ubuntu.com/community/UsingTheTerminal#Pasting%20in%20commands) these commands and see if the files update or not.```
sudo apt-get update
sudo apt-get upgrade
```

If it does not work, post any error messages that come up and the output of```
df -Th
```

---

### Post by ddalley on 2009-10-26
After trying the first two commands, it still was not complete:

"The following packages have been kept back:
  linux-generic linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."

Otherwise...

"$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext2    3.0G  2.7G  129M  96% /
tmpfs        tmpfs   1007M     0 1007M   0% /lib/init/rw
varrun       tmpfs   1007M  100K 1006M   1% /var/run
varlock      tmpfs   1007M     0 1007M   0% /var/lock
udev         tmpfs   1007M  168K 1006M   1% /dev
tmpfs        tmpfs   1007M  572K 1006M   1% /dev/shm
lrm          tmpfs   1007M  2.2M 1004M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb6     ext2    735M  294M  402M  43% /home
/dev/sda6     ext3    668G   30G  604G   5% /media/disk"

---

### Post by arrange on 2009-10-26
You can try to make some free space by cleaning the *apt* cache```
sudo apt-get clean
```You can also uninstall any old kernels if you have more than, say, two.

Then - if you need the new kernel - install it by running```
sudo apt-get dist-upgrade
```

---

### Post by nerdzero on 2009-10-26
Could you use a live CD to resize the /home and / partitions on your USB stick?  It looks like you have about 400MB free on /home but only 129MB on /

---

### Post by ddalley on 2009-10-26
Clean did the job. Thanks!

"You can also uninstall any old kernels if you have more than, say, two."

I'd love to do this, too, but the only instructions I've seen to do it didn't apply to Ubuntu and couldn't work.

---

### Post by ddalley on 2009-10-26
> **nerdzero said:**
> Could you use a live CD to resize the /home and / partitions on your USB stick?  It looks like you have about 400MB free on /home but only 129MB on /
Not having enough room to upgrade after waiting just *a bit* too long was what caused the problem in the first place.

When it is stated Linux can be installed on 1 or 2Gb USB sticks, they don't take installing programs into account. Even this 4Gb one is barebones and I am only using 8Gb sticks for new installs now, as a minimum install space.

I have never resized partitions before, but I guess I can figure out how. Thanks for the tip!

---

### Post by bumanie on 2009-10-26
> "You can also uninstall any old kernels if you have more than, say, two."

I'd love to do this, too, but the only instructions I've seen to do it didn't apply to Ubuntu and couldn't work. 

Easiest way to uninstall old kernels. Go to synaptic and type "linux-image" (without the quotes) in to search, right click the ones you want to remove and choose completely remove. Each one will save a little over 110mb of space. Then go to terminal and > sudo update-grub or if using grub 2 > sudo upgrade-grub2A good partitioning tool is gparted. > sudo apt-get install gparted then to start the gparted gui > sudo gpartedThe rest is fairly straight forward, however any partitions you want to alter must be unmounted.

---

