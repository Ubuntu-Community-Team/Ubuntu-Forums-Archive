---
title: "A n00b's Printer and Floppy Questions"
date: 2005-02-23
forum: Hardware &amp; Laptops
---

### Post by Pitbull11188 on 2005-02-23
I have an epson 1000 ics printer and i cannot get it to work, neither can i get my floppy drive to work. This is very important to me because I am a soph in hs and need to write and print papers very often. Also, I'm not sure how to make a data cd. If anyone knows how to fix these problems specifically the printer and floppy drive it would be greatly appreciated. If I can't solve them I will have to go back to windows and so far I like linux MUCH better. Please help me! Thanks.

---

### Post by David Haas on 2005-02-23
Click Computer at the top task bar. Then click "desktop preferences" and select "Removable storage". Here, uncheck, if checked, the boxes next to all the listed removable-storage, devices, including the floppy, the audio cds, etc. When checked, unmounting floppies and data CDs can be blocked.

Now format the floppy. I do it in the shell (terminal) (you don't need to be root to do this) with two commands. The first does a low-level format. The command is: fdformat /dev/fd0 <return>. The second puts the file system (type ext2) on the floppy. The command is : mke2fs /dev/fd0 <return> (The <return> indicates pressing the return or enter key.)

Now you should be able to "mount the floppy," which makes the file system accessible to the computer. You need to be root to mount (you can switch in the terminal at the $ prompt with the command: sudo -s).  Mount it in an empty directory. I use /media/floppy. The command is: mount -t ext2 /dev/fd0 /media/floppy

When you have copied files to the floppy and no longer need it for the session, unmount it with the command: umount /media/floppy.   Do note that the command is umount not unmount. Notice that one unmounts the files from the directory they were mounted to--in this case /media/floppy

I can (or someone else can) help you to use the data cdrom and set up the printer as soon as you have mastered the floppy.

---

### Post by Pitbull11188 on 2005-02-24
Ok I really screwed up i wanted to be able to use the floppy and I chown'd it. Here is the exact line of code I put in:

[CENTER]sudo chown -R jeff:jeff /media/floppy0[/CENTER] 

Please help because now i can't unmount the floppy.

---

### Post by Pitbull11188 on 2005-02-24
Nevermind I read [This](http://www.ubuntuforums.org/showthread.php?t=3687) and fixed my floppy problem. However the printer problem still remains. I think my system may be blocking the wire that the printer is connected by because upon boot I notice 4 errors that appear to be related to the wiring. Any help with this issue would be appreciated. Thanks.

---

### Post by Pitbull11188 on 2005-02-24
Does anyone know of a way to "mount" a usb port because I think that might be my problem, if its not and you know better please help me. Thanks.

---

### Post by Pitbull11188 on 2005-02-25
Somebody please help me I'm lost here! Thanks.

---

