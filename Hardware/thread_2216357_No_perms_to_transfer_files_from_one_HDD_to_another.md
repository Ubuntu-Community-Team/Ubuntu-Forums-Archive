---
title: "No perms to transfer files from one HDD to another"
date: 2014-04-11
forum: Hardware
---

### Post by CorneliusSneed on 2014-04-11
Hi folks, XP refugee and absolute linux newb here. Basically I need to know how to remount a second HDD under something other than root  so I can transfer files to it. Details follow if you need them.



Sorry for the lengthy text, but I am trying to describe my particular situation as clearly as possible. My issue doesn't seem to me to be hardware specific, but I will gladly post hardware info if it turns out to be relevant.

 On my machine under XP I had two HDD, one 200GB I used for the OS, and an 80GB I used for document backups.  I installed Ubuntu 12.04LTS to the 80GB, using the full overwrite method. When I subsequently plugged in the 200GB with the jumper in the slave position and rebooted, it auto-mounted, and I was able to transfer all my documents from it to the 80GB using cut and paste. So far, so good.

Since I am new to linux, I decided that before I got too invested in Ubuntu, I would give Mint a try as well. I reasoned that this would also be an easy way to format the 200GB so it would work with either OS. So I installed Mint 16 KDE on the 200GB, again using the full overwrite. Again, so far, so good.

I then shut down, connected the 80GB as slave, and rebooted. The 80GB did not appear under the Mint OS, which at this point didn't seem such a big deal. But, I decided that in case I really screwed something up, my documents should be on both disks, so if I needed to reinstall one OS or the other, I would not risk losing them. This is where I hit my current wall. 

I rebooted into Ubuntu, opened both drives, and tried to copy and paste my documents from the 80GB to the 200GB. It gave me the following error "The folder "Documents" cannot be copied because you do not have permissions to create it in the destination"  I then checked the properties of the 200GB and it lists the owner as root, the group as root, and told me I am not the owner, so I can't change perms. 

I then did some checking, and found out I can log in as root in Terminal. So I did, and that did not help. So I went into User Accounts to see if I could log in as root from there. Nope.

I have since stored most of my documents online, but I have 44GB of videos I do not wish to lose, and no viable place to put them.  So I need to either remount the 200GB as something other than root, or, well, do something else to enable me to transfer files easily from one drive to the other. 

I am sure there is an easy solution to my problem, but I have now spent hours googling and am getting a bit frustrated, as most of what I have found has been for obsolete releases of the OS, and tbh, the syntax used in Terminal is largely gobbledygook to me at this point. I have found a couple "how to" guides, and copied and pasted from them into Terminal, with varied results, some nearly disastrous with system freezes, all kinds of error messages on shutdown, and so on. In any event, none of these results included success. I also installed gparted, but it only sees the 80GB.

The documents in question are currently in my Home folder in one folder named "Documents," on the 80GB drive and the 200GB HDD is listed as "196 GB Filesystem," along with what seems to be a UUID listed in the bar above. (whatever you folks call that bar in linux)  Would one of you experienced people please tell me the most expedient way to solve this, whether it be via commands within Terminal or otherwise? At this point, if the most expedient way to solve it is through Terminal, I would be eternally grateful for the exact commands; I promise I will learn the syntax on my own, once I have my machine fully operational. 

Thanks for your patience in reading such a long question. ;)

---

### Post by cjhabs on 2014-04-11
With your 200Gb drive mounted you can use:
sudo chmod 777 /mount_point
where /mount_point is the folder your 200gb drive is mounted under.
Now, even though the folder is owned by root, every one has read write access to it

---

### Post by CorneliusSneed on 2014-04-12
Okay, I am probably not understanding completely.

When I check properties for the drive it says Location:   /media

So I did this:


kelly@kelly-desktop:~$ sudo chmod 777 /media
[sudo] password for kelly: 
kelly@kelly-desktop:~$ 

It didn't seem to do anything; I still can't move files to it. It seems I must be missing a step?

---

### Post by grahammechanical on 2014-04-12
I have a separate data partition. The partition itself has these permissions: 

Owner: Root. Access: Create and Delete files. 
Group: Root. Access: Access files. 
Others: Access files. 

And I am able to save documents to folders in that partition from other installations of ubuntu. Each folder in that data partition has these permissions. 

Owner: Root. Access: Create and Delete files.
Group: Root. Access: Create and Delete files.
Others: Access: Create and Delete files.

The Ubuntu File Manager (Nautilus) will let us set the permissions for all files in a folder as well but we need to be using Nautilus with administrator or root privileges.

```
gksudo nautilus
```

We may need to install gksu to run that command sucessfully as later versions of Ubuntu do not have gksu installed by default.

```
sudo apt-get install gksu
```

When we use File Manager as administrator and we create folders, then those folders become owned by root and only root has the ability to create and delete files. So, we must change the permissions to give both the Group and Others the ability to create and delete files.

Regards.

---

### Post by CorneliusSneed on 2014-04-12
Okay, but how do I tell it which files to set permissions for? I don't yet know the proper commands and syntax to get to the second HDD within Terminal.

---

