---
title: "how to auto-mount second hdd if its legacy"
date: 2021-03-22
forum: Hardware
---

### Post by devdlp on 2021-03-22
Pretty much i auto-mounted my hdd and some reason i couldnt use the desktop anymore had to reinstall. someone told me that if its uefi first in priority and the hdd is legacy itll break ubuntu. (something like that). so im using Ubuntu 20.10 and i have a ssd that has the 
install on it and a hdd that has nothing on it i didnt even wanna touch it becuase im afraid to break the os again.
i need to know how to auto-mount the hdd so i can use it for my games without getting that black screen when i boot Ubuntu. Thank you in advance.

---

### Post by TheFu on 2021-03-22
Modify the /etc/fstab - add a new line for each file system you want mounted. Use **sudoedit /etc/fstab** to safely make the edits.

Some hints:
[LIST]
[*]Best to choose a native Linux file system for many reasons, not whatever file system the drive arrived from {insert store name here}.  
[*]ext4 is a good all-around file system. If that isn't the type on the disk, you'll 98% want to change it.
[*]Changing to ext4 can be accomplished many different ways. **gparted** is commonly used, but **gnome-disks** can do it as well.
[*]Windows can't directly read ext4, but over a network with a samba share or using sftp (WinSCP), ext4 would be preferred.
[*]Mount using either the UUID, Partition LABEL, or LVM LV "path".
[*]Find the correct UUID using **blkid** command.
[/LIST]

