---
title: "HD used space error between Analyzer, Properties, and partion size"
date: 2014-03-23
forum: Hardware
---

### Post by RCXtest on 2014-03-23
Disk Analyzer shows ~40gb in the file sytem, but reports 145.7gb used.

Gparted shows 148.29 of 162.47 used.

File Sytem Properties shows 128.0**_TB_** used with 6.0gb free !!!!

[ATTACH=CONFIG]251401[/ATTACH]

I had recovered data from a 320gb drive to my home dir. I then deleted  the data but I assume somehow it is still in the file table. There were ~1.4 million files recovered.

I know that the value of ~40gb was the correct amount of used space on that partion before the recovery.

Any idea how to fix this without reinstalling Ubuntu?

I did a forced file sytem check on reboot, did not help.

Thanks.

---

### Post by houstonbofh on 2014-03-23
Did you empty your trash?

If so, I suspect this may be your problem.
[http://stackoverflow.com/questions/653096/howto-free-inode-usage](http://stackoverflow.com/questions/653096/howto-free-inode-usage)

---

### Post by RCXtest on 2014-03-26
Thanks, I had been reading up on inodes, and your link led in the correct direction. I cannot find a way to 'release' the inodes that still seem to be used up by the files I deleted. 

Time to reinstall anyway, 10.04 coming to end of its LTS. Trying to decide between Opensuse or Fedora.

---

### Post by houstonbofh on 2014-03-28
To more detailed (and complex) articles if you want to try...

[http://www.kossboss.com/freeinodes](http://www.kossboss.com/freeinodes)
[http://askubuntu.com/questions/231585/running-out-of-inodes](http://askubuntu.com/questions/231585/running-out-of-inodes)

---

