---
title: "Can't mount usb"
date: 2010-04-01
forum: Hardware
---

### Post by Scoff on 2010-04-01
Hey, I just installed ubuntu, and i can't use my usb sticks, when i try to open it, it says the following:

Unable to mount file location
Can't mount file

---

### Post by garvinrick4 on 2010-04-01
> **Scoff said:**
> Hey, I just installed ubuntu, and i can't use my usb sticks, when i try to open it, it says the following:

Unable to mount file location
Can't mount file
Use gparted or disk utility to give your USB device a Label. I will show you mine.
Now open a terminal and follow instructions and try to understand why you give use the Code:


rick@rick-laptop:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="EC587B18587AE0AE" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="7C2064AB20646E58" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="lucid" UUID="1fa6b366-0d18-442c-91cb-506460b1b9ab" TYPE="ext4" 
/dev/sda6: UUID="904f3813-9702-4940-ac21-33bdcbd44644" TYPE="swap" 
/dev/sda7: LABEL="karmic" UUID="203e3621-e1e0-4879-a286-4736cb8b9b54" TYPE="ext4" 
/dev/sda8: UUID="0db6108c-150d-4466-928e-ef68b4ac2ceb" TYPE="swap" 
rick@rick-laptop:~$ 

So you see all /dev has a partition # and a Label.

If I want to mount a USB device that is having trouble mounting or a partition.

sudo mkdir /media/lucid (makes a directory (or folder) so can be mounted)

sudo mount /dev/sda5 /media/lucid  (it is now mounted)

sudo umount /media/lucid  (that is not a typo umount is right to unmount)

You are better off to label all your devices including flash drives.
Lets say your flash is sba1 with a label of flash.

sudo mkdir /media/flash (make a directory, just have to do it once)

sudo mount /dev/sba1 /media/flash ( mounts drive)

there is a space after mount and a space afte sba1

All your drives are now  /media/flash  or /media/lucid or /media/karmic
whatever you label them and a media in front of.

When you mount you also have to use its /dev/sda1 space then /media/(your label).

Once you label your drives use:
sudo blkid (that is a small L for second letter)
to get your partition # and label.

Your main hard drive is sda1, sda2,sda3 and so on.
USB devices are usually sba1 and so on and on.
Always check to make sure you have right partition # and label.
Soon you will know them all by heart.

---

### Post by garvinrick4 on 2010-04-01
Tell us what version you are using and you will get some links for reading material and
how to's so you get off on right foot with Ubuntu.

---

### Post by Scoff on 2010-04-01
I'm on 9.04 :D

I'll try what you said first btw
 
Should i upgrade to the 9.10?

---

### Post by Scoff on 2010-04-01
I belive my usb thingys are sdb1, look:

scoff@scoff-laptop:~$ sudo blkid
/dev/sda1: UUID="3e48588e-9d99-4315-951f-3314d38ab302" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a5c53054-fdc7-43f2-be97-7176858fbf16" 
/dev/sdb1: LABEL="A-DATA UFD" UUID="56AE-2CB8" TYPE="vfat"

---

### Post by garvinrick4 on 2010-04-01
> **Scoff said:**
> I belive my usb thingys are sdb1, look:

scoff@scoff-laptop:~$ sudo blkid
/dev/sda1: UUID="3e48588e-9d99-4315-951f-3314d38ab302" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a5c53054-fdc7-43f2-be97-7176858fbf16" 
/dev/sdb1: LABEL="A-DATA UFD" UUID="56AE-2CB8" TYPE="vfat"

Yes it is sdb1 and has a label of A-DATA UFD

You can change that label to something easier.

Your Linux is in sda1 and has no Label. You can label that also.

9.04 is a nice stable version to use.
Here is a link to click on to get some instruction.

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Scoff on 2010-04-01
Mind giving me instructions now? :D

---

### Post by garvinrick4 on 2010-04-02
> **Scoff said:**
> Mind giving me instructions now? :D
Start your machine up.
Plug in flash drive.
go into gparted in System/Admin
click on gparted in upper left and go to devices and choose your flash device.
Right click on it and go to label and lable it lets say flash. Then hit the apply
check mark so it takes.

open a terminal and copy and paste these lines one at a time.
If you want to enter them yourself make sure you get spacing right.
There are pdf books on ubuntu you can download for free.

sudo mkdir /media/flash 

sudo mount /dev/sdb1 /media/flash

sudo umount /media/flash  (this line is to unmount and not a typo umount)

---

### Post by garvinrick4 on 2010-04-02
Now you know how to mount a drive with the terminal.

To mount everytime in your GUI (desktop)

Install a program called configuration-editor and open it.

Click on APPS go down to Nautilus click on, go to preferences click on

scroll down to media automount and click check mark in box.

It you want to automount open click check mark in media  automount open


Configuration Editor is in  system tools in Ubuntu software center.

Or in terminal type:  sudo apt-get install gconf-editor

---

### Post by Scoff on 2010-04-02
Ok i get this:
> 
scoff@scoff-laptop:~$ sudo mount /dev/sba1 /media/flash
[sudo] password for scoff: 
mount: special device /dev/sba1 does not exist
And if i try it with sdb1 i get this:
> 
scoff@scoff-laptop:~$ sudo mount /dev/sdb1 /media/flash
mount: you must specify the filesystem type
scoff@scoff-laptop:~$ 
I don't quite get this part... where is gparted thing
> **garvinrick4 said:**
> 
go into gparted in System/Admin
click on gparted in upper left and go to devices and choose your flash device.
Right click on it and go to label and lable it lets say flash. Then hit the apply
check mark so it takes.


Sorry if i'm bothersome, I'm doing my best to learn :P

---

### Post by garvinrick4 on 2010-04-02
If you do not have gparted, you should it is part of ubuntu install disk.
sudo apt-get install gparted

You can always check out if installed by Code:.
aptitude show gparted

Ok to get to gparted you go to System to Administration to gparted. Open gparted
in upper left corner it has a drop down menu that says gparted. Go to devices and choose
sdb1 your flash drive. Right click on it when it opens to your flash drive and go down to
Label and type flash in there. Then click the check mark on upper tool bar to apply it.
Now the flash drive has a label of flash.

The label has to match what you are typing in at the command line.

If that was done and you did label it flash.

You have to sudo mkdir /media/flash (that makes a directory(folder) so it will mount. (have to do this first)

sudo mount /dev/sdb1 /media/flash (it will mount) space after sudo after mount and after sdb1.  

After you label you can always check it out by Code:

sudo blkid     (that is a small L in second letter)

---

### Post by Scoff on 2010-04-05
OK, i swear i did exactly what you said, but I still get this:
```

scoff@scoff-laptop:~$ sudo mount /dev/sdb1 /media/flash
mount: you must specify the filesystem type

```

---

