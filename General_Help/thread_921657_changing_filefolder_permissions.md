---
title: "changing file/folder permissions??"
date: 2008-09-16
forum: General Help
---

### Post by serendipity576 on 2008-09-16
Hi everyone,
  Sorry I'm still using Feisty but I didn't want to upgrade because it took so long to get my wireless working.  I am having problems accessing a partition of my harddisk in which windows is on.  I can get into it and read files, however it will not let me edit/add/write to those files whether it be pictures, OO documents, or whatever.  When I try to change permissions under properties it just says I'm not the owner.  How do I change the permissions for these files?  Thanks for any help, and let me know if I need to clarify anything.

---

### Post by qstraza on 2008-09-16
Well make sure that you mounted your partition as read&write.
Than copy file as root (use sudo cp...).

---

### Post by aomlives on 2008-09-16
To take ownership of a directory and all of its contents, recursively:
     
```
sudo chown -R username /path to directory
```Taken from [this]("http://ubuntuforums.org/showthread.php?t=445213") thread.

---

### Post by serendipity576 on 2008-09-16
ok dumb question, how do I mount the partition that I want to access?

---

### Post by aomlives on 2008-09-16
There's an excellent guide for this here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by serendipity576 on 2008-09-16
ok I've got the partition mounted.  It is under /media/disk/My Documents.  But I can also get to it by going to computer=>"48.8 GB Volume: disk"=>Documents and Settings=>(myname)=>My Documents.   So there's two ways to get to this folder it seems like, or are there two different copies?  So as you can tell this is just the Windows partition mounted and I'm just needing to write to a few files like openoffice and also wanting to move around pictures on and off the partition.  
   I've tried the chown  and chmod but maybe I'm doing it wrong.  Everytime I go into permissions tab it just says I am not the owner.


Thanks

---

### Post by aomlives on 2008-09-16
You can install a tool called "ntfs-config" to automount ntfs drives and enable read/write access:

```
sudo apt-get install ntfs-config
```

---

### Post by serendipity576 on 2008-09-16
ok thanks I added the ntfs config utility and that is going to help with my external which is NTFS.  However, when I try to change permissions on the previously mentioned 'disk' it still says I am not the owner.  Any suggestions?  It seems like there's gotta be a way to change those permissions to where I can read/write/delete/do whatever with all those files that are on the Windows partition.
oh and when I try the chown command it tells me that the file system is read only.  Is there a way to write to NTFS?

---

### Post by aomlives on 2008-09-17
Sorry, I forgot Feisty doesn't have ntfs read/write support by default. To enable it, you have to install ntfs-3g.

```
sudo apt-get install ntfs-3g
```Then edit your fstab file, so that the entry for your "disk" looks like this, assuming for example that /dev/sda1 is your "disk".

```

/dev/sda1 /media/disk/My Documents ntfs-3g* other options*
```I'm not sure actually whether you mounted the partition in /media/disk or /media/disk/My Documents. Because you say:

> **serendipity576 said:**
> But I can also get to it by going to computer=>"48.8 GB Volume: disk"=>Documents and Settings=>(myname)=>My Documents.   So there's two ways to get to this folder it seems like, or are there two different copies?

You can mount a partition in whatever directory you want/create in the /media folder (any partition mounted here will show up automagically in "Computer"). However, I'm guessing you maybe created a folder "disk", and then a subfolder "My Documents", where you mounted your partition. But it's still the root contents from your default Windows drive that's mounted there, so if you go to "Documents and Settings -> *username *-> My Documents" you open your default Windows userfolder My Documents, which has nothing to do with the name you gave to the partition mount point. Am I making any sense? :) I could be completely confused/wrong here...

Anyway you should be able to write to it at least. Hope this helped.

---

