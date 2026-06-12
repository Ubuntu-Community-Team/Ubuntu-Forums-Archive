---
title: "Upgrading Problem"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by Telekinesis on 2009-02-15
So, I have been out of the loop for a long time since I haven't had access to my laptop. I had tons of updates to install for Feisty Fawn, all of which are now installed. I wanted to proceed with upgrading the distro, so I read up and found out I needed to exchange all traces of us.archive with links to the repositories (old-releases) which I also have done. My sources.list file now only contains the following:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

The problem is, whenever I try to upgrade I'm still getting an error regarding the us.archive link:

'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/binary-i386/Packages.gz)'

So I'm still not able to upgrade. I'm not sure why it's still showing its ugly head. Something simple that I'm missing? Any help would be appreciated. Thanks in advance.

---

### Post by Elfy on 2009-02-15
Do you have any sources in /etc/apt/sources.list.d ?

```
ls /etc/apt/sources.list.d
```

If you get a result then you'll need to deal with those repos too

---

### Post by Telekinesis on 2009-02-15
> **forestpixie said:**
> Do you have any sources in /etc/apt/sources.list.d ?

```
ls /etc/apt/sources.list.d
```

If you get a result then you'll need to deal with those repos too

Thanks for your help. I edited all of the us.archive links out of sources.list.d and tried to upgrade. Now the problem is that for some reason it keeps trying to fetch the 'us.archive' links even after I replace them. I can run an apt-get update and everything goes smoothly. As soon as I attempt to upgrade, the prereqs fail. If I check the log, it shows the archive links once again.

---

### Post by Telekinesis on 2009-02-15
Update:

Fixed my problem. I ended up having to switch 'feisty' to 'gutsy' in sources.list and the prereq list, then I just had to run an apt-update and apt dist-upgrade. I couldn't use the graphical installation, that was the main problem that kept switching the links back to the broken feisty-backports link. I'm in the process of upgrading right now through terminal, smooth sailing thus far.

Update:

Running Gutsy now. Everything went fine.

---

