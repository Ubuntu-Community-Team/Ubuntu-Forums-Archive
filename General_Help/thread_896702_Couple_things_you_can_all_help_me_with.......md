---
title: "Couple things you can all help me with......"
date: 2008-08-21
forum: General Help
---

### Post by fredster001 on 2008-08-21
Hi,

Just configured my laptop so I'm dual booting now with xp.

1) I have all my music, videos etc. on a separate partition. In Ubuntu this comes up as media, although it doesn't recognise it (mount I think it calls it) until I've clicked it in the "places" menu. I would like an icon for it on the desktop all the time, from the moment I log in. I have tried right clicking this desktop and creating a launcher, but with no success. Any ideas?

2) How do i get different backgrounds for each workspace?

3) If I want to use my evolution with my hotmail account, do I need to pay?


Thanks in advance for all the help!



Fredster

---

### Post by silkstone on 2008-08-21
1. You will have to add a line to /etc/fstab for your partition to be mounted automatically. This guide tells you how to do it - it's not too difficult!

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

2. As far as I know, you can't do this at the moment.

3. Sorry - can't help - I use Thunderbird not Evolution.

EDIT/

I think you should create the new mount point as a subfolder of /media - e.g. /media/music - rather than directly under the root directory. That will ensure that the icon appears on your desktop.

---

### Post by caljohnsmith on 2008-08-21
About your first question, I think probably all you need to do is add an entry for your media partition in /etc/fstab. If you need help with that, please post the output of:
```
sudo fdisk -lu
```

---

### Post by fredster001 on 2008-08-21
About the first question:

Couldn't work out the last bit of the tutorial, sudo fdisk -lu returns this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   105016904    52508421    7  HPFS/NTFS
/dev/sda2       105016905   168650369    31816732+   b  W95 FAT32
/dev/sda3       232332093   234436544     1052226   d7  Unknown
/dev/sda4       168650370   232332029    31840830    5  Extended
/dev/sda5       168650433   229777694    30563631   83  Linux
/dev/sda6       229777758   232332029     1277136   82  Linux swap / Solaris

Partition table entries are not in disk order


sda2 is the one with all the files on it...

---

### Post by caljohnsmith on 2008-08-21
First create a folder to mount your partition if it doesn't all ready exist, and also backup your fstab:
```
sudo mkdir /media/sda2
sudo cp /etc/fstab /etc/fstab.082108
```
Then pull up your fstab:
```
gksudo gedit /etc/fstab &
```
And add this line:
```
/dev/sda2 /media/sda2 vfat iocharset=utf8,umask=000 0 0
```
Reboot, and check that it works.

---

### Post by fredster001 on 2008-08-21
Great! thanks! thats worked now.

Any help with the other things (although they aren't really as important)

---

### Post by caljohnsmith on 2008-08-21
> **fredster001 said:**
> Great! thanks! thats worked now.

Any help with the other things (although they aren't really as important)
I'm glad its working for you now. :) About Evolution + hotmail, I don't use either, but it seems like you would have to check your hotmail account guidelines to see whether it is even possible to set up an external client to access it. And about a different background for each workspace, I don't think that it can be done unless you find some special software to provide a hack. :)

---

### Post by adrien214 on 2008-08-21
about the workspace, I remember that if you have compiz enabled (System>Preferences>Appearance>Visual Effects tab) then you should have too much trouble enabling different images for each desktop and don't forget the compiz-config-editor( sudo aptitude install compizconfig-settings-manager)... but I might not remember to well, if not, then check out [wallpapoz]("http://ubuntuforums.org/showthread.php?t=69507&highlight=different+background+workspaces") (which I don't actually recommend, lol)

about hotmail, it's a webmail, I am not aware of any mail-client capabilities.

---

