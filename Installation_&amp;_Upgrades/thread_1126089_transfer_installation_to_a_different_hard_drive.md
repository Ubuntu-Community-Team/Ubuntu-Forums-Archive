---
title: "transfer installation to a different hard drive"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by fahadayaz on 2009-04-15
I have bought a new hard drive and want to be able to run my Jaunty installation from here. Is it possible to just copy the partition to the new hard drive and install grub on it?

Or will i have to install Ubuntu from scratch?

---

### Post by Svensk023 on 2009-04-15
it is possible to clone your installation over, but I would just backup all the files you want and do a fresh install on your new HDD

otherwise we will have to set you up with some software, and do some work on the command line which can result in some serious data loss if you blip up on your input.

---

### Post by vlovich on 2009-04-15
you could use sudo dd if=/dev/sda of=/dev/sdb where sda is your old drive & sdb is your new drive.  You'll have to resize the partitions afterwards  if your new drive is bigger.  If it's smaller, DO NOT DO THIS.

[http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/]("http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/") gives more detail if you want to copy specific partitions only.

Optionally, you could create the partitions on the second drive & do

sudo tar c / | sudo tar x -C /media/my_new_partition  (the sudo is important here to do a proper backup, even if you don't strictly need root permissions - the man pages explain what options get enabled when tar is run as root).

With this method though, you'll need to to a grub-install on the new drive to create its MBR.

---

### Post by fahadayaz on 2009-04-15
my main reason for wanting to do this is to preserve the apps i have installed. sometimes I install things things in /usr or /opt 

i might forget about an individual app i may have installed or its config or whatever... so i was just wondering would it not be possible to copy the whole thing over just like that... if all the folders are on the same partition neway, which they are.... lol hmmm hope that makes sense  :D

---

