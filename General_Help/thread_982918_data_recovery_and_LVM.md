---
title: "data recovery and LVM"
date: 2008-11-15
forum: General Help
---

### Post by mauhiz on 2008-11-15
Hello there,

I used to have an array of two disks grouped with LVM2 :
- my /
- my /home

But recently my disk holding my / died. I would like to salvage my data on /home, but from the outside the disk is not ext2, but LINUX_LVM (as one would expect).

Do you know of any method enabling me to recover my data on that disk? I already tried mouting disk as ext2 anyways (which seems pointless to me afterwards), but it failed.

---

### Post by pofigster on 2008-11-15
Ok, first thing you need to do is download an "Alternate" Ubuntu CD and burn it to a disk.
Then, boot from the CD and enter "Rescue Broken System" (it's an option in the menu).
Tell it you want to open a shell inside the system - this will bring up a Command Line Interface that lets you access your system.  It should also prompt you for the password/key to unlock your drives at this point.
Once you are inside you're going to need to have another hard drive where you can copy the data.  Mount it (either internal or external, doesn't matter).

Then, it's a simple matter of EITHER using cp or making a .tar of your /home directory and copying the .tar.

I had a very similar thing happen to me a couple months ago (I don't use LVM anymore).  I prefered the .tar option because the drive I was copying to couldn't handle some of the file names I had and the .tar preserved directory structure.

THINGS TO REMEMBER
Your encrypted hard drive is under /dev/mapper/sdXY_crypt (at least, that's where mine was) where X is the drive and Y is the partition.

If you have any other questions, and you don't get a response on the thread, go ahead and PM me.

---

### Post by mauhiz on 2008-11-15
Thank you for your reply. I have currently no CDROM drive on this machine, so I tried with a pendrive installation of ubuntu-8.10-alternate.

The shell launches fine, but I have no 'mapper' directory in my /dev; but I have there my drive (sdb) and its 1st partition (sdb1).
Maybe the mapper module is not loaded?

Also, you said your drive was encrypted. Is this a default feature of LVM2 ? Otherwise I don't think mine would, since I never enabled this kind of option (and never provided it any password too).

---

### Post by pofigster on 2008-11-15
Oh...your LVM isn't encrypted?  I guess I didn't realize LVM could be used in a non-encrypted state.

Still, from the shell can you access your /home directory?  In whatever drive/partition it's in?  If you can, you ought to be able to mount another drive and copy all the files over.

---

### Post by mauhiz on 2008-11-15
No, I cannot access my partition, because mount fails. It won't recognize the partition type. This is actually the root of my problem.

I thought of 2 solutions
- ignore somehow LVM headers and manage a mount. Mount disagreed :)
- recreate a LVM environment (set up another ubuntu working, install LVM, and import volume group). It fails beacuse there is a volume missing in the group (my dead disk)

---

### Post by pofigster on 2008-11-15
I'm really sorry - I'm out of ideas then :(

Hopefully this post will bump your thread up to get more attention.

---

### Post by _sAm_ on 2008-11-29
LVM stores the data spread on the disks; "*In an LVM, there is no organization to where your data* ".
From: [http://groups.google.com/group/linux.redhat/browse_thread/thread/4c7b29019d33437b](http://groups.google.com/group/linux.redhat/browse_thread/thread/4c7b29019d33437b)

To be able to restore a LVM(without any raid), you need to have used the tool called "**vgcfgbackup**", then some of the data can be restored. 
From: [http://kbase.redhat.com/faq/docs/DOC-3335](http://kbase.redhat.com/faq/docs/DOC-3335)

If you want to group your disk without this downside try **mhddfs**. It is not so fast as LVM but if a disk gos down you can use the data on the other disk as normal(and the data is not spread). Its also easy to use.

I hope you had backup of your files.

---

