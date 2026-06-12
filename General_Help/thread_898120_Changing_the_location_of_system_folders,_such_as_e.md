---
title: "Changing the location of system folders, such as /etc, /bin, /sbin..."
date: 2008-08-22
forum: General Help
---

### Post by rickdane on 2008-08-22
I need to change the location of my system files to put them within another folder, for example I would create a folder called "system" and place all folders possible such as /etc, /sbin, /bin and so on into this folder with only the folders absolutely necessary for the initial system boot-up placed in the regular / directory. (The reason I am doing this is for the Amazon Ec2 EBS storage).

I am wondering if anyone can tell me how I can specify the new location of the folders so the system knows to look there instead of the old / directory.

Thanks

---

### Post by yabbadabbadont on 2008-08-22
You can't.  Give it up as a lost cause.

---

### Post by xeth_delta on 2008-08-22
Not exactly on topic, but you can have a look here on how the file system hierarchy is organized in Linux and the rationale: [http://www.pathname.com/fhs/pub/fhs-2.3.html#INTRODUCTION](http://www.pathname.com/fhs/pub/fhs-2.3.html#INTRODUCTION) and [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by rickdane on 2008-08-22
> **yabbadabbadont said:**
> You can't.  Give it up as a lost cause.

Yes you can, I know for a fact you can, please find somewhere else to troll

---

### Post by yabbadabbadont on 2008-08-22
The only possible way to do it, would require a separate /boot partition and a custom initrd that would chroot into the sub-directory you created.  Not something to be attempted lightly.

---

### Post by rickdane on 2008-08-22
[http://linux.die.net/man/2/chroot](http://linux.die.net/man/2/chroot) I found this, so I am beginning to see how to do it, I know its not something that is going to be simple but it is very important to what I am trying to do.

---

### Post by rickdane on 2008-08-23
In order to do this, so far I have gathered that something like this may work (replacing the original /sbin/init file with a shell script containing the code below):

mount /dev/sdi /real_root
cd /real_root
pivot_root . old_root
exec chroot . /sbin/init
/sbin/init

I have tried this but I lose the machine (instance), so far I have been unable to figure out what is going wrong, I would appreciate if anyone has any advice.

---

### Post by LateNiteTV on 2008-08-23
if you MOVE them, you will break your system. you can copy them to a different location, though, without damaging anything. do NOT move them.

---

### Post by cariboo on 2008-08-23
The linux operating system depends on having files where it can find them, they are hard coded links. It would be the equivalent to movint the Windows and Program Files directories in a directroy called System  and then expect it to work.

A better alternative would be to use a backup program and create an archive file of your system.

Jim

---

### Post by rickdane on 2008-08-23
I have copied them, not moved them.. I know that this is possible to do.. if you look at:

[http://linux.die.net/man/8/pivot_root](http://linux.die.net/man/8/pivot_root)
[http://www.ss64.com/bash/chroot.html](http://www.ss64.com/bash/chroot.html)

Basically the root directory has to be changed right after boot which is why I have changed the /sbin/init file to a shell script running the code from what I posted above. This is absolutely critical to what I am trying to do with Amazon EBS.

---

