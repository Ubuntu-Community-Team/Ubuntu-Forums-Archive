---
title: "No space left on root partition?"
date: 2008-11-07
forum: General Help
---

### Post by MDSmith2 on 2008-11-07
Hello, I use Xubuntu and wanted OpenOffice today so I started to install it and it said there was no space left on my root partition. I looked at my root partition (my partitions are /boot(ext3), /root(jfs), /home(jfs), and a swap) and it said it was only 9 MBs and had no space free, but when I booted up gparted, it said it was 9 GB with 7 Gbs free. 

Thanks

---

### Post by taurus on 2008-11-07
What's the output of this command from a terminal?

```
df -h
```
You can free up some space with these two commands.

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by MDSmith2 on 2008-11-07
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             950M  941M     0 100% /
varrun                189M  100K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   68K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
/dev/sda3              27G  9.5G   18G  36% /home
/dev/sda2             9.3G  1.6G  7.8G  17% /usr
overflow              1.0M   12K 1012K   2% /tmp

```weird, this says I don't have any space, but gparted says I have 7 GBs out of 9.
apt-clean removed 470 mb worth of files o.O

---

### Post by taurus on 2008-11-07
> **MDSmith2 said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             950M  941M     0 100% /
varrun                189M  100K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   68K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
/dev/sda3              27G  9.5G   18G  36% /home
**[COLOR="Blue"]/dev/sda2             9.3G  1.6G  7.8G  17% /usr[/COLOR]**
overflow              1.0M   12K 1012K   2% /tmp

```
weird, this says I don't have any space, but gparted says I have 7 GBs out of 9.

Your free space, 7.8GB, is on /usr.  So, unless you plan to install something in /usr, you are maxed out your disk on /.  In other words, if you plan to use disk space anywhere else besides /home and /usr, you are maxed out.

---

### Post by geirha on 2008-11-07
> **MDSmith2 said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             950M  941M     0 100% /
varrun                189M  100K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   68K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
/dev/sda3              27G  9.5G   18G  36% /home
/dev/sda2             9.3G  1.6G  7.8G  17% /usr
overflow              1.0M   12K 1012K   2% /tmp

```
weird, this says I don't have any space, but gparted says I have 7 GBs out of 9.

That's probably on the /usr partition it says that on.
```
sudo du -h -x --max-depth=1 /
``` should show you where the space on /dev/sda1 is used. Most of it is probably used by /var. Cleaning out the downloaded deb-files will probably give you a few 100 megs.

Once you've freed some space, you should disable the overflow filesystem it mounted on /tmp:
```
sudo /etc/init.d/mountoverflowtmp stop
```

---

