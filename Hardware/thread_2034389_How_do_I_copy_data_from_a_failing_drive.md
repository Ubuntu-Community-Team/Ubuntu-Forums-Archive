---
title: "How do I copy data from a failing drive"
date: 2012-07-25
forum: Hardware
---

### Post by divreu on 2012-07-25
I've booted off the Ubunto 12.04 LTS CD, installed ddrescue and when attempting to run the command line of:
 ddrescue -r 3 /dev/sdf1 /dev/sda2/image /dev/sda2/logfile
where sdf1 is the failing HDD and sda2 is the Windows 7 partition, I receive an error of:
 ddrescue: Can't open input file: Permission denied
The failing drive is 500GB and the destination image is going to a 2TB disk. I'm really new with Ubuntu/Linux and have going through pages and pages of searches trying to found a solution. Any help provided will be truly appreciated. Thanks.

---

### Post by David Andersson on 2012-07-28
1) Please, start a new thread for a new problem. Every person is unique, don't you think?

2)
> **divreu said:**
> I've booted off the Ubunto 12.04 LTS CD, installed ddrescue and when attempting to run the command line of:
 ddrescue -r 3 /dev/sdf1 /dev/sda2/image /dev/sda2/logfile
where sdf1 is the failing HDD and sda2 is the Windows 7 partition, I receive an error of:
 ddrescue: Can't open input file: Permission denied


You should have device /dev/sda2 mounted somewhere. You cannot access files on a file system via the /dev/xxx device. You may be able to mount (and open) /dev/sda2 from the Places menu or from icons on the desktop. When mounted it may have a path like /media/sda2 or /media/1234-5678 or /media/MyWin7Volume. Exactly what path it have you may be able to see when it is opened. (Or you can issue the **mount** command in a terminal. This will list mount points, look for a line beginning with /dev/sda2.)

A few other suggestions. Create a directory on the target partition (Windows 7 partition in this case) for this project. In Windows it could be C:\Users\divreu\Documents\rescue_project_2012 or similar. Mounted in ubuntu the same would be something like /media/1234-4567/Users/divreu/Documents/rescue_project_2012. Then use the **cd** command into that directory to make the rescue command shorter. Also I would call the image something descriptive like "ddrescue.img", "500gb.img" or "seagate.img" and the logfile the same but with ".log" extension: "ddrescue.log", "500gb.log" or "seagate.log".

The commands then would be something like

```
cd /media/1234-4567/Users/divreu/Documents/rescue_project_2012

pwd

ddrescue -r 3 /dev/sdf1 seagate.img seagate.log
```

(Replace directory names and file names to what you choose to call them. Do not run that ddrescue command without the preceeding cd command. You do not want the image to be stored in the live system, where there is not room, and where it may disappear. The pwd command will just show you the current directory, to verify the cd command worked.)

---

### Post by nothingspecial on 2012-07-28
Question moved to it's own thread.

---

