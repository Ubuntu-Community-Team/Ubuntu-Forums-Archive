---
title: "Help me find my other HDD for storage..."
date: 2008-08-12
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-12
Alright I have a 500g hard drive that I am going to be using for storage.

I cant seem to find it, where do I look exactly and if I want to make a desktop icon just drag and drop it right?

---

### Post by iaculallad on 2008-08-12
> **PsychedelicWonders said:**
> Alright I have a 500g hard drive that I am going to be using for storage.

I cant seem to find it, where do I look exactly and if I want to make a desktop icon just drag and drop it right?

Post the output of the following commands when inputted on your terminal:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by tamoneya on 2008-08-12
can we also get these commands:```
lsusb
dmesg | tail
```

Run these ones after you have plugged the drive in.

---

### Post by PsychedelicWonders on 2008-08-12
> **iaculallad said:**
> Post the output of the following commands when inputted on your terminal:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

psychedelicwonders@JohnnyScience:~$ sudo fdisk -l
[sudo] password for psychedelicwonders: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4463        9327    39078112+   7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3               1        4462    35840983+  83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49d849d7

   Device Boot      Start         End      Blocks   Id  System
psychedelicwonders@JohnnyScience:~$ sudo blkid
/dev/sda1: UUID="2B923EB257601A5A" TYPE="ntfs" 
/dev/sda3: UUID="911f7a70-3beb-46c4-ab0f-1a9b73a67a82" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="0ff885db-ddc9-42a1-a15e-0d9544ceeebf" 
psychedelicwonders@JohnnyScience:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> can we also get these commands:```
lsusb
dmesg | tail
```

Run these ones after you have plugged the drive in.

You want me to run these now too?  Or wait till we figure it out?

---

### Post by tamoneya on 2008-08-12
> **PsychedelicWonders said:**
> You want me to run these now too?  Or wait till we figure it out?

i thought it had to do with USB speed and that your drive was not being detected at all.  However from looking at the above outputs it appears that it is just not formated.  Run this:```
gksudo gparted
```Then select /dev/sdb in the pull down on the upper right.  Then add a partition and format it.

---

### Post by iaculallad on 2008-08-12
As tamoneya had suggested earlier, you have to format it first and include that drive in your /etc/fstab file for automount as you want it to be displayed in your user desktop.

---

### Post by y@w on 2008-08-12
Looks like you don't have any partitions created on the drive. Did you just pull it out of the box and plug it in? If so, looks like your device is /dev/sdb. You'll want to run:

```
sudo fdisk /dev/sdb
```

You'll be given a prompt and can type 'm' for help. You'll need to create a new partition of type "Linux", write the changes, reboot the machine, and then create a new filesystem:

```
sudo mkfs.ext3 /dev/sdb1
```

Once you do that you'll need to mount it:

```
sudo mount /dev/sdb1 <mount_point>
```

Obviously, you'll need to change "<mount_point>" to wherever you want to mount the device at.

EDIT: Looks like they beat me to it.. the GUI way works as well :)

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> i thought it had to do with USB speed and that your drive was not being detected at all.  However from looking at the above outputs it appears that it is just not formated.  Run this:```
gksudo gparted
```Then select /dev/sdb in the pull down on the upper right.  Then add a partition and format it.

Where do I find this application again?

---

### Post by iaculallad on 2008-08-12
> **PsychedelicWonders said:**
> Where do I find this application again?

Execute that command in your terminal: Application->Accessories->Terminal

---

### Post by PsychedelicWonders on 2008-08-12
> **y@w said:**
> Looks like you don't have any partitions created on the drive. Did you just pull it out of the box and plug it in? If so, looks like your device is /dev/sdb. You'll want to run:

```
sudo fdisk /dev/sdb
```

You'll be given a prompt and can type 'm' for help. You'll need to create a new partition of type "Linux", write the changes, reboot the machine, and then create a new filesystem:

```
sudo mkfs.ext3 /dev/sdb1
```

Once you do that you'll need to mount it:

```
sudo mount /dev/sdb1 <mount_point>
```

Obviously, you'll need to change "<mount_point>" to wherever you want to mount the device at.

EDIT: Looks like they beat me to it.. the GUI way works as well :)

