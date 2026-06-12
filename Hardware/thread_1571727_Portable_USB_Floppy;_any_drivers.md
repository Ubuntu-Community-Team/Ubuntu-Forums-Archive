---
title: "Portable USB Floppy; any drivers?"
date: 2010-09-10
forum: Hardware
---

### Post by M_Mynaardt on 2010-09-10
Hi!

I discovered a USB floppy that I forgot I had.  But my laptops with Linux don't seem to recognize it.  I put in a floppy, it makes a bit of noise, but nothing gets mounted.

Any ideas or suggestions?  It's a Mad Dog portable USB drive.  I don't have many occasions to use it, but it would be nice if I could make it work...

---

### Post by Master Cabbage on 2010-09-11
I am having the same problem with a Dell Floppy Drive Module. I plug it in, sounds, but no mounting.

**Edit: **I have gotten my floppy USB drive to work. Here is what I did:

1. Go to Place -> Home Folder -> File System -> Media
2. Create a folder in the Media file called data. You will now have this directory /media/data/
3. Install the program MountManager from the Ubuntu Software Centre
4. Plug in your USB Floppy Drive
5. Open MountManager. If your floppy disk is detected you should see a floppy symbol. Note where it is located. Mine happened to be located at **sdb**
6. Open Terminal and type > sudo mount /dev/**sdb** /media/data You will substitute the location of your drive in the **sdb** section of the command. Note the space between sudo and mount, mount and /dev, sdb and /media
7. Open the /media/data folder. The contents of your floppy disk should be there. If you don't see any files and you know something should be there press the reload button. 
8. To unmount the drive enter > sudo **umount** /dev/**sdb** /media/data

Note: I have not been able to edit anything in these folders, simply copy the data, which was all I wanted to do.

**Edit:** Also, to give credit where credit is due, my steps are adapted from:
[http://ubuntuforums.org/showthread.php?t=679692](http://ubuntuforums.org/showthread.php?t=679692)

---

### Post by M_Mynaardt on 2010-09-11
Thanks for the advice...

I'll see what happens with Mount Manager.

I don't really _need_ the USB flobby drive much.  But it would be a 'nice to have' gadget should it work for me.  I have flash drives and data back-ups coming out of my ears (_not_ literally, of course), so I'm okay for data on the whole.  But since I had that USB floppy drive anyway, I thought it would be nice if I could make it work for me sometimes.

Thanks for recommending Mount Manager; I'll see how well that works for me, if nothing else.

...  This might take a while.  I tried to create /media/data/ but I couldn't create a new folder in /media/ ... at least not from the GUI

---

### Post by Master Cabbage on 2010-09-11
> **M_Mynaardt said:**
> 
...  This might take a while.  I tried to create /media/data/ but I couldn't create a new folder in /media/ ... at least not from the GUI

You might have to access it through nautilus. 

Go to the terminal and enter 

>  sudo nautilus 

You will probably be able to add the folder through there.

---

