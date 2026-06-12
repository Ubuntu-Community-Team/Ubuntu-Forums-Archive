---
title: "Restore Deleted Files"
date: 2008-08-30
forum: General Help
---

### Post by dcraighead on 2008-08-30
HELP!! I'm new to Ubuntu. During a file backup, I mistakenly deleted some important files. Shortly before, I had dragged the "My Documents" folder to the "Read/Write Disk" for burning. Before burning, I decided to delete some old files. Thinking the "Read/Write" window was the active window, I began to delete old files only to realize later I was in the "My Documents" file on the HD.

I've read some of the posts but am not computer savvy enough to understand the suggestions; just don't know enough about computers.  Any suggestions for restoring those deleted files.  I need very specific, step-by-step instructions.  Thanks in advance.

---

### Post by gmxgeek on 2008-08-30
Check the trash bin. If they are there, restore them. If not then the process to restore is very long and complex and might not work. so try the trash bin first :)

---

### Post by dcraighead on 2008-08-30
> **gmxgeek said:**
> Check the trash bin. If they are there, restore them. If not then the process to restore is very long and complex and might not work. so try the trash bin first :)


Thanks. I did check the "Trash" but it is empty...It's feeling more like a labor day weekend than planned.

---

### Post by gmxgeek on 2008-08-30
> **dcraighead said:**
> Thanks. I did check the "Trash" but it is empty...It's feeling more like a labor day weekend than planned.

Well, while i think it might be technically possible to retrieve the data, it is far beyond my ability. Good luck though

---

### Post by 3DGE on 2008-08-30
Is there a system restore function in Ubuntu ?

---

### Post by drs305 on 2008-08-30
No, there isn't a system restore function.  :-(

Did you delete the files using the "rm" command in terminal or use SHIFT-del? If you deleted the files by either of those methods the files are difficult (but not totally impossible) to restore. There have been threads which detail which apps can do it but I don't think it is a simple process.

If you want to search through *all* the trash bins to see if they might have ended up there, use this command and then explore the contents with nautilus or another file browser:
```
sudo find / -type d -iname *Trash* | grep Trash
```

Good luck.

---

### Post by ShinHadoken on 2008-08-30
> **drs305 said:**
> No, there isn't a system restore function.  :-(

Did you delete the files using the "rm" command in terminal or use SHIFT-del? If you deleted the files by either of those methods the files are difficult (but not totally impossible) to restore. There have been threads which detail which apps can do it but I don't think it is a simple process.

If you want to search through *all* the trash bins to see if they might have ended up there, use this command and then explore the contents with nautilus or another file browser:
```
sudo find / -type d -iname *Trash* | grep Trash
```

Good luck.
That would have been my suggestion, but drs305 beat me to it! :D

---

### Post by dcraighead on 2008-08-30
> **drs305 said:**
> No, there isn't a system restore function.  :-(

Did you delete the files using the "rm" command in terminal or use SHIFT-del? If you deleted the files by either of those methods the files are difficult (but not totally impossible) to restore. There have been threads which detail which apps can do it but I don't think it is a simple process.

If you want to search through *all* the trash bins to see if they might have ended up there, use this command and then explore the contents with nautilus or another file browser:
```
sudo find / -type d -iname *Trash* | grep Trash
```

Good luck.

I did not use the "rm" command or SHIFT-del. I simply right-clicked on the file folder and a menu came up which included "Send to Trash." I selected that option but a window immediately came up saying, "Cannot move to trash, do you want to delete immediately," with option buttons at the bottom of the window. I chose the "Delete" button.

You'll need to bare with on this but I don't know how to search "all" the trash bins with nautilus or another file browser. I'm at a lost as to where to enter the [CODE]sude find / type d -image *Trash* | grep Trash|/CODE].

---

