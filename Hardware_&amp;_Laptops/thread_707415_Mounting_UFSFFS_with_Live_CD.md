---
title: "Mounting UFS/FFS with Live CD"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by TekNullOG on 2008-02-25
I need to remove about 60GB of data from a FreeBSD machine onto a Windows Server 2003 box. It was configured for a very specific network and after hours of trying to get it to connect to my own network, I decided I would try to mount it in Windows using this drive: [http://ffsdrv.sourceforge.net/](http://ffsdrv.sourceforge.net/)

A few blue screens later in Windows, I decided that I would stop trying this method.

I then thought that using an Ubuntu Live CD would maybe work but GParted doesn't recognize the filesytem. I tried to mount it manually using a tip from the Ubuntuforums. The command was:

> sudo mount -t ufs /dev/sdc1 -o ro /media/unix

This seems to have worked but Ubuntu is unable to display contents of folder. When I do an ls -l , I replies "ls: reading directory .: Input/output error"

- Is it possible to get Ubuntu to mount an FFS/UFS filesystem? If so, how?
- If not, how do you suggest transferring the data to the NTFS drive?
- Is there an easy to use BSD Live CD like Ubuntu's that could maybe do the job?

Note, I am very comfortable with Ubuntu and Windows but this was my first time  trying to use FreeBSD or trying to access this type of filesystem.

Any help would be appreciated.

---

### Post by TekNullOG on 2008-02-25
I'm not trying to bump. Just giving my state of progress.

I just tried FreeSBIE (live cd based on BSD) and still had no luck.

Here is what I did:
1- Burnt iso to cd and then booted from it. Selected defaults in boot menus.

2- But unlike most live CDs, you have to start your own desktop environment, if you want one, with startx. Xfce is the default desktop. (if you don't do this, you won't have a gui)

3- > sudo mountdisks rw

It only mounted the ntfs drive which didn't even end up being accessible.

Also, I tried the windows driver again on a different pc but it crashed windows to the point where it automatically rebooted every time I tried to mount the drive.

---

### Post by TekNullOG on 2008-02-28
Turns out freeBSD has a universal command that configures everything, If I took time to read the first few welcome lines when you login at startup, I would have solved this problem much quicker. I feel ashamed. :( sorry

I only had to config the bsd networking and then smb it all out to the windows machine.

Now that I actually know where to do all the configuring, I am surprised to see how easy the command line works on BSD.

---

### Post by the8thstar on 2008-03-16
Hello **eightinches**,

I plan on installing FreeBSD on my machine along with Ubuntu. I want to use my /home partition with the two systems. Will the two OS recognize each other's partitions formats (*FS, ext3)? Do I have to 'tell' them what to look for?

Thanks for your feedback!

---

