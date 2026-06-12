---
title: "[SOLVED] Error Loading Operating System - Need A File."
date: 2008-11-08
forum: General Help
---

### Post by coolcole93 on 2008-11-08
Hello :)


I recently was recommended Xubuntu and it's been working fine for a good few weeks now. On Wednesday night, my day after school consisted of doing about 13 pages and completing some coursework, ready to print off in a couple of days. I was going to print it off yesterday but when I turned on my computer it said 'error loading operating system'. I have tried putting the CD in and choosing the 'try Xubuntu without making any changes to my computer to see if I could access my computer's files like that - I can't. 

I assume that I'll have to reinstall Xubuntu, but is there any way I can access my computer's files beforehand to get my coursework off my computer or will I have to spend hours doing it all again :confused:?

Thank you for any answers.

---

### Post by coolcole93 on 2008-11-08
Bump. Please help!

---

### Post by Keith Hedger on 2008-11-08
boot from a live cd, open a terminal and post the output from```

sudo fdisk -l
```

---

### Post by ragtag on 2008-11-08
Did you try and manually mount your drive from the live cd. Create a folder in /media/ to mount to (e.g. /media/mydisk) then run something like.

 mount /dev/sda1 /media/mydisk

See man mount for details. /dev/sda1 could be /dev/hda1, or /dev/sda2,3 etc. depending on your hardware (just use tab completion to see what you have). You may need the -t flag to define your drive type in there too.

If your drive is truly toast, you should look into the programs testdrive and photorec. The first one is to repair broken partitions, and the second one can recover deleted files. photorec requires a place to restore the files to, so you would need a second drive or another computer. The safest thing to do, if you have the hardware (a second computer with lots of disk space), would be to dd the entire drive to file on another computer, and recover data from it there.

Also, I'm no expert at this. So plz wait for more replies. :) I just used photorec a couple of days ago to recover files from a friends computer that he had accidentally deleted (and emptied trash).

Good luck.

---

### Post by coolcole93 on 2008-11-09
I opened the terminal and presses "sudo fdisk -l" but it just came up with more code/writing. 

If what I want is impossble and there's no way of getting my coursework back please tell me to I at keast have enough time to restart it :-k

---

### Post by ciscosurfer on 2008-11-09
> **coolcole93 said:**
> I opened the terminal and presses "sudo fdisk -l" but it just came up with more code/writing.Which was what?  We would like to see it so we can help you futher.

> If what I want is impossble and there's no way of getting my coursework back please tell me to I at keast have enough time to restart it :-k  We don't know if it's impossible yet.  

We need to see the output from sudo fdisk -l (that's a lowercase "L" not the number "1").  The advice that ragtag gave you is good and you should try to follow it.  But before you start dumping data to other drives or disks, let's see if we can mount your current drive in a live environment, as suggested.  To do this, please post the output of the command mentioned so we can see how your drives and partitions are set up.

If you are in a serious time-crunch, and you can remember some of what you've written already, I'd say begin jotting stuff down again that way if you can't recover what you've lost, you'll at least have started again.

---

### Post by coolcole93 on 2008-11-09
> **ciscosurfer said:**
> Which was what?  We would like to see it so we can help you futher.

  We don't know if it's impossible yet.  

We need to see the output from sudo fdisk -l (that's a lowercase "L" not the number "1").  The advice that ragtag gave you is good and you should try to follow it.  But before you start dumping data to other drives or disks, let's see if we can mount your current drive in a live environment, as suggested.  To do this, please post the output of the command mentioned so we can see how your drives and partitions are set up.

If you are in a serious time-crunch, and you can remember some of what you've written already, I'd say begin jotting stuff down again that way if you can't recover what you've lost, you'll at least have started again.

Ok :)

Here it is..

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9542    76646083+  83  Linux
/dev/sda2   *        9543        9725     1469947+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by coolcole93 on 2008-11-09
Sorry to bump, but...

---

### Post by Tony Flury on 2008-11-09
try this :

in the live CD - open a Terminal

and then enter the following 
```

mkdir /media/mydisk

sudo mount /dev/sda1 /media/mydisk

```

If they both work then, your disk will be mounted on as sub directories under /media/mydisk.

you should be able to then use Terminal commands, or a file browswer to get at your files - and save them to a USB disk or similar.

When you reinstall Ubunutu - if you need to - I would suggest creating two partitions - and install /home into one paritition, and all the rest of the OS into the other. That way if ever loose Linux again - at least your files are likely to be safe (or at least safer).

---

### Post by coolcole93 on 2008-11-09
> **Tony Flury said:**
> try this :

in the live CD - open a Terminal

and then enter the following 
```

mkdir /media/mydisk

sudo mount /dev/sda1 /media/mydisk

```

If they both work then, your disk will be mounted on as sub directories under /media/mydisk.

you should be able to then use Terminal commands, or a file browswer to get at your files - and save them to a USB disk or similar.

When you reinstall Ubunutu - if you need to - I would suggest creating two partitions - and install /home into one paritition, and all the rest of the OS into the other. That way if ever loose Linux again - at least your files are likely to be safe (or at least safer).

ubuntu@ubuntu:~$ mkdir /media/mydisk
mkdir: cannot create directory `/media/mydisk': Permission denied
ubuntu@ubuntu:~$ sudo mount /dev/scal /media/mydisk
mount: mount point /media/mydisk does not exist
ubuntu@ubuntu:~$ 



So basically for some reason it won't let me make the 'mydisk' folder as it says access is denied. Is there somewhere I need to put my administrator password in or something?

---

### Post by FreeFull on 2008-11-09
Try putting sudo before the mkdir and repeating the commands above.

---

### Post by coolcole93 on 2008-11-09
> **FreeFull said:**
> Try putting sudo before the mkdir and repeating the commands above.

That worked for the first line  but when I told it to mount to there it said it didn't exist??


ubuntu@ubuntu:~$ sudo mkdir /media/mydisk
ubuntu@ubuntu:~$ sudo mount /dev/sdal /media/mydisk
mount: special device /dev/sdal does not exist
ubuntu@ubuntu:~$

---

### Post by Keith Hedger on 2008-11-09
thats /dev/sda1 NOT /dev/sdal the number one not the letter l u must be more careful about what u type if in doubt use copy/paste

---

### Post by coolcole93 on 2008-11-09
> **Keith Hedger said:**
> thats /dev/sda1 NOT /dev/sdal the number one not the letter l u must be more careful about what u type if in doubt use copy/paste

Aah, thank you! Sorry I was being a bit stupid before ;)

That all worked this time which means my files will be under that directory? Or is it less simple than that? How do I open that directory?

Thank you everyone for helping so far :D

---

### Post by Keith Hedger on 2008-11-09
to list files from the command line use ```
ls -AF /media/mydisk
```
to open them from the desktop just navigate to the /media/mydisk directory and there should be your files (actually they are probably somewhere in /media/mydisk/home/YOURUSERNAME where YOURUSERNAME is your username from the original install

---

### Post by Woody1987 on 2008-11-09
you can navigate to the file using the cd command, try cd /media/mydisk/path/to/file/

E.g. if the file is in the Documents folder then try cd /media/mydisk/home/USERNAME/Documents/    where USERNAME is your username.

---

### Post by coolcole93 on 2008-11-09
Wow, Thank you all so much!

It worked. Many thanks to everyone who contributed in this thread :guitar:

---

