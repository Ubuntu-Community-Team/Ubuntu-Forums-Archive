---
title: "Hard Drive will not mount where I attempt to mount it at."
date: 2015-03-13
forum: Hardware
---

### Post by anthony54 on 2015-03-13
Evening all,

Have a perplexing problem, I installed Kubuntu couple of nights ago, got the machine up and running just fine. When I initially installed the system I only had 2 drives in it; one for the swap and system and one for my home.  Last night (and continued today) I added another drive that I store my movies on. The system booted just fine and showed the new drive under the file manager, I can access it manipulate it and so on.  I want to make it a "permanent" directory under my home (/home/anthony/Videos/***Movies***), when I was using another flavor of linux to do this I would run an application called partition manager. I would select the drive, tell it where I wanted to mount it, accept the changes and it would work.

I attempted to do the same last night (and again today) using several different methods: "disks", "gparted", "KDE partition manager", even manually entering it in "fstab". After I reboot the machine though, the system stops during boot and displays a message (can't remember exactly what) about not being able to mount the drive now "press s to skip, m to manually mount". Well I press s - nothing, I press m - nothing, I wait for 15 minutes - the machines just hangs. So I reboot into safe mode, and now I can press s to skip, when I get to the desktop if I run any of the above utilities and remove my mount point and reboot, then I can mount the drive as I could from the start.

Funny thing is, about a week ago when I first moved to *buntu, I tried Ubuntu first and did the same thing (adding the drive after install) and it worked just fine using the "disks" program, so I am not sure what the difference is here that might be causing it.

If anyone has any suggestions, it would be very much appreciated.

---

### Post by sotiris2 on 2015-03-13
Please post the output of the following commands. Run them one at a time. ```
blkid
cat /etc/fstab
```

---

### Post by anthony54 on 2015-03-13
blkid:

/dev/sda1: UUID="673e462f-7b57-444a-a9e8-d4a67d9da7c1" TYPE="swap" PARTUUID="000dd0c6-01" 
/dev/sda2:  UUID="56e81253-92f0-4933-a081-7b309d057801"  UUID_SUB="6b93fe75-ae57-4c8e-9172-4de76d1422df" TYPE="btrfs"  PARTUUID="000dd0c6-02" 
/dev/sdb1: UUID="b8fe36e2-1bc6-48e9-bff2-6144512224ea" TYPE="xfs" PARTUUID="00092144-01" 
/dev/sdc1: UUID="b092ee4b-2b2f-432a-a0f9-253e92a655f8" TYPE="xfs" PARTUUID="161cea66-01"

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sda2 during installation
UUID=56e81253-92f0-4933-a081-7b309d057801 /               btrfs   defaults,subvol=@ 0       1

# /home was on /dev/sdb1 during installation
UUID=b092ee4b-2b2f-432a-a0f9-253e92a655f8 /home           xfs     defaults        0       2

# swap was on /dev/sda1 during installation
UUID=673e462f-7b57-444a-a9e8-d4a67d9da7c1 swap            swap    defaults        0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by sotiris2 on 2015-03-13
So apparently your system uses btrfs and xfs which I am not the most familiar with. 

Which reminds me, did you select your system to be encrypted? Or maybe your home folder to be encrypted? Maybe these could create a problem in the sense that mounts happen before login but if you checked home folder encryption, it gets decrypted AFTER you login. So maybe it can't mount because your Video folder doesn't exist before you login. It also can't mount it if you don't actually have an actual Movies folder inside your Videos folder, so maybe its actually a simpler problem.

So I will show you what to add to fstab which would work in non-encrypted install. If you try it and it doesn't work or you are confident that you tried it correctly we will make a script to mount it and have it run just after you login. 

So fstab ```
UUID=b8fe36e2-1bc6-48e9-bff2-6144512224ea /home/anthony/Videos/Movies xfs defaults 0 2[code]

I assumed b8fe36... is the correct uuid for the new drive since it's the only one not already used in fstab. Remember the folder Movies must already exist. 


If this does not work for any reason we can try the following. Open gedit and paste in the following[code]#!/bin/bash
mount -U b8fe36e2-1bc6-48e9-bff2-6144512224ea /home/anthony/Videos/Movies
``` Save it somewhere safe say your home folder with name mount.sh
Run ```
chmod +x ~/mount.sh
``` ~ is short for your home folder, adjust the command if you save somewhere else or check the 'Allow Executing File as Program' in right click -> properties. 

Then search in dash for startup applications and open it up. Hit add and use browse to select our file (or put it's path directly if you want) give it whatever name you want. Make sure it's enabled after adding it ( it has a check in it's box).

---

### Post by anthony54 on 2015-03-13
You would be correct about the home folder being encrypted. Funny, in the back of my mind I had a hunch that might be causing the problem. Don't need the excryption, just thought I might give it a try to see what it's all about. I have already tried to place the drive in fstab via the UUID (you are correct that is the UUID of the movies drive), and it still failed. I like the idea of the script file, although just doing some cursory research about an encrypted home it apparently causes more issues than it might be worth.

I am going to see if I cannot find "how to un-encrypt your home folder".

---

### Post by QIII on 2015-03-13
You might be able to save some time by just creating a new directory under /mnt and mounting the share there.

---

### Post by SeijiSensei on 2015-03-14
Mount the drive to /media/Movies.  You can then link to that in a user's home directory.
```

sudo mkdir /media/Movies
sudo mount /dev/sdc1 /media/Movies
cd ~ 
ln -s /media/Movies

```
If you are using XFS, you should connect this box to an uninterruptible power supply if you have not done so already.  I experimented with XFS but dropped it when I discovered how vulnerable it is to power outages.  I just use ext4 for everything these days without any problems.

---

