---
title: "Unmet dependencies: linux-restricted-modules-server"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by spleiner on 2009-05-07
Since about yesterday I have recieved the following error when trying to update my Jaunty-server with
```

Command:
sudo aptitude update && sudo aptitude full-upgrade

``````

Result:
The following packages are BROKEN:
  linux-restricted-modules-server
The following NEW packages will be installed:
  linux-image-2.6.28-12-server
The following packages will be upgraded:
  linux-image-server linux-server
3 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.7MB of archives. After unpacking 95.8MB will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-server: Depends: linux-restricted-modules-2.6.28-12-server which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-server

Keep the following packages at their current version:
linux-restricted-modules-server [2.6.28.11.15 (jaunty, now)]

Score is 189

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```On my other 2 Ubuntu machines (desktops, not server) I have the same error but for -generic instead of -server.

Is there anything I can do to resolve this or do I have to wait for the correct package being uploaded to the repository? Its very annoying being informed that I have updates to install but not being able to do so because of this error...

---

### Post by liame on 2009-05-07
Hi
just to say I have the same problem here (but with the generic one)
normally i would have forced the upgrade, but i am not sure if it's so good an idea to remove the linux-generic, i think that file is necessary for getting the following upgrades and no needing to make it manually.
but i am so no sure if it's so or no.

if u go for the forcing solution by removing this keep me posted, thanks :)

something else:
i tried too

~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-generic
The following NEW packages will be installed:
  linux-headers-2.6.28-12 linux-headers-2.6.28-12-generic
  linux-image-2.6.28-12-generic
The following packages have been kept back:
  linux-restricted-modules-generic
The following packages will be upgraded:
  linux-headers-generic linux-image-generic
2 upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 34.0MB of archives.
After this operation, 170MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

---

### Post by spleiner on 2009-05-07
I dont think I will force the upgrade since this is some core packages that will most likely ruin my system if I do :-( I have done that in the past and almost always found myself with a system that wouldnt boot so I would love to find a solution to the problem or better yet, suddenly find that the dependencies are met thru new packages in Ubuntus repositories.

But if I find a solution I will make sure to post it here for you and others in the same predicament as us...

---

### Post by spleiner on 2009-05-09
Problem solved itself when repositories were updated with packages that resolved the broken dependencies.

---