Now this is a dual boot system, so I want to be able to access any file on either Ubuntu or XP Pro, does this make a difference?

I havent done anything yet, is the GUI you speak of easier than these steps?

Yes I did just pull it out of the box and plugged it in, sorry shoulda said that.

---

### Post by PsychedelicWonders on 2008-08-12
> **iaculallad said:**
> Execute that command in your terminal: Application->Accessories->Terminal

I tried and this is what happened...

psychedelicwonders@JohnnyScience:~$ gksudo gparted
psychedelicwonders@JohnnyScience:~$ gksudo gparted
psychedelicwonders@JohnnyScience:~$

---

### Post by iaculallad on 2008-08-12
> **PsychedelicWonders said:**
> I tried and this is what happened...

psychedelicwonders@JohnnyScience:~$ gksudo gparted
psychedelicwonders@JohnnyScience:~$ gksudo gparted
psychedelicwonders@JohnnyScience:~$

The GParted application window does not show up after you entered your password?

---

### Post by PsychedelicWonders on 2008-08-12
no ive tried it 3 different times, the 1st time it didnt even prompt me for a password, the 2nd time it did, and the 3rd time it did not.

is it spelled wrong?

---

### Post by tamoneya on 2008-08-12
make sure it is installed.
```
sudo apt-get update
sudo apt-get install gparted
```

As for what format to use you could use ext3 or ntfs and be able to access in windows and linux either way.  The way I would pick is based on which you use more often.  If more than 50% of the time you use linux format as ext3.  Otherwise format as NTFS.

---

### Post by PsychedelicWonders on 2008-08-12
Yeah I will be using Ubuntu 99% of the time.

The few times I have had to use windows I have been miserable.

I will try the update now and let you guys know, thanks.

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> i thought it had to do with USB speed and that your drive was not being detected at all.  However from looking at the above outputs it appears that it is just not formated.  Run this:```
gksudo gparted
```Then select /dev/sdb in the pull down on the upper right.  Then add a partition and format it.

Nevermind Im doing it right now, I figured it out.

Do I need to format it after I partition it, or does me creating the partition format it automatically?

---

### Post by tamoneya on 2008-08-12
> **PsychedelicWonders said:**
> Alright everything is installed and scanning now... but you mean the upper left correct?

i meant upper right.  There is a pull down that at the start of the program is labeled: /dev/sda.  This is your old harddrive.  You need to pull it down and select /dev/sdb (the new drive)

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> i meant upper right.  There is a pull down that at the start of the program is labeled: /dev/sda.  This is your old harddrive.  You need to pull it down and select /dev/sdb (the new drive)

Alright, everything has been partitioned, am I done now and ready to mount?

Or does the partition now need to be formatted?

---

### Post by tamoneya on 2008-08-12
gparted allows you to format as well as partition.
1. partition: gparted
2. format: gparted
3. mount: terminal
4. setup automount: fstab

---

### Post by PsychedelicWonders on 2008-08-12
Ok, everything is formatted.

What are the next set of codes to mount this thing?

Mount just means the systems ability to view this device basically right?

I would like to add a numerical value to my HDD's so I know which is which very quick,

How do I name them C:, D: etc?

---

### Post by PsychedelicWonders on 2008-08-12
Will I have to do this mounting thing in windows or just here in ubuntu?

Will the drive just show up in my computer in xp?

---

### Post by tamoneya on 2008-08-12
to mount run these commands (this assumes it is /dev/sdb1 and you are mounting to /media/storage):```
sudo mkdir /media/storage
sudo mount /dev/sdb1 /media/storage
```
If that works then you should add this line to /etc/fstab:```
/dev/sdb1 /media/storage ext3 defaults 0 0
```

---

### Post by PsychedelicWonders on 2008-08-12
Now the way we are setting this up is completely separate from the HDD running my OS's correct?

I'm doing this separate hard drive deal to try and keep my data as corrupt free as possible.

I will be also adding a 500g 3rd hdd to mirror the one we are currently setting up, but thats a whole different thread for a whole different day.  :D

Amd where exactly do I add the following?...

/dev/sdb1 /media/storage ext3 defaults 0 0

Is this the area that I rename them C:, D: etc?

---

### Post by tamoneya on 2008-08-12
> **PsychedelicWonders said:**
> Now the way we are setting this up is completely separate from the HDD running my OS's correct?

