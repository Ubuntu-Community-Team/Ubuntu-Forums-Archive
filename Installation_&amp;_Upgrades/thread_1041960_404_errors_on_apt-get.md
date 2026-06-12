---
title: "404 errors on apt-get"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by bandad on 2009-01-17
Has something been moved, expired, or deleted?
I need to install GIT on a box running 7.04 and I continually get 404 errors from apt-get

```
bob@forte:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  git
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 262kB of archives.
After unpacking 995kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  git
Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com feisty/universe git 4.3.20-10
  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/git/git_4.3.20-10_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

git-core is similar
apt-get update gives many 404s.

Do I have to upgrade the system? I really don't want to have to do that right now.

ideas?

---

### Post by Pumalite on 2009-01-17
No support I think. Might be wrong.

---

### Post by ugm6hr on 2009-01-17
> **bandad said:**
> Do I have to upgrade the system? I really don't want to have to do that right now.

Feisty is not supported any more.  Hence the official repos have been removed.

Yes - you should upgrade.

If you really don't want to (not advisable), you can edit your repos.

Look here for advice: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Tim Sharitt on 2009-01-17
Nevermind

---

### Post by bandad on 2009-01-17
> **ugm6hr said:**
> Feisty is not supported any more.  Hence the official repos have been removed.

Yes - you should upgrade.

If you really don't want to (not advisable), you can edit your repos.

Look here for advice: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

Looks like an upgrade then.
Thanks for the help

Bob

---

### Post by Pumalite on 2009-01-17
Try:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by bandad on 2009-01-17
Upgrade complete! GIT installed !!!

Thanks everyone.
Why was I worrying about the upgrade? Only took 30mins.

Bob

---

### Post by ugm6hr on 2009-01-17
> **bandad said:**
> Upgrade complete! GIT installed !!!

Thanks everyone.
Why was I worrying about the upgrade? Only took 30mins.

Bob

No worries.

If you don't like upgrades too much, you should be prepared for Gutsy's withdrawal of support in April.

I'd recommend sticking with Hardy (once upgraded from Gutsy), since it is LTS, and you can then just upgrade directly from LTS to LTS every 2-3 years.

---

