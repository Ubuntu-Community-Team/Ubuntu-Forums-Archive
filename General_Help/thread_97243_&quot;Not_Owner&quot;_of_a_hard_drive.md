---
title: "&quot;Not Owner&quot; of a hard drive"
date: 2005-11-30
forum: General Help
---

### Post by k0ontz on 2005-11-30
Hi, 

I can't save/or edit things in the file system (in this case /var/www). It says I dont have accses privilages. After a closer look, I was not the owner of Hda1 and could not write files to it. 

How do I give myself ownership of the drive, I am the only user on this machine. I CAN save files to desktop and home directory.

Thanks in advance.

---

### Post by taurus on 2005-11-30
What kind of permission do you have for /dev/hda1?  This command will tell you

more /etc/fstab

---

### Post by k0ontz on 2005-11-30
Well, im not on the Ubuntu machie, but from the GUI tool, it said I had

Owner: Read, Write and the third 
Group: Read, and the third one
User (I think): Read and the third one.

Sorry, i can't accsess the Ubuntu machine right now, so im working of memory. I hope that helped.

---

### Post by aysiu on 2005-11-30
The /var directory is owned by root and cannot be written to by the user.

You have two options:

1. Change ownership of the directory, using the *chown* command ```
sudo chown -R yourusername:yourusergroupname /var/www
```

2. Open your /home directory. Then Run (Alt-F2) the command ```
gksudo nautilus
``` and open up /var/www. Create a directory in your /home directory (say, /home/www) that you middle-click-drag to /var/www and select "link here."

I prefer the latter option, but it's your choice.

---

### Post by thegnark on 2005-11-30
**don't do the stuff in *italics* yet. read the longer paragraph before you do anything**

[I]you should be able to `sudo chown -R user:group /`

alternatevely (and probably better) would be to modify fstab to reflect the correct owner.[/I]

i think the problem is much simpler than all this though. for most places (pretty much anywere outside of your home directory) you need to use sudo ("superuser do"). for example, if i wanted to copy a file, foo.txt to /var/www, i would type this: `sudo cp ~/foo.txt /var/www`. it's like gaining temporary root access. give it a shot and see how it works out

p.s. the permission options are like this: rwx (read, write, execute)

---

### Post by taurus on 2005-11-30
I want to see how you mount your /dev/hda1, not a file's permission...

---

### Post by k0ontz on 2005-11-30
Thanks alot, aysiu and thegnark

I'll try linking it to my home directory, and what is the "fstab"?

---

### Post by Svictor on 2005-11-30
As far as I know, you are not supposed to have write access to your the system folders. This is part of the Unix security model and even though it may seem restrictive at first, you shouldn't modify it. One of the security aspects is that if something goes wrong in a program your user runs, it can not modify files or folders that are important for the system. This is one of the reasons why Linux avoids some nasty viruses for example.

So normally, you should have write access to none of the folders in the root directory, apart from /tmp (which is writable by everyone ; but erased on system restart) and /home/yourusername + the directories beyond it. Sometimes, you also have automatic write acces to the folders in the /mnt directory. In no case should your user be the owner of the whole drive where your system is : this would allow any program your run to do virtually anything on it.

You still can maintain your system with sudo.

Fstab is the file that tells your system where and how to mount the filesystems. You can get an overview here : 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by hw-tph on 2005-11-30
A sane way of managing access is through groups. You can create a new group to have write access to selected parts of /var/www (say, a directory for a specific virtual host), and add users to that group. Also set the sticky bit on the directory. This is what groups are for - to manage read/write access to different files (or devices - hey, even devices are files in the *nix world!).


Håkan

---

### Post by U5tabil on 2006-09-23
Is there any opertunity to make a write access to all files under a folder with one command? its a paintaking process if im going to set write on all my files....

---

### Post by hw-tph on 2006-09-24
> **U5tabil said:**
> Is there any opertunity to make a write access to all files under a folder with one command? its a paintaking process if im going to set write on all my files....

**sudo chmod -R ${mode} /path/to/directory**

Replace ${mode} with the mode you want to use, ie g+rw.

---

