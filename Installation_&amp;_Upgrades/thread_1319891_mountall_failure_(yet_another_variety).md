---
title: "mountall failure (yet another variety?)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by duckling9 on 2009-11-08
Hello
I've seen a number of threads about mountall failures, and although none of them seems to capture mine they might give some hope as to how I might fix it... but not quite the answer.

The message is mountall /proc ...device busy

My machine : amd64
Upgrade: jaunty to karmic
Dual boot: grub
Partitions: /sda3,4,5,6,7 

data: not backed up (I know, i know) - so please don't suggest anything as scary as a fresh install - am sure it isn't needed!

what works - booting into windows (the shame!), but all other previous kernels freeze in the same way.

What I did during the upgrade was to ask for my menu.lst to be left untouched (because of nasty things that I need for my pc to work, that I forget...). I have seen elsewhere that this might be the problem - my root partition is mounted, but read-only - so I can't edit the menu.lst file, which I think would solve the problem.

Can anyone help with this (sure its a very simple question for some) - any way without a livecd would be much preferable.

thanks 
jane

---

### Post by duckling9 on 2009-11-13
Aha! Thanks to witeshark, i finally realised the "e" button on the grub menu is very handy. After editing to point at the latest kernel (i found what this was from the partial boot, which allowed a ls /boot), I could then boot, and then edit menu.lst
 
Aah! very good :)
 
 
[http://ubuntuforums.org/showthread.php?t=1318129&highlight=mountall](http://ubuntuforums.org/showthread.php?t=1318129&highlight=mountall)

---

