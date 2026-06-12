---
title: "dist upgrade does not appear after cancelling"
date: 2008-11-01
forum: General Help
---

### Post by hwttdz on 2008-11-01
I had to cancel the dist upgrade and now I cannot get it to appear again.  I have my sources set to show all releases, and neither checking for updates through update manager nor apt-get dist-upgrade gets me anything.  Is there some way I can clear the canceled attempt? and try again?  Thanks.

---

### Post by hwttdz on 2008-11-01
help?

---

### Post by soro2005 on 2008-11-02
System --> Administration --> Update Manager should get you there. You can also download the "alternate" CD for your flavor and run it while you're logged in. That should offer you the upgrade. Or you can issue ```
sudo do-release-upgrade
``` Unsurprisingly, there are [several paths to Intrepid](http://www.ubuntu.com/getubuntu/upgrading).

---