An example /etc/fstab mount line:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=e3396778-bf33-42f5-8420-d1a31bdac7df   /stuff   ext4    nofail,noatime,errors=remount-ro     0  1
```

Here's another example:
```
/dev/vgubuntu/home /home   ext4    noatime,errors=remount-ro    0 1
```
I'm using an LVM-Logical Volume above.
[LIST]
[*]# begins a comment in the fstab file.
[*]Parameter order matters.
[*]The first parameter in each fstab will be unique to your system. You can't just make up answers.
[*]A mount point is just an empty directory that already exists. Well, strictly speaking, it doesn't need to be empty, but when storage is mounted onto the directory, everything underneath it cannot be accessed. 99.99% of the time, that would be undesirable.
[*]Spacing isn't critical - 1 space or 20 are the same.  In the "options area", no spaces are allowed between options. Tabs can be used with or without spaces.
[*]1 line must be used for 1 mount. No wrapping allowed.
[*]Different file system types support different options.
[*]Use sudedit /etc/fstab to make edits to almost all system files. There are exceptions for 3 files (crontabs, sudoers, and passwd), which have dedicated editing commands.
[*]It is smart to backup any modified /etc/fstab files with your daily/weekly backups.
[*]UUIDs are not sensitive. They are automatically generated and we can force a new one to be generated if we like. The only purpose is to have a unique identifier for different storage objects.
[*]If you want to use LABELs, best never to mix case nor have any non-alphabetic characters; no spaces to avoid hassles.
[/LIST]

Above, /home is a very important mount, so I don't have the nofail option.  /stuff isn't as important. If that disk fails or is missing, I still want the OS to boot.
If you web-search using "ubuntu fstab", you'll find a how-to guide somewhere on *.ubuntu.com which explains UUIDs, LABELs, and lots of other options.  An fstab with a broken line seems to break lines below it, so put your new partitions at the end/bottom of the file.

The format of this file hasn't changed in 15 yrs and is the same on all Linuxen that I'm aware.

Some handy commands for gathering storage information:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
Add those to your alias file like any others, the you can just type dft or lsblkt to get the nicer output.  There is a way to have lsblk include the UUID, but I don't use those much so my alias doesn't do that. Sorry.

**If you don't know what this is, ignore it.  **:
If you have LVM storage, there are some things I do to make the mount entries more useful by containing the VG and LV names. LVs have multiple links, any of which can be used for mounts.  Think of it like looking inside different Windows at different couches in a house.  You'll see the same couch, just how you see it is different, but for mounting, that doesn't matter at all. Recent installers have selected about the single most useless "window" to look at the couches, IMHO. I always manually change that spec in the fstab to be human useful, and much shorter.

---

### Post by yancek on 2021-03-22
>  Pretty much i auto-mounted my hdd

How you did that is likely the source of the problem, I don't suppose you took any notes?

>  someone told me that if its uefi first in priority and the hdd is legacy it'll break ubuntu

No it won't.  I'd suggest you find a better source of information.  If you got this from some web site you should probably note it so you don't use it again.  Having a 2nd hard drive with either gpt/legacy(msdos) on which you store data isn't going to make your system unbootable.   You need to first create a filesystem, usually done on a partition or multiple partitions first, explained in detail above.

---

### Post by devdlp on 2021-03-22
[IMG]https://ibb.co/Xs58xN0[/IMG] how does this look before i save it?

---

### Post by devdlp on 2021-03-22
[IMG]https://ibb.co/Xs58xN0[/IMG] how does this look before i save it?

# UUID="3cc92ece-c06c-46b6-a852-3d1a5a8f6686" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="223ad905-01
dont know if you guys can see the image

---

### Post by TheFu on 2021-03-22
> **yancek said:**
>  You need to first create a filesystem, usually done on a partition or multiple partitions first, explained in detail above.

Using the term "automount" sometimes means something specific to Unix people where a different method to mount stuff is used. **autofs** usually manages the **automount** tool. Neither of these other methods are controlled in the fstab.

I didn't really mention exactly how to make a file system.  gparted, gnome-disks, and mkfs can all do it.  
[LIST]
[*]mkfs is a CLI tool.  Fast for people comfortable with that and who don't need to be visually lead to the correct partition.
[*]gparted is a partitioning and file system program - nothing is really buried multiple levels deep. If it is available, I'll use this to create partition tablets, partitions, perhaps format partitions and maybe add a LABEL to it.
[*]gnome-disks buries all the modification parts and removes all the window controls - I'm not a fan of that. Plus, trying to explain what to press, right-click, and enter in a GUI is very hard here.
[/LIST]

On a desktop, I'd use gparted with a right-click on the correct partition ---> Format ---> ext4 in the GUI. ;) Be certain to selected the correct drive in the pull-down list (upper right).

---

### Post by TheFu on 2021-03-22
> **devdlp said:**
> [IMG]https://ibb.co/Xs58xN0[/IMG] how does this look before i save it?

# UUID="3cc92ece-c06c-46b6-a852-3d1a5a8f6686" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="223ad905-01
dont know if you guys can see the image

That is incorrect format for an fstab line.

---

### Post by devdlp on 2021-03-22
Could you please correct it and i can be a script kiddie and just paste it in there3 sorry i suck
or
# UUID=3cc92ece-c06c-46b6-a852-3d1a5a8f6686 /storage ext4 nofail,noatime,error>

---

### Post by devdlp on 2021-03-22
i tried it and i still can log in and out with no blank screen at login but it still doesnt auto-mount

---

### Post by TheFu on 2021-03-22
> **devdlp said:**
> Could you please correct it and i can be a script kiddie and just paste it in there3 sorry i suck
or
```
[COLOR="#FF0000"]# [/COLOR]UUID=3cc92ece-c06c-46b6-a852-3d1a5a8f6686 /storage ext4 nofail,noatime,error[COLOR="#FF0000"]>[/COLOR]
```

The example:
```
UUID=e3396778-bf33-42f5-8420-d1a31bdac7df   /stuff ext4  [COLOR="#00FF00"]nofail,noatime,errors=remount-ro  0  1[/COLOR]
```

I've color coded the problems in your line and important corrections in my example. Details matter.  Those 2 numbers at the end of my line MATTER! You were close.

---

### Post by devdlp on 2021-03-22
oh i see where i messed up i just didnt finished thanks @TheFu

---

### Post by devdlp on 2021-03-22
Bro you the best!!! It worked! restarted its still mounted and everything :) thank you

---

