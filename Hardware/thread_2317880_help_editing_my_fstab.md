---
title: "help editing my fstab"
date: 2016-03-20
forum: Hardware
---

### Post by korn16ftl3 on 2016-03-20
so i have got my server up and running and my 3TB hdd is shared over my network over samba, now comes streaming media via plex as well as a few other minor detail such as the second hdd not auto mounting on restart.

so i have been reading about editing my fstab file so that devices automatically mount on boot this subject first came up when searching why i can not find any sub directories in Plex while using the browse option to set up libraries (see article here: [http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341) )

i attempted to edit my fstab and i had horrible results i had to remove the add'd line so i must have done something wrong, what im hoping for is that someone can help me write the line that i do need to add in the fstab so i dont make this error again.

according to the site i was reading (see here: [http://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup-in-ubuntu-12-04](http://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup-in-ubuntu-12-04) ) i need a few things

```
[COLOR=#111111][FONT=Consolas]UUID=<uuid> <pathtomount> <file system> uid=<userid>,gid=<groupid>,umask=0022,sync,auto,rw 0 0[/FONT][/COLOR]
```

so i obtained most if not all of the information
```
/dev/sda1: UUID="2bd1c8c3-2e6e-433c-ab3c-d5311b98bcd3" TYPE="ext4" 
/dev/sda5: UUID="a53e2978-0c37-438f-a799-60c934be68e6" TYPE="swap" 
/dev/sdb1: LABEL="Network Storage" UUID="686f24ec-b686-4dda-b4b6-0a69a2d6602e" TYPE="ext4" 

```

now 
>  /dev/sdb1: LABEL="Network Storage" UUID="686f24ec-b686-4dda-b4b6-0a69a2d6602e" TYPE="ext4" 

is the device i would like to auto mount on boot up with the following path (whats displayed in the dolphin property's for the HDD's root directory)

> /media/korn16ftl3/Network Storage/

my user id is 
> korn16ftl3@UBUNTU:~$ id -u korn16ftl31000


my group ID is as follows:
> korn16ftl3@UBUNTU:~$ id --groups1000 4 24 27 30 46 107 113


now if im following the instructions correctly the line i need to add should be something like this

```
UUID=686f24ec-b686-4dda-b4b6-0a69a2d6602e /media/korn16ftl3/Network Storage/  type=ext4 uid=1000,gid=1000 4 24 27 30 46 107 113,umask=777,sync,auto,rw 0 0  
```

i have no idea what a umask is but in a quick google search it said it assigns read and write permissions.....personally seeing as how this drive is also my samba drive as well as where my media is stored i would like read write and execute privileges to it when it is auto mounted.

so what im looking for is is this peice of code ready to copy and paste right to my fstab file? what would you guys change about it? i didnt do anything crazy that will screw something up like to many spaces or anything did i? 

i have been known to not have correct linux punctuations shall we call it? before where to many spaces screwed me up every time in the CLI

---

### Post by sisco311 on 2016-03-20
This is the line you have to add to fstab:

```
UUID=686f24ec-b686-4dda-b4b6-0a69a2d6602e    /media/korn16ftl3/Network[color=red]\040[/color]Storage    ext4    defaults    0    2
```

After editing the file make sure that the mount point exist:
```
sudo mkdir -p "/media/korn16ftl3/Network Storage/"
```

To check if the fstab stanza is correct, unmount the partition:
```
sudo umount  "/media/korn16ftl3/Network Storage/"
```

then mount it with:
```
sudo mount -a
```

`-a' means mount all partitions mentioned in fstab.

I

---

### Post by weatherman2 on 2016-03-21
And remember: if "sudo mount -a" returns NO OUTPUT, then everything in the fstab file was mounted correctly.  In other words: no news is good news from that command!

---

### Post by korn16ftl3 on 2016-03-21
thanks for the help....but for future us there are 2 things i gotta ask....

> /Network\040Storage    ext4    defaults    0    2

whats up with the back slash instead of forward and the 040 in the path name?
also what is the 02 for at the end of the line as well seeing as i had 00 in my initial thoughts

---

### Post by weatherman2 on 2016-03-21
Lines in an fstab file have fields that are separated by spaces.  You chose a directory name with a space in it, which could cause problems in trying to understand your directory name.  If you left that name as it was, then it would try to mount to the directory "/media/korn16ftl3/Network" not "Network Storage" and it would think "Storage" was the file system not "ext4" .

"\040" is an "escape sequence" that means "space" in Linux.  It lets you use the name "Network Storage" with the space in your fstab file.

The 2 is a field of information used by the operating system to determine how the mounted file systems are checked with fsck, the file system checking software in Linux.

This page describes exactly what the fields in an fstab file mean:

[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)

---

### Post by deadflowr on 2016-03-21
^ 0(zero) means no check.
Typically it is what swap is set at, since swap partitions won't contain anything, so no need to check it.
But usually 1 is set for the root file system (/)
and then 2 for all others.

---

### Post by SeijiSensei on 2016-03-21
In general, it's best to avoid embedded spaces in file and directory names. Use hyphens or underscores instead.  While a name with an embedded space is valid in Linux, it causes problems for the shell which treats space as a delimiter.  You then need to embed the name in quotation marks or use the backslash "escape" character like this: 
```
Network\ Storage
```
The backslash tells the shell to treat the space literally rather than as a delimiter.  In general embedded spaces are a pain in the neck if you do much from the command prompt.

---

### Post by korn16ftl3 on 2016-03-21
also i made another post over in linuxquestions.org (see here: [http://www.linuxquestions.org/questions/linux-server-73/fstab-editing-4175575465/#post5519104](http://www.linuxquestions.org/questions/linux-server-73/fstab-editing-4175575465/#post5519104) )and got this as a reply:

> **rknichols said:**
> Several problems:
[LIST=1]
[*]The **uid**, **gid**, and **umask** options do not apply to Linux native filesystems like ext2/3/4. They are for filesystems like FAT that don't support Unix-style ownership and permissions. To set ownership and permissions in ext2/3/4 filesystems, use *chown*, *chgrp*, and *chmod* while the filesystem is mounted.
[*]As was mentioned before, you should not use both LABEL and UUID. Use one or the other.
[*]The fstab format does not support quoted strings. The quote characters will be taken literally. To represent a space character, use its octal escape **%040**.
[/LIST]


what way should i actually go about making the HDD auto mount on boot up?

Additional question:

> **sisco311 said:**
> 

After editing the file make sure that the mount point exist:
```
sudo mkdir -p "/media/korn16ftl3/Network Storage/"
```



why would i need to create the directory? isent a directory just a folder? or is this in reference to the root of the hdd im trying to auto mount?

---

### Post by weatherman2 on 2016-03-21
You have to create the directory (same thing as a "folder") because just putting the directory name in the fstab file doesn't create it.  If the directory doesn't already exist, the auto mount will fail.  Create the directory first if you want the fstab mount to work.

If the partition you are trying to auto mount truly is ext4, then having "ext4 defaults 0 2" at the end of your fstab line should be all you need.  (If you asked about umask etc., apparently it was in that other thread, not here.)

---

### Post by korn16ftl3 on 2016-03-21
ok i committed these changes posted above tested it as instructed it all seemed to function before restarting, once the desktop loaded i received the following error screen

> No command arguments supplied!Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...

furthermore none of the sub-directories appeared under the browse option in plex for the HDD im trying to get to auto mount (network storage) .......still....so back to sorting that out as well as what ever i just caused as well....no major i can always undo the auto mount??

---

### Post by weatherman2 on 2016-03-21
It may not appear in the "Browse" section anymore.  But it may be there - navigate to the filesystem, then /media and down to see if you can see it.  If you navigate to an empty directory, then it's probably not mounted.  (Once you find it under /media, then you can bookmark it to make it easy to get back to next time.)

Open a terminal and type:

```
df
```

to see if it is mounted.  If not - show us the full contents of your /etc/fstab file again.

---

