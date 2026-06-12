---
title: "unable to mount floppy after install"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by towner on 2005-01-22
Hi all, hope this isn't a stoopid question

Just installed ubuntu on a friend's computer. Everything went fine and he's happy but when we try to mount a fat formatted floppy we get the message that we 'must specify a filesystem type'. 
OK so we do specify the filesystem , still no joy.
so apt-get and reinstalled dosfstools, thinking that a FAT partition cannot be properly accessed, but same old story

here is floppy specific line in /etc/fstab

/dev/fd0       /media/floppy0  auto    rw,user,noauto  0       0


am I missing something?

---

### Post by towner on 2005-01-24
missing floppy update

managed to solve the problem, so I'm posting what I did just incase anybody else has the same issue :-D 

looked at /dev and noticed that the special block device file /dev/fd0 was missing from this install! made a new device with the commands:-

cd /dev
sudo mknod fd0 b 2 0

then changed the permissions of the file the easy way
sudo nautilus /dev

and right click on fd0, Properties, Permissions..and checked the radio buttons

I hope that this helps anyone else with the same problem

---

