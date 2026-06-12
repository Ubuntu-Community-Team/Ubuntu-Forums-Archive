---
title: "Can't write to External USB drive, Formatted EXT3"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by e30drift on 2008-01-11
I am in the middle of creating some VM's of Windows Server Environment.  I installed VMWare Server and got it running on my laptop.  Unfortunately I will run out of disk space and I need to move the VM images to an external USB drive.  I slapped together a 320GB hard drive with a external USB2 case.  

It installed fine and was recognized as NTFS.  I used the Partition Editor (GParted) to format it to EXT3.  It took a few minutes and it seemed to be ok.  It shows up under "Computer" as "disk" or /media/disk.  I tried to create a new folder and the right-click menu the option is greyed out.  other write functions are greyed out too.  

I attempted to take ownership of the drive:
```
sudo chmod 777 /media/disk
```
```
sudo chown user /media/disk
```
Both of those did nothing.  chmod gave me a permission error and chown didn't do anything at all.  ls -l shows that root still owns the disk...  grrr....

I tried -R switch, no go on that either...
 so, 
btw, im ive been using Ubuntu/Linux for about a week, so i'm n00b

---

### Post by maxino on 2008-01-12
What I did was to create a directory and then change the ownership to user of *that* directory.
Something like:

```
sudo mkdir /media/disk/data
```

and then

```
sudo chown max:max /media/disk/data
```

Now 'max'  is the owner of 'data' and can read/write/execute and the file manager menus are no longer greyed out.

Hope this helps

---

### Post by e30drift on 2008-01-12
Sweet!!  

It worked!  Well, I unfortunately cannot fully test it out, but I ran the commands, the folder showed up and when I right click on the folder for "properties" I was able to freely edit the permissions within the GUI!!  I can only assume that this will work without any more issues!

the "Give Thanks" is a nice feature on this forum!

---

