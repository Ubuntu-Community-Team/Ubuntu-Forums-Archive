---
title: "Partition Permission?"
date: 2008-09-30
forum: General Help
---

### Post by mickeyd1965 on 2008-09-30
Hi,
I have just created partition and tried to save a file to it and found out that i don't have permission. The mount point is "media/Data Partition " . This command line stuff totally confuses me. Can somebody please help me?

mickeyd1965

---

### Post by glotz on 2008-09-30
Howdy! Do a **sudo chown -R yourusername:yourusername /media/Data Partition**

sudo (super user do) command means you want to do the following command with super user privileges; you'll be prompted for the password

chown (change owner) command means you wish to change the ownership parameters of some files

The -R (must be a capital r) parameter tells the chown command to work recursively, i.e. to work on all files and folders under the specified target

the yourusername:yourusername part is your username and groupname. (By default the user belongs to a group with the same name. Obviously yourusername should be substituted with your user name. If you forgot it, you can always do **whoami** :))

and finally, there's the target to work on (/media/Data Partition)

I suggest you do a **man chown** to see the syntax of the command. (Man is short for manual page.) Any help?

---

### Post by mickeyd1965 on 2008-09-30
Thanks Glotz,
I'll give it sa try.

mickeyd1965

---

### Post by scouser73 on 2008-10-01
You should use **gksudo nautilus** in the terminal to change permissions really.

---

### Post by vanadium on 2008-10-01
By the way, there is an "Absolute Beginners Forum" here, where you will get more chances of getting step-by-step help.

---

