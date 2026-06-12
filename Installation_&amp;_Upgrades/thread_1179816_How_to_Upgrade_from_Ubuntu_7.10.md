---
title: "How to Upgrade from Ubuntu 7.10"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by edwinkcw on 2009-06-06
I have a server installed for long time. Recently, I ssh to this machine but I found that I cannot apt-get anymore since all the source in source list are expired. How can I upgrade my Ubuntu? Thanks.

---

### Post by Bucky Ball on 2009-06-06
I would fresh install 8.04 LTS (long term support) server version. Upgrade can take awhile and are sometimes problematic.

:)

---

### Post by edwinkcw on 2009-06-06
Thus, you mean I need to reinstall Ubuntu as well?

---

### Post by pastalavista on 2009-06-06
But if you don't want to install fresh

```
sudo do-release-upgrade
```

---

### Post by edwinkcw on 2009-06-06
> **pastalavista said:**
> But if you don't want to install fresh

```
sudo do-release-upgrade
```

I had tried this 
but it shows
$ sudo do-release-upgrade
sudo: do-release-upgrade: command not found

---

### Post by pastalavista on 2009-06-06
> **edwinkcw said:**
> I had tried this 
but it shows
$ sudo do-release-upgrade
sudo: do-release-upgrade: command not found

come to think of it, 'sudo' may not be necessary.. try it without sudo, it might not need it until the process starts... or it could just be for Intrepid and Jaunty

Or you could try ```
sudo apt-get upgrade -d
```

edit: just read the help file and it specifies this for servers
```
do-release-upgrade -m --server
```

---

### Post by edwinkcw on 2009-06-06
> **pastalavista said:**
> come to think of it, 'sudo' may not be necessary.. try it without sudo, it might not need it until the process starts... or it could just be for Intrepid and Jaunty

tried, however, the same error occurs
$ do-release-upgrade
-bash: do-release-upgrade: command not found
btw, thanks

---

### Post by pastalavista on 2009-06-06
Oh well, been to long since I ran Gutsy... sorry

---

### Post by edwinkcw on 2009-06-06
> **pastalavista said:**
> Oh well, been to long since I ran Gutsy... sorry

ok....any other suggestions, I don't want to reinstall every thing

---

### Post by pastalavista on 2009-06-06
According to [this page]("http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts"), you need to install update-manager-core first.

---

### Post by edwinkcw on 2009-06-06
> **pastalavista said:**
> According to [this page]("http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts"), you need to install update-manager-core first.

Ya...but....I cannot apt-get now since the source list is out-of-date....

---

### Post by Partyboi2 on 2009-06-06
Hi, backup your current sources.list and try replacing your sources.list with
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
```then update and try installing the update-manager-core package.

---

### Post by pastalavista on 2009-06-06
You can download the packages here

[http://mirrors.kernel.org/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~dapper5_all.deb]("http://mirrors.kernel.org/ubuntu/pool/main/u/update-manager-core/update-manager-core_0.56~dapper5_all.deb") There was no version specifically for Gutsy, but this should do it. You could also edit your sources.list file (back it up first) and change 'Gutsy' to 'Hardy' in the entries... and then do apt-get update

---

### Post by edwinkcw on 2009-06-06
> **Partyboi2 said:**
> Hi, backup your current sources.list and try replacing your sources.list with
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
```then update and try installing the update-manager-core package.

Thanks,
How can you get this source list?

---

### Post by Partyboi2 on 2009-06-06
From the terminal backup your current sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```then open your sources.list
```
sudo nano /etc/apt/sources.list
```delete the contents and add 
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
``` then save and close nano
```
Ctrl+o 
Enter
Ctrl+x
```
then
```
sudo apt-get update
sudo apt-get install update-manager-core
```

---

### Post by edwinkcw on 2009-06-06
> **Partyboi2 said:**
> From the terminal backup your current sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```then open your sources.list
```
sudo nano /etc/apt/sources.list
```delete the contents and add 
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
``` then save and close nano
```
Ctrl+o 
Enter
Ctrl+x
```
then
```
sudo apt-get update
sudo apt-get install update-manager-core
```

I know how to do it..
but more and more problem occurs about the dependency:

Setting up libgtk2.0-common (2.12.9-3ubuntu2) ...
Setting up libpango1.0-common (1.20.1-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
Failed to clean up for defoma: 256 at /usr/sbin/update-pangox-aliases line 48.
dpkg: error processing libpango1.0-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.20.1-1); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.20.1); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured

---

### Post by Bucky Ball on 2009-06-06
> **Bucky Ball said:**
> I would fresh install 8.04 LTS (long term support) server version. **Upgrade** can take awhile and **are sometimes problematic**.

:)

Save everything you need to save and start again. Easiest in the long run. I *never* keep anything on the same partitions as my OSs. That way you can always just kill the appropriate OS and start again without having to pluck bits out.

---

### Post by edwinkcw on 2009-06-06
> **Bucky Ball said:**
> Save everything you need to save and start again. Easiest in the long run. I *never* keep anything on the same partitions as my OSs. That way you can always just kill the appropriate OS and start again without having to pluck bits out.

ic .... actually, how do you partition your HD?

---

### Post by Bucky Ball on 2009-06-06
Not sure if you have a desktop environment on your server or not, but you can use Gparted to resize and partition (System->Administration->Partition Editor). If you're wanting to resize the partitions your OS is on, your best bet is to download Gparted LIVE iso and make a CD and boot from that as the partitions need to be unmounted to work on (impossible if you are actually running your OS from the parittion you want to resize):

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

0.4.5-2 is the latest, the first one. Backup your data to an external drive or somewhere else is a good idea if possible before resizing.

---

