---
title: "iPod Shuffle Suddenly Not Mounting"
date: 2013-08-23
forum: Hardware
---

### Post by JaredNJames on 2013-08-23
My iPod shuffle was working fine up until yesterday.  Plug it in, it popped up in the notifications as being attached and then I could open gtkpod and manage the music.

Now all of a sudden it doesn't seem to automount on insertion anymore.  The only place I can see any sign of the shuffle is with the command lsusb which shows it, but nowhere else does it appear.

I have absolutely no idea why this happened, I haven't installed anything and I even did a fresh install of the OS to try and rectify the problem and it didn't help.  All I've done between yesterday and today is shut the laptop down and start it again.

Anyone have similar issues or know of a solution it would be much appreciated.

Ubuntu 13.04 with Gnome 3.8.  iPod Shuffle 2nd Generation.

---

### Post by Whoopie on 2013-08-24
You should install latest linux image 3.8.0-30.44, it has a fix for it. -> [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-raring.git;a=commitdiff;h=16f333a2318a6c6ed5359fb1d6c880e4f93f1aaa](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-raring.git;a=commitdiff;h=16f333a2318a6c6ed5359fb1d6c880e4f93f1aaa)

---

### Post by JaredNJames on 2013-08-24
Thank you for replying.  I'll give it a go and get back to you.

UPDATE: This works perfectly.  I updated to the latest 3.10 kernel (just because it was there) and now the problem is gone.

---

