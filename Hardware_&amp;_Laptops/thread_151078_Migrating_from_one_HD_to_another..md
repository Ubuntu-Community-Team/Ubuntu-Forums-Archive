---
title: "Migrating from one HD to another."
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by inha on 2006-03-27
Here's the scenario: My old main hd is dying on me and I bought a new one. Now I'd like to transfer my system from the old one to the new one. Someone mentioned about creating a hd-image and transferring that to the new one but I have no clue whatsoever how this is done. 

So, can someone help me out or point me to the right direction?

---

### Post by nemin on 2006-03-27
[QUOTE=inha]Here's the scenario: My old main hd is dying on me and I bought a new one. Now I'd like to transfer my system from the old one to the new one. Someone mentioned about creating a hd-image and transferring that to the new one but I have no clue whatsoever how this is done. [/QUOTE]
To copy an image of your old harddisk to your new one, both harddisks should be exactly the same size, I believe (correct me if I'm wrong):-k 
What I'd do, is setting up your new harddisk in your computer, and installing Ubuntu on it (as 'main system'). Of course, you'll have to reinstall all software you want.
From that system, you can mount your old harddisk and copy the /home dir and eventually your /etc dir, because those directories contain most of your specific stuff.
I hope that makes some sens :p Good luck!:)

---

### Post by inha on 2006-03-27
Damn. My new one is quite a bit larger than the old one. I guess I'll have to do a fresh install then.

---

### Post by frodon on 2006-03-27
[QUOTE=nemin]To copy an image of your old harddisk to your new one, both harddisks should be exactly the same size, I believe (correct me if I'm wrong):-k [/QUOTE]It's not needed, you can put your image file to whatever you want if your new partition have enough space.

The simple way is to make a tar of your root partition and put it on another hdd or on a dvd. Then add your new hdd in your computer and boot on a live cd. With the live cd untar your old ubuntu partition on the new hdd, that's it for puting your old ubuntu partition on a new hdd.

To make the tar file use this command : ```
tar cvpzf backup.tgz --exclude=/mnt  /
```It will create the tar in the directory where you are, i suggest you to run this command in your second hdd if you have one. The --exclude command tells to not save the directory, i add /mnt because it's where i mount my partitions and i don't want to add my other partition in the tar.

In the live cd use this command to untar the archive : ```
tar xvpfj backup.tar.bz2 -C path_to_the_directory_where_you_mounted_your_new_ubuntu_partition
```By the way, you will have to re-create the directories you excluded (sudo mkdir /mnt)

However your new hdd will not have the boot sector activated and you will need to reinstall GRUB, i think. Don't worry it's easy to do, just follow one of those guides : 
[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by inha on 2006-03-27
Thanks a lot. Seems like a straight forward thing to do.

---

### Post by nemin on 2006-03-27
[QUOTE=frodon]It's not needed, you can put your image file to whatever you want if your new partition have enough space.[/QUOTE]
Ok, I'm sorry for the confusion. 
I was thinking about an exact clone of your harddisk (on physical level), isn't it a requirement in that case either? (just out of curiosity, my question is quite OP;))

---

### Post by aysiu on 2006-03-27
Use a live CD and PartImage.
The drives do not have to be the same size for this.

---

### Post by inha on 2006-03-29
I'm getting a "tar: Error exit delayed from previous errors" while trying to create the tarball. Anyone know what this is about?

---

### Post by frodon on 2006-03-29
Strange,

Anyway don't bother with tar if it generates too many errors, partimage do the same job in an easier way, i would have directed you to it first (my fault).
Partimage will create an image file for you, it's also on the ubuntu live cd i think, so after making your image file boot on the live cd and use partimage to restore your old ubuntu partition on your new drive.
I give you a link which explain quickly how to use partitmage (not too hard ;) ) : [http://www.partimage.org/doc/index-3.html](http://www.partimage.org/doc/index-3.html)

Hope you will solve your issue soon.

---

### Post by inha on 2006-04-15
after a couple of weeks of laziness I decided to finally go forward with this. ubuntu live didn't have partimage but knoppix has. so I used that but ran into a problem with partimage. it can't write on my second hd so I can't create the image. I tried to add write rights with chmod and change the ownership to root with chown but the permissions simply won't change. has anyone ever ran into this with partimage/knoppix? there was 1 thread at the partimage forums about this but it didn't help me at all.

---

### Post by 146lily on 2006-04-15
I downloaded the free ultimate boot cd (brilliant loads of tools, google it) from mrbass. Connecting the new hdd as a slave to the drive I wanted to clone using gn4u (if I remember right, option F7 in F2) I created a cloned hdd in 30min. This post is from a 30min. clone + 10min using Dapper in repair mode to fix grub booting. Problem is I have a spare 10gb of unallocated disc space.....how do I use it?

---