### Post by EmanresuusernamE on 2008-08-30
Looks to me like you erased some files from your windows partition.  If you still have windows try using: 
[http://www.pcworld.com/downloads/file/fid,23108-order,1-page,1/description.html](http://www.pcworld.com/downloads/file/fid,23108-order,1-page,1/description.html)
It's small, and free, and pretty good too.  Don't put this on the hard drive that you erased the files from, or you won't be able to recover some files.  When you erase a file, you only unlink it from the filesystem for the most part.  If you put stuff on the hard drive after you erase it, you risk having that data overwritten and loosing it permanately.

---

### Post by EmanresuusernamE on 2008-08-30
Before I forget, you don't have to install it.  So put it on a USB drive and then run it from Windows.

---

### Post by az on 2008-08-30
Was what you deleted on the same partition as your ubuntu partition?  Because "My Documents" is typically windows.

If you deleted stuff from an NTFS filesystem, don't boot into windows.

Install ntfsprogs and use ntfsundelete:

[https://help.ubuntu.com/community/DataRecovery#Ntfsprogs](https://help.ubuntu.com/community/DataRecovery#Ntfsprogs)

---

### Post by drs305 on 2008-08-30
> **dcraighead said:**
> You'll need to bare with on this but I don't know how to search "all" the trash bins with nautilus or another file browser. I'm at a lost as to where to enter the ```
sude find / type d -image *Trash* | grep Trash|/CODE].

No problem. Consider this a learning experience. The chances of finding the files may not be great but you can learn a bit about the command line (CLI)...

Copy the 'sudo find ...' command above (CTRL-C). Since you probably prefer icons, go to Applications, Accessories and select Terminal. *As a technique, since you will use the Terminal often, I would drag the Terminal icon to the top panel to create a shortcut that is always available.* Paste the command in the terminal (CTRL-**SHIFT**-V) and hit Enter. After a while, depending on how large your disks are, the results will appear. You will see something like:
[CODE]
~/Desktop: sudo find / -type d -iname *Trash* | grep Trash
/media/ntfs/.Trash-1000
/home/drs305/.local/share/Trash
/home/.Trash-0

```

These will be all the different Trash bins on your computer. There are at least two and maybe many more. Open nautilus or another file browser with the command "gksu nautilus" from another terminal window and navigate to each Trash bin. Most Trash folders have two subfolders - info and files. The deleted files would be in the 'files' folder.

If you prefer, you can copy the results of the previous command by highlighting each line. In a terminal, you copy with CTRL-SHIFT-C and paste with CTRL-SHIFT-V (or highlight it with your mouse to copy and middle click to paste). Once you have copied one of the lines, you could enter it below and nautilus will take you directly to the trash bin you copied:
```
gksu nautilus PASTE_HERE
```

Example: gksu nautilus /root/.local/share/Trash

Hopefully I haven't confused you too much. Again, happy hunting.

---

### Post by dcraighead on 2008-08-30
I tried your code via the "terminal" and received the following response:
find: /home/ubuntu/.gvfs: Permission denied
ubuntu@ubuntu:~$

---

### Post by dcraighead on 2008-08-30
This is the heart of my problem. I am running XP-Home (well, was; it crashed 2 days ago). My nephew suggested Ubuntu. A friend downloaded it and burned me a disk so I'm running a life OS via my DVD drive. How would I store the PCWorld download you suggested?

---

### Post by dcraighead on 2008-08-30
Thanks, but I'm being stopped by a "Permission Denied" issue. In the terminal window, how do I write the search code as an "administrator"?

---

### Post by EmanresuusernamE on 2008-08-30
> **dcraighead said:**
> Thanks, but I'm being stopped by a "Permission Denied" issue. In the terminal window, how do I write the search code as an "administrator"?

You either didn't put sudo in front of all of those commands, or you're not using the proper username and password.  Also, the login you used must be enabled to use sudo.  Usually the first login created is given these permissions by default.

> **dcraighead said:**
> How would I store the PCWorld download you suggested?
Use another computer to put it on a USB flash drive.  Or even better, if their computer has the room and cables, attach your hard drive to their system and run the Restoration program off of their machine.

---

### Post by dcraighead on 2008-08-30
If I understand your question, "No." Ubuntu is not loaded on my computer. I was attempting to copy files from my windows system that crashed two days ago. My nephew suggested using the Ubuntu OS, running live to get to my files, copy them and then reload my windows XP. I'm now running the live Ubuntu OS via my DVD drive with no change to my system (as far as I know and other than deleted fiels). I was at the copying files step when I mistakenly deleted the wrong files. I'm trying to recover them before preceding.

---

### Post by EmanresuusernamE on 2008-08-30
Hmmm, it would probably be best for you to take the hard drive out of your system and add it into someone else's system and then run that restoration program off of that system.  If Ubuntu does like windows does, it only removed the link to the file and didn't actually delete it.  It's just not associated at all.

---

### Post by monkeyking on 2008-08-31
If the data is very important, do a total raw disk copy using dd.

Then you can play around.
What kind of files is it.
text files, movies, music, and how many gigs.

As long as your files were on a ntfs,
you are quite likely to recover everything.

check this one out.
But do make a complete back up first.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by al prince nofl on 2011-01-06
This video can help you and test by me.. [http://www.youtube.com/watch?v=QGAgpl77Vmc](http://www.youtube.com/watch?v=QGAgpl77Vmc)

---

### Post by axept on 2011-01-06
Hello,

I used a program called PhotoRec to recover my photos a time ago. I worked well for me. But that was on a broken HDD. 

Anyway, you can try it for your self. It finds anything, not just photos. And there will be many files! 

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Its easy to use.

---

