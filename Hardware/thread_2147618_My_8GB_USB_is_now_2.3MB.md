---
title: "My 8GB USB is now 2.3MB"
date: 2013-05-22
forum: Hardware
---

### Post by baqar on 2013-05-22
I was using linux mint, but when ubuntu 13.04 came i downloaded it
And used startup disk creator to create a bootable Ubuntu USB.
Now i want to use it. Its showing 2.3mb

I tried to format it, but no! nothig happened, even in windows

The pics are attached when i tried to format i get the following error via the DISK:confused: any one

[ATTACH=CONFIG]242895[/ATTACH][ATTACH=CONFIG]242893[/ATTACH][ATTACH=CONFIG]242894[/ATTACH]

---

### Post by sudodus on 2013-05-22
Please unmount (eject) and unplug the USB pendrive.

Plug it in again and run the following commands in a terminal window

```
 sudo fdisk -lu
```
```
 cat /etc/mtab
```
and post the result in a reply. This will help us understand and give advice.

---

### Post by baqar on 2013-05-22
Here you go :)

[ATTACH=CONFIG]242896[/ATTACH][ATTACH=CONFIG]242897[/ATTACH]

---

### Post by sudodus on 2013-05-22
Some install drives have strange partitioning, and it may not be interpreted correctly by some programs. But it can still do it's job.

1.  Did you try to install from it before you tried to format it? In that case, what was the result?

2. How did you try to format it? Which tool in Mint (before trying in Windows)?

-o-

3. When you want to try again, wipe the partitions with ***gparted***. And then create a new partition and format it to FAT32.

4. Finally, try again with the startup disk creator.

---

### Post by baqar on 2013-05-22
> **sudodus said:**
> Some install drives have strange partitioning, and it may not be interpreted correctly by some programs. But it can still do it's job.

1.  Did you try to install from it before you tried to format it? In that case, what was the result?

2. How did you try to format it? Which tool in Mint (before trying in Windows)?

-o-

3. When you want to try again, wipe the partitions with ***gparted***. And then create a new partition and format it to FAT32.

4. Finally, try again with the startup disk creator.


1. I installed ubuntu from it, and right now i am using ubuntu which i have installed using this USB.

2. I first tried to copy some stuff which i needed to give someone, but it say the USB is write protected, so i reboot my system and formated through Windows, after format it become 2.3MB :(


3. Yep will try Gparted now, and will post the result.

4. No need for startup disk creator now.:KS
[B][I]
[SIZE=2][FONT=fixedsys]*Alas! *
Cant Download gparted [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG] Check this thread [http://ubuntuforums.org/showthread.php?t=2147638](http://ubuntuforums.org/showthread.php?t=2147638)[/FONT][/SIZE][/I][/B]

---

### Post by sudodus on 2013-05-23
Try to add those repositories that are mentioned in the other thread! It can also be done with Synaptic.

And after that you should be able to download gparted. But honestly, I think gparted should be among the packages available without adding extra packages at least in Ubuntu. I don't know about Linux Mint.

Try the commands from this list of commands originally posted by *oldfred*.

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

---

