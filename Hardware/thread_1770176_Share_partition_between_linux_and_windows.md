---
title: "Share partition between linux and windows"
date: 2011-05-28
forum: Hardware
---

### Post by T.Money on 2011-05-28
I just got a dual boot set up going (windows 7 and Ubuntu 11.04) and I'm interested in setting up a shared partition between both of the OS's hopefully around 30GB for my music storage and all of my homework. I've been reading that a FAT32 formatted partition is the best bet, but I've also heard files on that type of drive are more susceptible to corruption. Just looking for some input on the best way to do this - I definitely don't want to have to worry about corrupted files if I'm storing my Homework and music on this drive. Does how big I make it make a difference, is it really more likely to be corrupted/how do I avoid that, any drawbacks to be aware of, etc...
Thanks!

---

### Post by garvinrick4 on 2011-05-28
Make it a NTFS partition it will come up as a letter in Windows, E or G or F whatever is next in line and will be a sda number in Linux if first drive sdb number if in a second drive so on. Will be say sda6 or sda7 whatever is next in line:
You can also have it automount in Linux through /etc/fstab using UUID is best as below an example make a directory in media:
```
sudo mkdir /media/data
```Install at bottom of fstab as such below:

# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0

Notice above using UUID and /dev/sda8 is commented out:
Will now automount when O.S. boots.

Can get your own UUID number by:
```
sudo blkid
``` (second letter lower case L)
Below is link for fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by nzjethro on 2011-05-28
Hi there. I would recommend NTFS over fat32. It's less susceptible to corruption, and you can store files larger than 4GB. I found this out the hard way when I tried to put a game .iso on a fat32 disk, and ended up having to reformat to NTFS. So I would go NTFS.
As for access from both OSes, check out this site:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
If you have already installed everything, just look at the last section. I am running Win 7 and Maverick Meerkat, and used this to set up my entire system. Basically, what you should do is delete you "Documents", "Pictures", and what ever other folders you would like to share from /home/user/. Then, set up these folders in your shared partition (probably called "xxGB Filesystem" if you haven't named it). Then, create links to these folders from /home/user/. To do this, select these folders in your shared partiton, right click and select "Make Link". Then, drag these links into your /home/user/ folder.
Good luck!

---

