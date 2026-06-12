---
title: "Blank screen and home directory not found"
date: 2008-08-29
forum: General Help
---

### Post by swappo1 on 2008-08-29
Hello,

I got a blank screen today while booting up.  I got passed grub, but then the screen went blank as it normaly does for a period of time but the login screen never came up.  I hit <Ctrl><Alt><delete> and the login screen came up.  I got a message that the home directory does not appear to exist and do I want to login as root.  Whether I select yes or no, I get a message stating the session only lasts 10 seconds and it returns me to login.  If I reboot from options it boots up as expected.  This blank screen problem only happens about 1 in 10 bootups.  It all started when I ugraded to Hardy Heron.  I would really like to find out why this happens and fix it.  Any ideas?  Thanks

---

### Post by HermanAB on 2008-08-29
If /home is not mounted, then that will happen.  It is likely due to to a timing error in the initialization code.

---

### Post by swappo1 on 2008-08-29
Any idea how I can fix this timing error?  It doesn't happen that often but I would still like to fix it so it never happens.

---

### Post by jigsaws on 2008-08-29
Try to boot rescue mode and check what happend. Is your /home at root filesystem or own /home filesystem?

---

### Post by swappo1 on 2008-08-29
> Try to boot rescue mode and check what happend. Is your /home at root filesystem or own /home filesystem? 
When I boot into rescue mode, how do I check what happened?  Is there a log of some sort?  Not sure what you mean by the last sentence, but my /home file system is on its own partition.

---

