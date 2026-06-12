---
title: "Floppy disk drive"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by ron999 on 2006-07-21
Hi
I'm new to Linux. I installed Ubuntu 6.06 Dapper Drake.
Please can somebody explain how to mount and use my floppy disk drive.
Ron

ps I'm going to move this to a more appropriate thread

---

### Post by ron999 on 2006-07-21
Hi
I'm new to Linux. I installed Ubuntu 6.06 Dapper Drake.
Please can somebody explain how to mount and use my floppy disk drive.
Ron

---

### Post by Sef on 2006-07-21
> ps I'm going to move this to a more appropriate thread

This is the appropriate thread for your question.


> Please can somebody explain how to mount and use my floppy disk drive.

From a previous post of mine:

> 1) Open Terminal (Konsole in KDE)

2) sudo gedit (Kate in KDE) /etc/fstab

3a) Go to the floppy module (on the bottom in gedit)

Code:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


3b) Change auto to vfat

Code:

/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

4) To open the floppy, go to Places > Computer > click on the floppy (Not sure what it is called in KDE.)

5) Click on the floppy pic

6a) Floppy drive will mount

6b) You can read your floppy documents

6b) To unmount, right click on the floppy and highlight unmount

[Floppy]("http://ubuntuforums.org/showthread.php?t=181436&highlight=Floppy")

---

### Post by catlett on 2006-07-21
It should be as simple as putting the floppy in and going to Places<Computer. From there double click on the floppy drive.
If that doesn't work you can use the command line to mount and unmount.
To mount enter 
```
sudo mount /dev/fd0
```
To unmount enter
```
sudo umount /dev/fd0
```
If you want to do it graphically you can add the floppy formatter and the mount disks launcher for the panel.
The floppt formatter is in Applications<System Tools<Floppy Formatter If it doesn't appear in the menu, go to Applications<Accessories<Alacarte Menu Editor and add it to the menu.You don't necessarily have to format the floppy but it is a good way to erase a disk as well as a means to format it as linux ext2 as opposed to dos.
Next you can add a disk mounter to the panel. Go  to the top or bottom panel and right click. Select "add to the panel". A window will open with icons for different addons. Scroll to "system and hardware" and you will see "Disk Mounter". Hit on it to highlight it and then hit "add" in the right corner.
Now you will see icons on your panel that represent your partitions, cd drive and floppy drive. To mount a floppy just click on the floppy icon and a menu drops down with an option to mount the floppy. Click on mount and the floppy mounts. You can also open the floppy folder from the icon as well. When you want to unmount just do the same thing except there will be an unmount option.
Make sure you unmount the floppy. If you just press the button on the computer case to eject it, it won't have the data on it that you added. The floppy isn't synced to the system. Meaning the data doesn't get written to the floppy when you drag and drop or enter a command. It will write the data later . Most of the time the data is written when you unmount the floppy. If you select unmount you will see a window apear with a bar graph showing that data is being written to the floppy.

---

### Post by ron999 on 2006-07-21
Hi
I've put a floppydisk into the drive. When I click on places/computer it shows my file system and CD-ROM drive but no floppy drive.

When I entered sudo mount /dev/fd0 this is what I got:- 
ron@ron-desktop:~$ sudo mount /dev/fd0
Password:
mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab

It's getting late now and difficult to concentrate so I will read the rest of your reply in the morning and see what happens.
 
Thanks

Ron

---

### Post by catlett on 2006-07-21
I see what your problem. You do not have an entry for your floppy drive. 
/etc/fstab is the file that tells the computer what to mount and how.
We can edit your file with these commands. Open a terminal and enter 
```
sudo mkdir /media/floppy0
```
now we will open the text and edit it
```
sudo gedit /etc/fstab
```
Place this line in the next available line
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
Make sure to hit save at the top of the window. Close the document and reboot. That should solve your problem. Now any method I listed should work.If you get another error, post it here.

---

### Post by lizzard on 2006-07-21
It seems that there misses an entry for your floppy drive in /etc/fstab.
So do a 'sudo gedit /etc/fstab' and enter something like this:
```
/dev/fd0        /media/floppy0   auto   rw,user,noauto  0       0

```

---

### Post by lizzard on 2006-07-21
Oh, Catlett was faster than me, and of course you have to create the directory /media/floppy0 to use it as mountpoint. That's what I forgot.

---

### Post by ron999 on 2006-07-21
Hi catlett (and lizzard) - thanks for your replies

I've added the line to the etc/fstab file.
Now when I click on places/computer it does show Floppy1.

But when I try to mount it I get:-

ron@ron-desktop:~$ sudo mount /dev/fd0
mount: you must specify the filesystem type

Also I've followed your graphical instructions and it went well - except that when I click on Mount Floppy1 it says:- mount:I could not determine the filesystem type, and none was specified.

What next?

Ron

---

### Post by catlett on 2006-07-21
What a pain the "auto" section of the entry means the system should automatically detect the file system type. 
Just to verify that everything else is working. Get to the floppy formatter and format the floppy. Then try and mount.
Let me check my /etc/fstab guide and see if there is something to cure this.

---

### Post by ron999 on 2006-07-21
Hi catlett

It won't let me format the floppy. It says cannot initialise device, unable to open any device, formatting cannot continue.

I've just noticed the reply from sef above. He suggested using 'vfat' instead of 'auto' in the fstab file. I've tried doing this too but no different.

Ron

---

### Post by catlett on 2006-07-22
The server was down and I couldn't get in for a while.
It sounds like this is bigger than mounting. The system isn't recognising the floppy device properly, or at least it seems that is the issue.
I'll hunt for a solution and post back.

---

### Post by ron999 on 2006-07-22
Hi

Has anyone else got any ideas why I can't mount the floppy drive please?

Ron

---

### Post by ron999 on 2006-07-22
Hi

Has anyone else got any ideas why I can't mount the floppy drive please?

Ron  ... I'm beggin'

---

### Post by Sef on 2006-07-26
Have you checked to make sure that all the wiring is connected ok?

---

