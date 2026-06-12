---
title: "Installing o3d on Ubuntu"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by sarky7 on 2009-04-25
I decided to try to build Google's new 3d environment for web browsers for my Ubuntu machine.  

First, I go here: 

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fsrc.chromium.org%2Fviewvc%2Fchrome%2Ftrunk%2Fdepot_tools%2Frelease%2Flinux%2Fgclient.py%3Fview%3Dlog%26pathrev%3D9812&ei=Tf_ySdLYNpGItAPup_DhCg&usg=AFQjCNEiFei-c6zlGGL6GnurILNz_5SkLQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fsrc.chromium.org%2Fviewvc%2Fchrome%2Ftrunk%2Fdepot_tools%2Frelease%2Flinux%2Fgclient.py%3Fview%3Dlog%26pathrev%3D9812&ei=Tf_ySdLYNpGItAPup_DhCg&usg=AFQjCNEiFei-c6zlGGL6GnurILNz_5SkLQ)

This is the link to gclient.py.  Download that to /usr/bin.

Then cd to /usr/bin, ln -s gclient.py gclient.

Now I'm following the steps here:

[http://code.google.com/p/o3d/wiki/HowToBuild](http://code.google.com/p/o3d/wiki/HowToBuild)

Since there wasn't a thread for o3d on Ubuntu, I started this one and hope other people will post their experiences.

---

### Post by OKKARE on 2009-05-28
Thanks for the istructions, but it says "sudo: gclient: command not found".

and 

"noah@belle:~$ gclient config [http://o3d.googlecoe.com/svn/trunk/googleclient](http://o3d.googlecoe.com/svn/trunk/googleclient)
bash: /usr/bin/gclient: Permission denied"

---

### Post by Skofo on 2009-05-28
Ha, lucky for you I found this thread by Googling only two hours after you posted that.

To fix the permission issue, right-click on gclient, go to Properties, go to Permissions and allow executing of the program. ;)

However, I have another problem. It says that I have an outdated version of Subversion. Does Ubuntu have an outdated version of Subversion by default?

---

### Post by weaponx69 on 2009-08-06
Thanks, that helped.  I don't know why the instructions do tell you about downloading and install gclient first before you can check out O3D.

---

### Post by suoko on 2009-09-16
i'm trying ppa repo for o3d on jaunty
[https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily](https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily)

but neither chrome nor chromium recognize it at the moment

UPDATE: with new packages it now works

---

