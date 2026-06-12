---
title: "Primary Slave not detected"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by The Pinny Parlour on 2006-01-19
Hi all,

Have complete a fresh install and my second slave HDD is not recongnising.  Any ideas?

Thank You

---

### Post by lha on 2006-01-19
[QUOTE=The Pinny Parlour]Hi all,

Have complete a fresh install and my second slave HDD is not recongnising.  Any ideas?

Thank You[/QUOTE]

Does it show up in BIOS? Are the cables good? Are jumpers where they should be? (Master/slave/cable select)

Please post output of
```
sudo fdisk -l
```

---

### Post by The Pinny Parlour on 2006-01-19
Hello,

Yes it shows up in the BIOS and the IDE cable is new.  Jumpers are correct.  What file system should the drive be?  Fat32 etc

Will post when I get home and am on that PC

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)

---

### Post by The Pinny Parlour on 2006-01-20
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)



Thanks

---

### Post by gosh on 2006-01-20
Does it show up in System->Administration->Disks? Is it mounted?
Or in GParted?

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=gosh]Does it show up in System->Administration->Disks? Is it mounted?
Or in GParted?[/QUOTE]

Hi and thanks

It shows up on both.

---

### Post by damianmann on 2006-01-20
so, what is the solution? i have the same issue. It shows up in the device manager. but, i have no idea how to access it's contents:confused:

---

### Post by lha on 2006-01-20
Open terminal and type
```
sudo mkdir /media/hdb1
cd /etc
sudo cp fstab fstab_backup
sudo gedit fstab
```

Add
```
/dev/hdb1 /media/hdb1 vfat gid=admin,dmask=002,fmask=113,ro 0 0
```

and save. Then type
```
sudo mount /media/hdb1
``` in terminal and see if you can access contents on that partition. If everything looks ok, remove ",ro" from the line that was added to fstab to allow writing to hdb1.

These settings give read/write access to root and members of admin group. All other are allowed to read.

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=lha]Open terminal and type
```
sudo mkdir /media/hdb1
cd /etc
sudo cp fstab fstab_backup
sudo gedit fstab
```

Add
```
/dev/hdb1 /media/hdb1 vfat gid=admin,dmask=002,fmask=113,ro 0 0
```

and save. Then type
```
sudo mount /media/hdb1
``` in terminal and see if you can access contents on that partition. If everything looks ok, remove ",ro" from the line that was added to fstab to allow writing to hdb1.

These settings give read/write access to root and members of admin group. All other are allowed to read.[/QUOTE]


Thanks for your help.

I am trying to code in Terminal the following:
```
sudo mkdir /media/hdb1
cd /etc
sudo cp fstab fstab_backup
sudo gedit fstab
```

but only the first line gets recognised in Terminal and it's prompts me for my password which I then cannot type in.

any ideas?   I didn't think hooking up a slave HDD would be so much trouble.

---

### Post by lha on 2006-01-20
[QUOTE=The Pinny Parlour]Thanks for your help.

I am trying to code in Terminal the following:
```
sudo mkdir /media/hdb1
cd /etc
sudo cp fstab fstab_backup
sudo gedit fstab
```

but only the first line gets recognised in Terminal and it's prompts me for my password which I then cannot type in.

any ideas?   I didn't think hooking up a slave HDD would be so much trouble.[/QUOTE]

Ok, each of those lines are separate commands. First type
```
sudo mkdir /media/hdb1
```
You will be asked for your password. Just type it in, even though it seems that nothing happens when you press keys. This is to protect your password. If it showed dots or stars, someone could see how many characters there are in your password. After that, type in each line, one at a time.

---

### Post by The Pinny Parlour on 2006-01-20
Thank you again.

Manage to get the drive to show up but having now luck in being able to write to the drive.  I have removed the 'ro' as you said but no go.

You do not have permissions to write to this folder.

I actually cant save anything to the primary HDD (File System) either

Any ideas?

Thank You

---

