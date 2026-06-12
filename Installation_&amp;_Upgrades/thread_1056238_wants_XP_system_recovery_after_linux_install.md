---
title: "wants XP system recovery after linux install"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2009-01-31
daughters puter broke, maybe virus, so did clean reinstall of xp.  decided to give her a couple of linux distros, thinking maybe they are safer.
used gparted to repartition hd:
[root@amanda dan]# fdisk  -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             692       11553    87249015    7  HPFS/NTFS
/dev/sda2   *           1         691     5550426    b  W95 FAT32
/dev/sda3           11554       12955    11261565   83  Linux
/dev/sda4           12956       19457    52227315    5  Extended
/dev/sda5           12956       14357    11261533+  83  Linux
/dev/sda6           14358       14618     2096451   82  Linux swap / Solaris
/dev/sda7           14619       19457    38869236   83  Linux

Partition table entries are not in disk order

Installed Ubuntu  8.04.  was then able to boot into either ubuntu or xp.
next installed fedora 10.  new menu.lst did not show ubuntu, only fedora and xp.  had some lockups in fedora, and had to pull plug to reboot 2 or 3 times.  replaced power supply.  added ubuntu into menu.lst.
boots into fedora and ubuntu fine.  tried to boot xp, and get "Preparing System Recovery Option", then PC Angel appears, and it wants me to use the system restore option for xp.

is there something i can do to recover xp without having to wipe the hd and reinstall xp, then reinstall ubuntu and fedora (and if i do all that, how can i be sure i don't end up with the same problem?
thanks in advance for any help.

---

### Post by Pumalite on 2009-01-31
Check this thread. It might be helpful:
[http://ubuntuforums.org/showthread.p...light=meierfra](http://ubuntuforums.org/showthread.p...light=meierfra)

---

### Post by vbdanl on 2009-01-31
> **Pumalite said:**
> Check this thread. It might be helpful:
[http://ubuntuforums.org/showthread.p...light=meierfra](http://ubuntuforums.org/showthread.p...light=meierfra)

that put me back at the ubuntu forums home page

---

### Post by Pumalite on 2009-01-31
Do a search for 'meierfra' in the Forums.

---

### Post by vbdanl on 2009-01-31
> **Pumalite said:**
> Do a search for 'meierfra' in the Forums.

i read bunches of meierfra posts, downloaded the ultimate boot cd, and tried to use it to run chkdsk.  it came back with "UMB's unavailable" and a bunch of German lingo.  didn't fix anything.  someone finally saw the simple error.. i needed hd0,0 instead of hd0,1.  it works fine now.
i have another pc that has vista instead of xp along with several linux distros.  it uses hd0,1 to boot vista, and hd0,0 for restore, so when fedora installed grub with hd0,1, it looked fine to me..
hope this helps someone down the road..  took most of my Sat.. :(

---

