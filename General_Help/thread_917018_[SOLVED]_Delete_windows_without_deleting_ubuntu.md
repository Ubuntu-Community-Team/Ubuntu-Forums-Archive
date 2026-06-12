---
title: "[SOLVED] Delete windows without deleting ubuntu"
date: 2008-09-11
forum: General Help
---

### Post by Eremis on 2008-09-11
Hi, 

I was just wondering how to do delete Windows without deleting your Ubuntu. And then making your Ubuntu partion bigger? 

Please reply, thanks

---

### Post by zohaib on 2008-09-11
start ubuntu go into the drive where windows is located n directly delete the folders of windows. this will destroy windows.

---

### Post by oilchangeguy on 2008-09-11
> **zohaib said:**
> start ubuntu go into the drive where windows is located n directly delete the folders of windows. this will destroy windows.

the op did not ask how to "destroy" windows. the op asked how to delete it. simply run the partiton manager from the live cd. and delete the windows partition. the resize the ubuntu partition to take over the unallocated space.

---

### Post by hwttdz on 2008-09-11
Caution: do not try this until someone confirms you can do this to a partition that is currently in use.  

If you don't have your live cd handy you can also do this through gparted in your existing ubuntu installation.  You can get gparted through synaptic.  And then I think it appears under system -> partition manager.

---

### Post by oilchangeguy on 2008-09-11
> **hwttdz said:**
> Caution: do not try this until someone confirms you can do this to a partition that is currently in use.  

If you don't have your live cd handy you can also do this through gparted in your existing ubuntu installation.  You can get gparted through synaptic.  And then I think it appears under system -> partition manager.

no, you can't do it to a partiton in use. there will be a lock icon there. if the computer is being run from the live cd, there is nothing on the hard drive in use.

---

### Post by Therion on 2008-09-11
Personally I find [GParted](http://gparted.sourceforge.net/screenshots.php) easier to use if only for the GUI.  Just at thought.

@the OP:  **oilchange** is correct.  You MUST use a LiveCD or DVD to remove and/or resize partitions.

---

### Post by kokkus on 2008-09-11
Go to windows and in the command line u write Format C:
This will format the partision and completly clean windows away.

---

### Post by oilchangeguy on 2008-09-11
> **kokkus said:**
> Go to windows and in the command line u write Format C:
This will format the partision and completly clean windows away.

Please spell all words. u is not a word. And what's a partision? Do you mean partition? And you can't do this from within windows. It can be done using a windows cd. But why waste time, when both operations (delete the partition, and resize the other partition) can be done with the ubuntu live cd.

---

### Post by Eremis on 2008-09-11
Thanks for all replies, i just used the live CD, and it worked.

Now I am Windows free!!! :)

---

### Post by Bart_D on 2008-09-11
Which one had you installed first...Ubuntu or Windows?

When deleting Windows, would the procedure of deletion depend on which one was installed first?

---

### Post by oilchangeguy on 2008-09-11
> **Bart_D said:**
> Which one had you installed first...Ubuntu or Windows?

When deleting Windows, would the procedure of deletion depend on which one was installed first?

no, not if you're using the live cd.

---

### Post by kokkus on 2008-09-11
> **oilchangeguy said:**
> Please spell all words. u is not a word. 
This really bothers you, does not it?

Well, I am glad u problem is solved Eremis :)

---

### Post by oilchangeguy on 2008-09-11
> **kokkus said:**
> This really bothers you, does not it?

Well, I am glad u problem is solved Eremis :)

no it doesn't bother me. but your post shows how immature you are. and there are many users in here whose first language is not english. and therefore may not understand the use of silly slang. this is a forum, not a chat room.

---

### Post by kokkus on 2008-09-11
> **oilchangeguy said:**
> no it doesn't bother me. but your post shows how immature you are. and there are many users in here whose first language is not english. and therefore may not understand the use of silly slang. this is a forum, not a chat room.
immature yes :D
Or maybe not.

But I do see your point with "silly slang". I do understand that it could be hard for someone to see what people mean when they write like that.
But it's easy too hehe:)
But ok I got your point.

---

### Post by Therion on 2008-09-11
> **Bart_D said:**
> When deleting Windows, would the procedure of deletion depend on which one was installed first?
You don't "delete" an operating system.  You have to reformat the partition it resides on.  This being the case, no, it does not matter in what order the OS'es were installed.  Again, you can't delete an OS like an application; you have to "wipe" the drive; either with a reformat or a re-installation - which pretty much means a reformatting if not a re-partitioning.  

You can't partition a drive that is in use, that's why you need to use a bootable (Live) CD or DVD.

---

### Post by oilchangeguy on 2008-09-11
> **Therion said:**
> You don't "delete" an operating system.  You have to reformat the partition it resides on.  This being the case, no, it does not matter in what order the OS'es were installed.  Again, you can't delete an OS like an application; you have to "wipe" the drive; either with a reformat or a re-installation - which pretty much means a reformatting if not a re-partitioning.  

You can't partition a drive that is in use, that's why you need to use a bootable (Live) CD or DVD.

if you use the live cd to delete the partition that the operating system is on. you then delete the operating system. and no need to format anything, if a user is going to simply expand another partition to use the unallocated space.

---

### Post by Bart_D on 2008-09-12
> **Therion said:**
> You don't "delete" an operating system.  You have to reformat the partition it resides on.  This being the case, no, it does not matter in what order the OS'es were installed.  Again, you can't delete an OS like an application; you have to **"wipe" the drive; either with a reformat or a re-installation** - which pretty much means a reformatting if not a re-partitioning.  

You can't partition a drive that is in use, that's why you need to use a bootable (Live) CD or DVD.

Say Windows was installed and THEN Ubuntu was installed to get dual booting.  Now, if (from a LIVECD...Gparted) the Ubuntu partition was formatted/deleted(so as to create empty space), **wouldn't that mess up GRUB?  Would GRUB have to be restored for the user to be able to boot into Windows?**

---

### Post by oilchangeguy on 2008-09-12
> **Bart_D said:**
> Say Windows was installed and THEN Ubuntu was installed to get dual booting.  Now, if (from a LIVECD...Gparted) the Ubuntu partition was formatted/deleted(so as to create empty space), **wouldn't that mess up GRUB?  Would GRUB have to be restored for the user to be able to boot into Windows?**

no, you'll need to use your windows cd to restore the master boot record.

---

### Post by Therion on 2008-09-12
.

---