### Post by jon_z on 2006-01-20
With your secondary hard drive, I'm not too familiar with gnome, because I've been using KDE forever, but in your disk manager screen shot, are you able to modify your hard disk mount at all. I attached a screenshot of what I mean.  If you have these available options, make sure you (the owner) is the owner of the disk, and check writeable and enable at startup.

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=jon_z]With your secondary hard drive, I'm not too familiar with gnome, because I've been using KDE forever, but in your disk manager screen shot, are you able to modify your hard disk mount at all. I attached a screenshot of what I mean.  If you have these available options, make sure you (the owner) is the owner of the disk, and check writeable and enable at startup.[/QUOTE]


Thanks for your help

I don't have any of those options you speak of, (wish I did).  That KDE looks good and seems to have more options then gnome.  I mgiht have to install that.  Is it easy to do?  Do I need to fresh install or can I install over gnome?  I want this slave HDD to work.

---

### Post by jon_z on 2006-01-20
You have a few options, you can get Ubuntu with KDE pre-installed at:
[Kubuntu]("http://www.kubuntu.org")
or we can go about installing it..
to do this open up a terminal

```
sudo apt-get install kde
```
this will go through and install the (K) (D)esktop (E)nvironment...once it is done press together on your keyboard:  Control + Alt + Backspace   the screen will flash quickly, and you will go back to your login screen.. before typing in your username, you will have an option to select what type of session you want to run,  select KDE instead of GNOME. put your password in and start'er up.

once we have done that, i must suggest going back to the terminal and typing:

```
sudo apt-get install synaptic
```
This is the graphical package manager which is very very very convient.  Once installed goto the kmenu -> system -> package manager (synaptic)  once doing the first time start things, press re-fresh and update**I suggest only doing this if you have a broadband internet connection or else you will be sitting there a LONNNGGG time***

My suggestion is to try installing KDE, see if you like it more than Gnome, if you do, Download and burn the Kubuntu CD...that way your packages that correlate to KDE are there and arent using Gnomes.. (the text editors, system configurations, etc..)  As soon as you boot into Kubuntu: ' sudo apt-get install synaptic '  then go [Here]("http://ubuntuforums.org/showthread.php?t=105343") and follow the instructions.  This painlessly installs many many usefull programs.  hope I helped a bit.

---

### Post by jon_z on 2006-01-20
I made a mistake:> Quote:
install kubuntu 	

from the terminal: sudo apt-get install kubuntu-desktop


Quote:
uninstall unbuntu 	

from the terminal: sudo apt-get remove --purge ubuntu-desktop

From a post by Aysiu: 
Quote:
As you may or may not know, if you install the package called kubuntu-desktop, a lot of other packages will be installed so that you get the full KDE experience in addition to Gnome.

If, however, you uninstall kubuntu-desktop, none of the other "full KDE experience" packages will be uninstalled. You may have installed kubuntu-desktop to get the KDE experience but then found it cluttered things up too much. 	

Link to post: [http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+termina](http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+termina) l

Note: Same situation would exist with Ubuntu leaving meta-packages on Kubuntu's desktop.

---

### Post by jon_z on 2006-01-20
double post eeek
> You can click the little "Edit" button instead.
I did... hence my post not being "double"

---

### Post by heftigrat on 2006-01-20
[QUOTE=jon_z]double post eeek[/QUOTE]
You can click the little "Edit" button instead.  ;)

---

### Post by lha on 2006-01-20
[QUOTE=The Pinny Parlour]Thank you again.

Manage to get the drive to show up but having now luck in being able to write to the drive.  I have removed the 'ro' as you said but no go.

You do not have permissions to write to this folder.

I actually cant save anything to the primary HDD (File System) either

Any ideas?

Thank You[/QUOTE]

I forgot to mention that you have to remount that partition to use new settings from fstab. You can do
```
sudo mount /media/hdb1/ -o remount
```
to remount it.

Where are you trying to save on your primary hdd? You should not be able to write anywhere else except your own home directory without using sudo. This is to prevent yourself or some else from wrecking your system, be it on purpose or by accident. Usually you really don't need to modify or save anything anywhere else except your home.

About KDE: You don't need it to make your hd work. If you want to give KDE a try, go ahead and install it. You are able to use both Gnome and KDE. There's an menu on login screen where you can choose your preferred desktop environment or window manager.

---

