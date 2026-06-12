---
title: "how do i install a program and read a win2k hdb1?"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by bdd4 on 2005-12-24
brand new to linux - i am.

my system: running ubuntu breezy 5.10, 1.5GHz AMD, 1GB ram, 40GB hda1, 120          GB win2K hdb1.

1. program switchercadiii.exe downloaded to my desktop - how do i install it ?

2. hdb1 is 120GB hd with virus infected win2k programs. how can i read files from that location ? After invoking SYSTEM,ADMINISTRATION,DISKS,CLICK ON 120GB HD,PARTITIONS,  report is that windows ntfs file system is inaccessible, ENABLE  choice does nothing.

thank you in advance

bdd4

---

### Post by kaamos on 2005-12-24
1. .exe is a windows program so asking how to install it in linux is like asking "I  have MozillaCaminov.1.1.dmg from my mac on my winxp desktop, how to install?". So installing an exe requires a windows enviroment. Luckily this can be done:
- with wine. Install wine with synaptic. See [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
- in vmware or similiar emulator. See [http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

2. Look here: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Hope this helps. :)

---

### Post by bdd4 on 2005-12-24
[QUOTE=kaamos]1. .exe is a windows program so asking how to install it in linux is like asking "I  have MozillaCaminov.1.1.dmg from my mac on my winxp desktop, how to install?". So installing an exe requires a windows enviroment. Luckily this can be done:
- with wine. Install wine with synaptic. See [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
- in vmware or similiar emulator. See [http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

2. Look here: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Hope this helps. :)[/QUOTE]

thanks for the input.

i have been reviewing mount ntfs commands but in the examples given the assumption stated in the example is that windows is on hda1. my ubuntu 5.10 breezy is on hda1, windows is on hdb1. suggestions ?

bdd4

---

### Post by gsdefender on 2005-12-24
You should already be able to access your partition by browsing /media/hdb1, you should otherwise try:

   mkdir -f /media/hdb1
   mount -t ntfs /dev/hdb1 /media/hdb1

You would want to add this row to the /etc/fstab

    /dev/hdb1 /media/hdb1 ntfs defaults,user,rw,uid=xxx,gid=xxx 1 2
                                      
The uid and gid parameters should be the same as those of the account you want to use. You can get them as so

              id -u (for uid)
              id -g (for gid)

for the current user.

Writing on NTFS is impossible by default, but you will like the Captive package if you can figure out how to install it (I'm trying to do it now on a Slackware box, but the principles should be the same).

---

### Post by kaamos on 2005-12-24
Writing to ntfs is really not safe and should not be instructed. The possibility of data loss is just too big.

Just my 2 cents..

---

### Post by Badojo on 2005-12-24
yea it would be smart to check out that wiki its loaded with all the answers you need to continue solving the problems you have and whatever they may be it will be answered.

---

### Post by bdd4 on 2006-01-01
though belated, thaks for the help

bdd4

---

### Post by bdd4 on 2006-01-01
though belated, thanks for the help

bdd4

---

