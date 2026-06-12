---
title: "Where has my Hard Drive space gone?"
date: 2008-05-11
forum: Hardware
---

### Post by wobbleyhead on 2008-05-11
Afternoon all,

It's a lazy linux sunday and I am doing a little bit of housekeeping on Gusty.

I've been cleaning out old files and installing some new apps when i got an error saying that i was running out of disk space. I only installed Gusty last week after moving from Gentoo (which upon reflection was a bit nails for me as I'm still a n00b).

I've read through this [http://ubuntuforums.org/showthread.php?t=766985&highlight=disk+usage](http://ubuntuforums.org/showthread.php?t=766985&highlight=disk+usage)
and run dmesg which the output is attached along with a screenshot of the Disk usage analyszer

I've also run sudo apt-get clean and sudo find -name '*' +1G/500M/100M/50M and got the results I expected to see.

So I'm a bit confused as to where the disk space has gone, does anyone have any ideas?

---

### Post by tubbygweilo on 2008-05-11
Do you have any deleted files lurking in the .trash folder? I ask because if you have been on a deleting spree then they are iirc held in the .trash folder until you go in and get rid of them for good so as to release the space they occupied back to the file system.

---

### Post by wobbleyhead on 2008-05-11
yeah, i cleaned out the .trash file...for some reason i had two so i cleaned out both.

the thing that's confusing me is why the disk usage analyser shows that there is 36.8Gb on the disk..correct..but that there is only 2.8 Gb free...?
and then the usage graph shows that only 6.8G is being used in the file system

---

