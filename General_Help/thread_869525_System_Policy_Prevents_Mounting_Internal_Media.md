---
title: "System Policy Prevents Mounting Internal Media"
date: 2008-07-24
forum: General Help
---

### Post by wmgcf on 2008-07-24
I have seen over 20 similar posts, but none were close enough to my problem, so here is my first question:

first, I am using Ubuntu 8.04

I have an internal fat32 partition. when I log in as myself the partition is automatically mounted with full read and write permissions.

Unfortunately, my other users are not able to mount it. When the other users try to mount it they get a dialog box that says: "System Policy Prevents Mounting Internal Media" The dialog box asks them to authenticate and lists my id as the only user they may authenticate with.

I need a simple way to change this so that all users have automatic access to this partition. I already used the "users and groups" to experiment by giving one of the users admin rights - that did work, but I don't want to extend admin rights - only auto mount, with read and right to a partition.

I am very comfortable using the terminal, I just need to know what commands to use, etc.

---

### Post by iaculallad on 2008-07-24
Had you tried:

```
sudo chmod 777 /mountpoint/mountname
```

---

### Post by wmgcf on 2008-07-26
thanks for offering a tip, it didn't work- probably because I don't know enough. I tried to run the command under my wife's ID - it asked for her sudo password, put it in and I got a message saying something like "this incident will be reported". neat.

I actually fixed the problem another way, for now. All I did was use the graphical box to authenticate each user. I also found and made some adjustments under system=>authorizations. The combination of the two makes it so the other users now have complete access to the fat32 partition.

For now, this is what I need because we have dual boot machine and i am weaning us off of XP. When we are ready to trash windows I'll backup and make some adjustments to the partitions- bye bye vfat

i am very pleased that ubuntu security is so tight and there are so many configuration options. One of my complaints about windows is that the "users" functionality never worked correctly, - for example changes on one users desktop could affect others- and that it was so difficult to lock things down.

another point for ubuntu - here's the score:

ubuntu 999
microsoft -323

---

### Post by mc4man on 2008-07-26
Try going to system -> admin -> authorizations -> storage -> mount file systems from internal drives. You normally should be able to grant another user authorization under the Explicit section

edit: missed you did that in post - should read more carefully, imo that is the proper way to address want you wanted.

---

