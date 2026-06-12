---
title: "Booting Multiple Ubuntu Versions"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by Didius Falco on 2009-04-13
I currently run Ubuntu Intrepid 8.10, dual booting with Win XP.

I did have the Jaunty beta running, but I managed to screw it up so completely that I decided to delete all my Ubuntu partitions and start from scratch. It's also a good way for me to learn - setting things up multiple times "burns" the information into my brain better. I went back to Intrepid because the 9.04 Final release is so close, it seemed kind of dumb (and wasteful of my broadband download limits) to spend all that time and bandwidth re-downloading all the updates. 

I would like to add 2 other versions of Ubuntu when Jaunty comes out on the 23rd of this month - both the Jaunty 32 and 64 bit versions.

My partitions are set up as follows:

1 Swap partition
1 /Home partition
1 / partition

I have plenty of room left to make new partitions. Preferably, I'd like to have a separate /Home partition for each version, so when I settle on my final choice, it will make things easier.

Is this possible? If it is, how do I set it up so that each version doesn't overwrite the other versions /Home partition?

If it isn't possible, how do I correct the situation?

Any help would be highly appreciated.

---

### Post by inobe on 2009-04-14
very possible, here' this is how it's done, it has nice pictures too .

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by tommcd on 2009-04-14
You can also make a separate /data partition for your personal files. You can share this partition with any linux distros you have on your system.
With a separate /data partition, each distro's /home partition is contained within the root partition for that distro. This allows you to use the same user name and password for each distro without any conflicts. And all your data is contained in 1 partition for simplicity. 
I boot multiple linux distros on my system and this is how I do it. You can call /data what ever you want.    
Just mount it on a separate partition.

---

### Post by Didius Falco on 2009-04-14
Thank you both for the help. I just suggested that psychocats site for another user with a question not 4 hours ago. I told him how it was a virtual treasure trove of useful information. 

I guess I should have spent more time looking at it myself... 

Thanks, inobe and [tommcd]("http://ubuntuforums.org/member.php?u=34402")

---

### Post by night_fox on 2009-04-14
A word of warning: When I tried this a year ago, I installed PCLinuxOS and Ubuntu in I cant remember which order. The second one I installed changed all my device UUIDs.

So when you install $DISTRO1 then $DISTRO2, you need to change the /etc/fstab in $DISTRO1.

Boot into $DISTRO2
go to the $DISTRO1 root partition in the terminal
```
ls dev/disk/by-uuid
sudo gedit etc/fstab # and change the UUIDs $DISTRO1 should recognise them by.
```

---

