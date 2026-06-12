---
title: "Update Manager problem, changed /home/ as the soruce?"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by perryjp on 2009-08-17
Hey, I'm running into a problem with update manager. When I press the Install Updates button, nothing happens.

I did a sudo apt-get update and then gksudo /usr/bin/update-manager and when I click the button I get:

> 
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 572, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py", line 946, in checkFreeSpace
    st = os.statvfs(d)
OSError: [Errno 2] No such file or directory: '/home'
I did change my home directory to /home2/ so I could automount some network directories so I'm thinking this might have something to do with the problem.

Any help would be appreciated, thanks!

---

### Post by jerrrys on 2009-08-17
change home2 back to home and you should be ok.  also if you want a home2, just create a new folder.  there are hidden files in home that are necessary to many programs...

---

### Post by perryjp on 2009-08-18
Well, as I understand it I do need to leave my stuff in /home2/ due to automounting network directories.

I didn't only change the directory name, I did change DHOME in [FONT=monospace][/FONT]/etc/adduser.conf to /home2 as well as all references to /home in /etc/passwd

---

### Post by perryjp on 2010-12-01
I never did fix this... I'm still stuck on Jaunty and would like to upgrade. I found this bug noted:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/463506](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/463506)

which was fixed in lucid but how do I get around that to upgrade while on Jaunty?

Thanks

---

