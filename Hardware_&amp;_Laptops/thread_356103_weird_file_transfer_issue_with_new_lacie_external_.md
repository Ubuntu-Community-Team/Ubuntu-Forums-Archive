---
title: "weird file transfer issue with new lacie external drive"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by wickstopher on 2007-02-08
I just picked up a 320gb  usb 2.0 lacie external hard drive (one of the porsche designed editions).  Ubuntu recognized it just fine, and I checked in gparted, and the filesystem is fat32.  Transferring files hasn't been a problem, except for this:  when I attempt to transfer a file that exceeds 4gb (i.e. an iso image of a dvd), it automatically shuts down the transfer at *exactly* 4gb.  Has anybody else experienced similar problems, and is there any solution?  Haven't tried it in windows (the drive did come with some windows software called "1-click backup", and i have an xp pro partition on my hdd).   please don't tell me that i need proprietary software to use an external hard drive!

Edit:
I just tried doing the same thing with my other external drive (maxtor 80gb).  Lo and behold (I guess I haven't yet attempted any large file transfers), I'm experiencing the same problem.  I can Transfer a large group of files no problem.  It doesn't seem to matter whether or not the whole group of files is greater than 4gb.  But if one single file exceeds 4gb, it stops, very consistently, at exaclty 4gb (right down to the last byte).  Is this a problem with nautilus, or with that fat32 filesystem?  Or is it a problem with the ubuntu usb 2.0 drivers?  Or is it something else?

---

### Post by terdon on 2007-02-08
Do you get the same problem at the command line? 

If nothing else works, you can always use split:

Split file into  ~2GB pieces (named xaa,xab etc):
 [INDENT]split -b 2000000000 filename [/INDENT]
Copy each file (assuming they are the only files beginning with x):
[INDENT]cp -v x* /media/lacie (or whatever your destination folder is)[/INDENT]
[INDENT]cd /media/lacie [/INDENT]
Then put it all together again
[INDENT]cat x* > new_file_name[/INDENT]

Hope this helps.


PS. I have a LACIE drive and I haven't seen this problem. I'll go try it and see if I get it too.

---

### Post by wickstopher on 2007-02-08
I do get the same problem with the command line cp app.  Using -v for verbose output, I get this message:

File size limit exceeded (core dumped)


and I get the same results.  Apparently my file size limit is set at 4.0gb.  Any way to change this?

edit:
I get the same (core dumped) message when splitting the file apart (this works fine), and then attempting to reassemble it using cat (this is where I get the message after a certain time).

there has to be a way to reset the file size limit!  thanks!

---

### Post by wickstopher on 2007-02-10
Issue Resolved (partly).

After a little digging, I found out that there is in fact a file size limit in the fat32 filesystem itself, and it is 4gb.  Most folks reading this forum probably already knew that, but I didn't!

I ended up using the gparted liveCD to reformat my external drive to the ext3 filesystem.  I ran into a problem here, as it automatically sets the owner of the drive to root, so I couldn't write to it from my normal ubuntu profile.  I had to login as root, mount the drive, and change ownership to my user profile.  Now I'm writing big files!  The only complaint I have here is that I was really hoping for a drive to share large files between my ubuntu and xp pro partitions.  Insofar as I can tell, there is no way of making this happen, as the only friendly gobetween filesystem seems to be fat32.  Any suggestions, or am I stuck with this solution for the time being?

---

### Post by gradedcheese on 2007-02-10
You can edit your /etc/fstab to have the drive mounted with 'user' permissions rather than for root.  I forgot about the FAT32 limitation, but it makes sense if you think about it... 2^32 = 4GB ;)

---

### Post by judyh on 2007-02-17
> **wickstopher said:**
> Issue Resolved (partly).
The only complaint I have here is that I was really hoping for a drive to share large files between my ubuntu and xp pro partitions.  Insofar as I can tell, there is no way of making this happen, as the only friendly gobetween filesystem seems to be fat32.  Any suggestions, or am I stuck with this solution for the time being?

I used this [solution]("http://www.fs-driver.org/") some time ago with great success on an ext3 volume.
From the website:
[INDENT]The "Ext2 Installable File System for Windows" software is freeware.
It provides Windows NT4.0/2000/XP/2003 with full access to Linux Ext2 volumes (read access and write access). This may be useful if you have installed both Windows and Linux as a dual boot environment on your computer.
Linux Ext3 volumes can also be accessed. To do that, please read the FAQ section.[/INDENT]

---

