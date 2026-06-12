---
title: "Partitioning and package management"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by shylent on 2009-08-15
First of all, hello, everyone!

I am coming from another distribution (I've had it with rpm and kde4...) and have just completed my first ubuntu installation.

Now I do have a couple of questions.
First. Here is how I've handled paritioning:
$ df -h
/dev/sda6              19G  2.5G   15G  15% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G   96K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  156K  1.8G   1% /dev
tmpfs                 1.8G   84K  1.8G   1% /dev/shm
lrm                   1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5             441M   36M  383M   9% /boot
/dev/sda8             410G  219M  389G   1% /home
/dev/sr0              699M  699M     0 100% /media/cdrom0

Did I get it right with a 500 Mb boot, ~20Gb "/" (also have 8gb swap, - I am running on 4Gb RAM)? Or should I have done it a different way?

Second question:
Can I use aptitude alongside synaptic (synaptic uses apt-get, right?). I have a lot of debian servers at work and I've figured that aptitude is far superior, compared to apt-get in the dependencies handling departament :P So, can I use aptitude for installing/removing arbitrary packages and synaptic just for updates and, basically for looking at my packages in a neat GUI? Without breaking everything, that is.

Thanks in advance for any information!

---

### Post by raymondh on 2009-08-15
df -h looks good.  I've never used a /boot but I have read that it really does not need much so 500mb seems to be Ok.  Swap at 8GB is your preference.  As you  know by now, swap usage is dependent on your regular app usage and hibernating practices.  Some advocate 2x installed RAM.  Some advocate 1-2X maximum installable RAM (for future possible additions).  Some just use 1-2GB swap.  Though I use 4GB RAM and 1.5GB swap ..... I'll say, "if you have the space,  what's a few GB dedicated to swap gonna cost you?".  Root at around 20GB is OK.  I have mine at 20GB and have downloaded already a bunch of apps.... but still am at around 8GB.

Using apt-get or aptitude is really a personal preference.  I use apt-get because I am used to it.  One thing for sure is you can only use 1 package manager at a time.

Happy Ubuntuing.

EDIT : when you make your first update/upgrade ..... make sure you go to software sources (system > administration) and un-tick the CD-rom ;)

---

