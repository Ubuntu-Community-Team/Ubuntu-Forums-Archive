---
title: "Mount DVD?"
date: 2012-09-03
forum: Hardware
---

### Post by chriswt on 2012-09-03
[FONT=Times New Roman][SIZE=3]I installed Ubuntu 12.04 SERVER on a new HP Pavilion p6-2117c desktop PC.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I am a beginner in Linux! This is my first install.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The install went well, no errors and I selected to have LAMP installed.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]What is keeping me from moving foreword for now is that:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I do not know how to access the DVD. So far, as I understand, it may not be mounted.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Does Ubuntu unmount the dvd after the install? The dvd worked to install from the boot disk.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]For me to see the drives even if they are not mounted, as I understand, is fdisk will show me disk even if they are not mounted. It does work. I’m not sure if the format is NTFS or some other. I selected to format the hard drive Without another OS, dual boot. So Windows 7 may had been removed and I do not know what format it is now.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]HOW DO I GET THIS DVD WORKING TO ACCESS IT?[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Once I do get the dvd working, the next time I boot, will it still be mounted?[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman]THANKS![/FONT]

---

### Post by Bashing-om on 2012-09-03
chriswt; Hi ! Welcome to the forum.

let me see if I can help.
Access the DVD: In ubuntu the device is auto mounted upon insertion of a disk.
                               Question: are you attempting to read a window's disk?
fdisk: is a powerful/potentially destructive tool, as such one must use sudo.
```
sudo fdisk -l
``` 
will list all partitions.

install: If you chose to "use entire disk" on the installation process, I am afraid the installer did just what you told it too; and wiped your windows out. If you did do it as dual boot....do this from the ubuntu command line:
```
sudo update-grub
```

if you installed grub to the booting harddrive, then this command should enable you to boot into windows (chain loading the MBR to windows).

does this suffice to get you started ? Your post is somewhat unclear to me. Post back for any needed assistance.

[INDENT]regards <==BDQ
[/INDENT]

---

