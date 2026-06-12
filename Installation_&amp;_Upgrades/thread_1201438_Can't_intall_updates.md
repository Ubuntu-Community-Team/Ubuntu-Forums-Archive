---
title: "Can't intall updates"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by guppygould on 2009-07-01
Just installed Jaunty on my new laptop and everything was going super until I tried to update some packages. I get this:
[COLOR="Red"]
Not enough free disk space

The upgrade needs a total of 477M free space on disk '/'. Please free at least an additional 448M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/COLOR]

The laptop has two hard drives and I dual booted one drive with Vista and Ubuntu equally but It's still saying I don't have enough space to install some updates. I just used the default install setting and didn't change any of the partition sizes. I know brand new Ubuntu and Vista installs don't use 60GB of space, so what's the problem?

If anyone could help me with this I'd greatly appreciate it.

---

### Post by Soul-Sing on 2009-07-01
```
df -h
```
please post the results here.

and post a picture of the outcome of: ```
sudo gparted
```

---

### Post by guppygould on 2009-07-01
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   20M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  156K  1.5G   1% /dev
tmpfs                 1.5G   92K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2              70G   23G   48G  33% /media/Acer
/dev/sda3              68G   88M   68G   1% /media/DATA

---

### Post by guppygould on 2009-07-01
I'm guessing that the problem is that the /dev/sda5 usage is 100%?

Oh and the gparted command gives a "command not found" error.

---

### Post by guppygould on 2009-07-01
I've just tried to install flash now and it says I don't have enough space for the download. :(

Any easy fixes or am I going to have to reinstall?

---

### Post by guppygould on 2009-07-01
Any suggestions? - I really want to get this sorted as soon as possible.

-Leo

---

### Post by Kevbert on 2009-07-01
Please try the following commands
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
and see if any space is freed up.

---

### Post by guppygould on 2009-07-01
Thanks for the suggestions but it's still being used 100% :(

---

### Post by colau on 2009-07-01
> **guppygould said:**
> Thanks for the suggestions but it's still being used 100% :(
Can you post
```

sudo fdisk -l

```

---

### Post by Kevbert on 2009-07-01
If you have a Ubuntu Live CD run up the demo and see if you can enlarge sda1 with gparted as it seems to be on the small size. You'll need to reduce the size of sda2 first.

---

### Post by guppygould on 2009-07-02
Just to thank you all for the help and suggestions in this thread. I left it resizing some partitions last night and it did the trick. It was /dev/sda5 which needed the extra room as I thought.

Thanks again,

-Leo

---

