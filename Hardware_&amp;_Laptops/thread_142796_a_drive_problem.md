---
title: "a: drive problem"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by jingo811 on 2006-03-11
Hi've been using Ubuntu: Hoary for a while now and I don't know much about how you mount the a: drive in terminal CLI.  Whoever ironically I've been mounting and writing to my dual Windows XP fat32 partition quite a lot via Ubuntu for some time now.

But ever since Hoary I've been given the tip of using the Diskmounter program to access the Floppy and CD drive without having to type anything in CLI.
That luxury now dissappeared when upgrading the distro to Breezy :???: 
I get this error message when trying to mount the Floppy or merely accessing the diskette:
[http://web.telia.com/~u87415110/gfx/problem_03.png](http://web.telia.com/~u87415110/gfx/problem_03.png)
Since the Breezy install CD seem to be all whack compared to Hoary I had to use my native language Swedish for GUI even though I wanted English.  But that's a whole another chapter.

What the error message says badly translated I guess would be:
> _Mount error_
Cannot mount chosen volume
Fault: chosen **UDI** is not a mountable volume
What the heck does that mean man?  How can I solve this?

---

### Post by StefanoCole on 2006-03-13
Hello, maybe this thread can help you: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=howto+floppy]("http://www.ubuntuforums.org/showthread.php?t=104259&highlight=howto+floppy")

Stefano

---

### Post by jingo811 on 2006-03-21
The procedure was very much appreciated, however I'm thinking of waiting for the next Ubuntu release to fix this bug.  I'm too scared and lazy to do all that complicated stuff.
However I would like som help on accessing the a: drive the easy way trough the terminal.
For instance in CLI: **sudo mount /media/floppy** I can access and copy anthing that's already on the floppy disk.  But I can't transfer and copy any files from Ubuntu to the floppy disk.  Help please :cry: what command will let me transfer files to the floppy?

---

### Post by StefanoCole on 2006-03-22
Well, from terminal type: ```
sudo mount -t vfat /dev/fd0 /media/floppy0
```

then, to copy files to the floppy do:
1. move to the directory where you have the files: ```
cd /path/to/files
```
2. copy the files with the following command: ```
cp filename /media/floppy0
```
3. check files copied with: ```
ls -l /media/floppy0
```
4. unmount floppy with: ```
sudo umount /media/floppy0
```

Note: step 4. is necessary before you extract the floppy, otherwise the files will not be saved. 

Stefano

---

### Post by jingo811 on 2006-03-22
Tnx :mrgreen: appreciate the help!
You know when you save website pages for instance then there's like 50 long and different filenames that's connected to eachother consisting mostly of .gifs and .jpgs.
Is there a copy command that copies entire folders instead of copying each and every 50 file separately?

---

### Post by StefanoCole on 2006-03-22
Well, to copy more files you can type: ```
cp *.* /media/floppy0
```

To copy directories recursively something like: ```
cp -R * /media/floppy0
```
About this last command I am not sure since now I am not on a Linux box, but you could type: ```
man cp
```
and see the options for the copy command.

Note: from terminal you can use the "tab" key to complete filenames in commands like cp, cd, ls, etc.

The following is a link to Linux bash commands: [http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

and to cp command: [http://www.ss64.com/bash/cp.html]("http://www.ss64.com/bash/cp.html")

Stefano

---

### Post by jingo811 on 2006-03-22
tnx :mrgreen:

---

