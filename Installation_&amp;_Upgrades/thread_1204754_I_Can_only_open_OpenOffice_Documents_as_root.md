---
title: "I Can only open OpenOffice Documents as root"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by tony_wh on 2009-07-05
Something odd has happened in the last 24 hours.  I don't know if it coincides with an update.  I have also just installed VirtualBox in order to run WM7. But...

When I now try to open an OpenOffice document of any type (Write, Calc or Presentation), it tries to open, shows the OpenOffice 3 splash, shows a window as if its about to show the data, then closes.  But if I open it from Nautilus as root, it opens OK.

I've tried removing OOO and reloading it.  It's not the folder permissions as it occurs however I configure them and whichever folder I use.  Of course I've googled and searched this site (indeed until then I thought I'd lost my files but someone in 2007 noted the same problem and found that they could open as root but never solved the problem).

Does anyone have any ideas? For safety, I'd rather not open documents as root.

Thanks in advance

T

---

### Post by aysiu on 2009-07-05
Try this: ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

Afterwards, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by tony_wh on 2009-07-06
Thanks for taking the trouble to reply.  I'm afraid that I'd already tried changing the file permissions and it makes no difference (I share the files between Windows at work and Ubuntu on my Laptop so the permissions are already rwxrwxrwx with me as the owner).

I'm currently reading through your link - it may not be as bad as I thought!

---

### Post by darolu on 2009-07-06
> **tony_wh said:**
> Thanks for taking the trouble to reply.  I'm afraid that I'd already tried changing the file permissions and it makes no difference (I share the files between Windows at work and Ubuntu on my Laptop so the permissions are already rwxrwxrwx with me as the owner).

I'm currently reading through your link - it may not be as bad as I thought!

What aysu told you to do is change the OWNER not just the mode (permissions); make sure your username and group (by default is the same as username) own the folder you are trying to read the files from, although chmod 777 should work; also make sure the folder (and its files) where openoffice is installed has 755 permissions.

---

### Post by tony_wh on 2009-07-06
Thanks for your help Darolu but as I said in my original reply: > (I share the files ... so the permissions are already rwxrwxrwx **_with me as the owner_**).When I add the column "Owner" in Nautilus, it has my user name against the files. Have I misunderstood?

I have checked all of my openoffice folder permissions - they are already 755.

This is obviously not a common problem!!:cry: I may just have to do a fresh install:frown:

---

### Post by tony_wh on 2009-07-07
The problem seems to have been solved by a partial upgrade:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/365763?comments=all](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/365763?comments=all)

Thanks to all for their help

---

