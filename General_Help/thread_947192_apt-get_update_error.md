---
title: "apt-get update error"
date: 2008-10-14
forum: General Help
---

### Post by linitha on 2008-10-14
hi,
im new to debian and im using ubuntu 8.04.
im trying to get apt-get update and its failed.
does anyone know whats going on what are things missing here?

root@tme-desktop:/home/tme# sudo apt-get update
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy Release.gpg
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/restricted Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/main Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/multiverse Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/universe Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates Release.gpg
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/restricted Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/main Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/multiverse Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/universe Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports Release.gpg
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/restricted Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/main Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/multiverse Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/universe Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed Release.gpg
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/restricted Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/main Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/multiverse Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/universe Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security Release.gpg
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/restricted Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/main Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/multiverse Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/universe Translation-en_US
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy Release 
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates Release
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports Release
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed Release
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security Release
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/restricted Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/main Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/multiverse Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/universe Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/restricted Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/main Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/multiverse Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/universe Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/restricted Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/main Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/multiverse Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/universe Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/restricted Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/main Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/multiverse Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/universe Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/restricted Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/main Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/multiverse Packages
Ign [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/universe Packages
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/restricted Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/main Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/multiverse Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy/universe Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/restricted Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/main Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/multiverse Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-updates/universe Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/restricted Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/main Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/multiverse Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-backports/universe Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/restricted Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/main Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/multiverse Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-proposed/universe Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/restricted Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/main Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/multiverse Packages
404 Not Found
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) hardy-security/universe Packages
404 Not Found
W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/main/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz) 404 Not Found

W: Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@tme-desktop:/home/tme#

---

### Post by iaculallad on 2008-10-14
Try to change you download server. System->Administration->Software Sources.

---

### Post by linitha on 2008-10-14
i tried changing the mirror from software sources.
but im not able to download the updates successfully.
still error. But i can click that link and access to the packages. but not through synaptic or software source.
is there any setting missing? or do i need to set my proxy somewhere?

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-10-14
What about doing, does it show the same error message?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by linitha on 2008-10-14
i'm getting the same error message.

root@tme-desktop:/home/tme# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@tme-desktop:/home/tme#

---

### Post by Ryadt on 2008-10-14
Is there any reason as to why you are using the root account?

---

### Post by linitha on 2008-10-14
There is no specific reason for it. In fact, i can't get updates as normal user or as root. it returns the same eorrr.

---

### Post by Elfy on 2008-10-14
I assume that you have no other problems with the net - so are you maybe using a proxy? If you are you need to make sure it's set for the repositiories as well, it might be that theyare - check in Synaptic - Settings, Preferences, Network

---

### Post by taladan on 2008-10-14
Note - root account is disabled/locked by default in a fresh install for security reasons - you can do everything root can do with your initial user by using the 'sudo' command.  There really isn't a reason to need to log in as root - if you need a persistent root environment then you use 'sudo -i' from your initial user.

Also - if you're logged in as root there is no need to type 'sudo' in front of any command.  You're causing yourself extra work.

Regarding the pkgs, +1 on checking for a proxy.

Tal

---

### Post by linitha on 2008-10-14
Hi everyone,
my problem has been resolved.
it caused by the http proxy.
i set to my valid proxy and it works.
thanks for helping guys

---

### Post by Elfy on 2008-10-15
Ok that's good I thought it might have been a proxy problem.

Re using root, it's probably best to not use it constantly. Use suod for non gui uses - eg commands running in a terminal and gksudo for gui needs.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