I'm doing this separate hard drive deal to try and keep my data as corrupt free as possible.

I will be also adding a 500g 3rd hdd to mirror the one we are currently setting up, but thats a whole different thread for a whole different day.  :D

Amd where exactly do I add the following?...

/dev/sdb1 /media/storage ext3 defaults 0 0

Is this the area that I rename them C:, D: etc?

no that line has nothing to do with windows (C:, D:).  It sets the drive up to automatically mount itself when the OS starts.  It should be added to the end of the file /etc/fstab.  To edit this file type this in terminal:```
gksudo gedit /etc/fstab
```Then just add the new line and save.

as for being separate from your OS driver you are correct.  You have now got a second physical drive setup.

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> no that line has nothing to do with windows (C:, D:).  It sets the drive up to automatically mount itself when the OS starts.  It should be added to the end of the file /etc/fstab.  To edit this file type this in terminal:```
gksudo gedit /etc/fstab
```Then just add the new line and save.

as for being separate from your OS driver you are correct.  You have now got a second physical drive setup.

alright, working on that now.

Why is this dubbed the media file?  just because thats what its going to contain?

Now after this is mounted, what is left in order to be able to drag and drop and save files on a nice little icon on my desktop?

---

### Post by PsychedelicWonders on 2008-08-12
alright so I got this...

terminal:

psychedelicwonders@JohnnyScience:~$ sudo mkdir /media/storage
[sudo] password for psychedelicwonders: 
psychedelicwonders@JohnnyScience:~$ sudo mkdir /media/storage
mkdir: cannot create directory `/media/storage': File exists
psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdb1 /media/storage
psychedelicwonders@JohnnyScience:~$ gksudo gedit /etc/fstab

that other thing :)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/storage ext3 defaults 0 0

Is all of that correct?

---

### Post by tamoneya on 2008-08-12
yep your all set.  Just so you know, from now on you no longer need the sudo mkdir /media/storage.  That was just necessary the first time and you got that error because you ran it twice.  Now place your data that you want to protect in /media/storage.  If you want you can make links between some directories in your home to /media/storage

---

### Post by PsychedelicWonders on 2008-08-12
where exactly do I access this new drive for the first time?

places>computer?

How do I change its name?  Just right click and rename?

I can now drag and drop this to the desktop for easy use right?

Also when I set my programs (frostwire, bit torrents, digital camera etc) to automatically save new files to a specific directory, what one do I use to access this drive now?

like it windows it would be

d:/myfiles/music 

etc.

How or where do I figure out what that is in Ubuntu?

---

### Post by tamoneya on 2008-08-12
you access by putting files in /media/storage.  Any files in there are written to your new drive instead of the old OS drive.

---

### Post by PsychedelicWonders on 2008-08-12
I type that in the terminal?

Sorry sometimes its hard for me to understand new things completely, gotta break it down barney style for me from time to time.  :)

I really appreciate all your help, youve helped me on many different subjects, thanks.

---

### Post by tamoneya on 2008-08-12
you dont have to do anything.  Open nautilus and navigate to /media/storage.  Any files in that directory or any of its sub directories will be on the new harddrive.

---

### Post by PsychedelicWonders on 2008-08-13
what is nautilus?

I've looked in all the menus at the top, didnt see anything?

---

### Post by tamoneya on 2008-08-13
nautilus is the file manager.  Its where you can view your files and everything.  Lets just start from the desktop.  Go to "places -> filesystem"
Then navigate to /media/storage.  Any files there are on the new drive.

---

### Post by PsychedelicWonders on 2008-08-13
is this where you mean?

I dont see anything labeled "filesystem"

or media/storage?

---

### Post by tamoneya on 2008-08-13
in your case it would be "places -> computer"
EDIT: you can also see the new drive as 500 GB drive near the bottom of the menu.  THis would take you to /media/storage

---

### Post by PsychedelicWonders on 2008-08-13
Ahh ok so that is it.

What is this lost+found file inside of it?

Can I just delete this?

---

### Post by PsychedelicWonders on 2008-08-13
Im trying to drag and drop a file on the right to the hdd in the left column and im getting this error message...

Can you npt drag and drop?

---

