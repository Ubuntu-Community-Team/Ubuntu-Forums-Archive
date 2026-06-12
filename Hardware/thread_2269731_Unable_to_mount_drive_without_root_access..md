---
title: "Unable to mount drive without root access."
date: 2015-03-17
forum: Hardware
---

### Post by maurits2 on 2015-03-17
Hi all,

I took the harddrive from my external USB drive and put it into my computer.
Through gnome-disks I tried mounting the drive but every time I get the following error message:

[COLOR=#545454][FONT=arial]Error [/FONT][/COLOR][COLOR=#545454][FONT=arial]**mounting filesystem**[/FONT][/COLOR][COLOR=#545454][FONT=arial]. Not authorized to perform operation ([/FONT][/COLOR][COLOR=#545454][FONT=arial]udisks-error-[/FONT][/COLOR][COLOR=#545454][FONT=arial]**quark**[/FONT][/COLOR][COLOR=#545454][FONT=arial], [/FONT][/COLOR][COLOR=#545454][FONT=arial]**4**[/FONT][/COLOR][COLOR=#545454][FONT=arial])

[/FONT][/COLOR]I am only able to mount the drive when I have root access and I am wondering if this normal.
If not, how can I fix it?
More information about the harddrive is provided in the screenshot.

Thank in advance for any help!

---

### Post by yancek on 2015-03-17
> I am only able to mount the drive when I have root access and I am wondering if this normal.

Nothing to 'fix'.  That is standard and expected behavior on any Linux system.  You can give yourself read/write permissions as a user by using root/sudo.

---

### Post by Keith_Helms on 2015-03-17
> I took the harddrive from my external USB drive and put it into my computer.

So this drive is now internal in your PC?

The question to me is, do you want to manually mount it every time you want to use it or would you like it automatically mounted when your system boots?

If automatically, then you will need to edit the /etc/fstab file.

The steps I would take are the following:

1.  First of all, figure out what directory you want the volume mounted under.   You could put it under /home/whoeveryouare/newdirectory where whoeveryouare is your user name and newdirectory is the name you want the drive to show up under.  Go ahead and create that directory.

2. The screenprint you attached showed the partition on the new drive is under /dev/sda1.  Do ```
ls -l /dev/disk/by-uuid
```from a command line and you should see a result line for each of your hard drive partitions including one for /dev/sda1:
```
lrwxrwxrwx 1 root root 10 Mar 17 16:49 86fe499e-591c-472d-a87d-1ab49495f53c -> ../../sda1
```

3. Save a copy of your existing /etc/fstab file.  ```
cp /etc/fstab ~/fstab.save
``` or something like that.

4. Do```
gksudo gedit /etc/fstab
``` from the command line.  If you don't have gksudo, try sudo.  If you don't have gedit, try mousepad.  You're going to add a couple of lines to the file:
```
# /home/whoeveryouare/newdirectory was on /dev/sda1 during installation
UUID=86fe499e-591c-472d-a87d-1ab49495f53c /home/whoeveryouare/newdirectory          ext4    defaults        0       2
```

The first line is a comment.  Put whatever you want in there after the #.  For the second line, change the directory path to be the one to the new directory you created.  Copy the long string of hexadecimal characters from the ls -l /dev/disk/by-uuid result line and paste it after the UUID= tag.   BE CAREFUL.  DO NOT DELETE ANYTHING THAT IS ALREADY IN THIS FILE.  IF YOU DAMAGE THE LINE WITH A DIRECTORY NAME OF / YOUR SYSTEM PROBABLY WON'T BOOT!
Save the file, reboot, and the partition on your new drive should be automatically mounted for you.

---

### Post by maurits2 on 2015-03-20
Thank you very much for your reply. This was going to be my next question.
I am wondering if the partitioning is correct: it says 'master boot record' but isn't that only supposed to be on the main hard drive that contains the operating system (which is the other hard drive)?

---

### Post by Keith_Helms on 2015-03-20
Any hard drive can have a master boot record on it.   Yours was probably formatted with one when it was put in an external enclosure.  Those enclosures don't have an OS on them and don't actually boot anything, but having a MBR doesn't hurt anything.  With SATA drives, you can go into the BIOS and set the system to boot from whichever drive you want.  So, bottom line, there's nothing wrong, and you can ignore the MBR on the 2nd drive.

---

