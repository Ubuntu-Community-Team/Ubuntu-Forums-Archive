---
title: "[SOLVED] Unable to use Newly Created Partitions"
date: 2008-10-03
forum: General Help
---

### Post by ft23002 on 2008-10-03
Hello,

Decided to give ubuntu another look and so far very pleased with it. With compiz fusion, emerald, and screenlets all set up, and all loading on start, I'm lov'n ubuntu even more. Have found this forum to be a great help & for all those participating and offering help, a Big Thanks from this newbie. I been using the search with good success, however couldn't find anything about this.

Running ubuntu 8.04 on a Dell E1505 laptop on a 20 gig internal desktop drive connected via a ata/sata to USB adapter. For now, have the laptops internal drive removed.

Ubuntu was installed on its own 8 gig ext3 partition with (I believe) grub installed on this partition (mount point- /). The other partition created at the time of install was a 2 gig swap (little excessive and may reduce to 1 gig as it appears to never get used).

Using GParted and with the remaining estimated 9 gig's on the drive, have created an extended partition (/dev/sda3). On the ext. part., created 2 logical partitions:
1- 3 gig. - ext2 - mount point- "media/disk"   (no flag) /dev/sda5
1- 6 gig. - ext3 - mount point- "media/disk-1" (no flag) /dev/sda6

When both are mounted, I'm unable to anthing with them. Cannot create new folders, move files to them, nothing. In: /media, I see the 2 folders; disk, disk-1, and when right-clicked and choose properties, under tab "permissions" the owner is "root" and everything is greyed out and states "You are not the owner, so you can't change these permissions". Wish to use them as general backup/storage and access them directly threw places/computer/(partition). Also, they will not be shared, networked, or would need to be accessed via any other OS.

Questions:

1. How can I use these partitions as I am unable to anything with them?
2. Should they remain as owner "root" for security reasons?
3. Do partitions always need to be mounted to via a folder, unlike a drive letter like with M$?
Since theres nothing on them, they could be deleted and I could start over if need be. 

Thanks in advance for the help :)

[ATTACH]87169[/ATTACH]

---

### Post by vanadium on 2008-10-03
Only the root user can change ownership and permissions. To load a nautilus instance with root privileges, press Alt+F2 then type "gksudo nautilus" then enter. Do what you need to do as root (be sure you know what you do), then close that instance as soon as you are done.

Partitions are always mounted in the folder structure, and believe me, that is way more uniform and consistent than the drive letter approach, that stems from the time where we had floppy a and floppy b in our computer.

The real power of Linux comes with links. You should create links under your home directory for easy access to your data on other partitions.

---

### Post by ft23002 on 2008-10-03
Why is the user who created the partitions unable to use them? 

It seems strange that user created partitions cannot be used by the user who created them without doing advance and somewhat critical permission changes that could easily allow the wrong access.

Don't want to set a "bad" permission, so could someone please let me know what to change to allow only myself full access and use?

Is this what everyone has to do to use newly created partitions?

---

### Post by jerome1232 on 2008-10-03
You can do it two ways:

First the gui way, press alt+f2
type 'gksudo nautilus' hit enter
browse to /media, right click the folder, change the owner and group to your user name, click apply to enclosed files, then close the window, then close that nautilus window. Now you should now be able to create/delete files in there, only you can since you are the owner.

now the cli way:
```
sudo chown -R $USER:$USER /media/disk
sudo chown -R $USER:$USER /media/disk-1
```

---

### Post by vanadium on 2008-10-03
In linux, it is the root user who installs the system and determines what other users may do. No normal user is allowed to create partitions (that is relaxed with removable drives, though).

To give yourself full permissions 1) make yourself owner of the directory (or file) 2) make sure all all permissions for the user are set. To restrict use by groups and others, turn off the corresponding permissions: write to disable write access, and add read and execute to prefent groups and others to navigate through your directories and see their contents.

---

### Post by ft23002 on 2008-10-03
Thanks for the help. Did it the terminal way, then went to "disk" permissions tab and can see the changes made and can change permissions as I am now the owner. :)

Did try it the other way as vanadium posted and it worked too. -Thanks

Last questions about options in the permissions tab;
What does "group" permissions define? There is currently only one user, is it if theres 2 or more users, they can be assigned to a group and thus use the same permisssions?
Does the system or root fall under any of these permissions or does it always have access?

Thanks again for the help, as with anything new, theres a learning curve. Was thrown off by having to do it with a newly created partition. Its definitly a lot easier than Vista's pos method for folder perrmissions... Errggg, now thats a headache!

---

### Post by jerome1232 on 2008-10-03
Group permisions are nice. I'll give an example of how I use them

I have a partition mounted as /mnt/data it's ownership is root:data rwxrwx--- (so owner is root, group is data, onwer has read/write, group has read/write, others have nothing)

Every user that I want to be able to read/write to that partition I add to the group data and viola, anyone in the data group can read/write there.

---

### Post by ft23002 on 2008-10-03
After my last post I clicked on its drop down and noticed it options. They weren't what I expected, but your post makes sense of them. So as long as a user belongs to a group, any dir with read/write permissions for a defined group will allow that user full access, and not others who do not belong to that group... Cool.
After changing permissions of the "disk" DIR, I created 2 folders, then went back and changed permissions of "disk" DIR back to the defaults root (owner&group). Not sure if it matters, but this way I only have use of the 2 DIR I created in the disk DIR. Can do anything within those DIR's as I'm' the owner of them, but not the parent dir's (media & disk).

Found another way to this as well:

sudo mkdir /media/disk/(newdir)

Then do:
 
sudo chown -R $USER:$USER /media/disk/(newdir)

This way one never has to change the permissions of the parent dir.

Then to delete a dir in root parent dir...

sudo rmdir media/disk/(newdir)

Lots to learn and having fun doing it.
Next- moving the home dir to its own partition. Yikes! Going to backup it up first to cd.
Is there an elevated copy command to make sure it backs up ALL dirs/files in the home dir? Noticed a lot of dir's are hidden.

Thanks for the help

---

