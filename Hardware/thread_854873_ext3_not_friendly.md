---
title: "ext3 not friendly"
date: 2008-07-09
forum: Hardware
---

### Post by badaveil on 2008-07-09
My pc has a master and slave hard disk both on NTFS file system. On Sunday, newbie me did a successful installation of Ubuntu 8.04 in the master hard disk but the slave hard disk icon was missing. I managed to mount it using the command line taken from HELP plus sudo in front. After a reboot, the slave hard disk got mounted but was still in NTFS mode. I managed to install the Partition Editor and reformated the slave hard disk to ext3. Now, the name of the secondary hard disk has changed from "secondary" to "80.0 GB Media" which I don't like. I want to relabel it but this is not allowed from the "backend".

Q1: How do I relabel ext3 when the e2label [dev] [newlabel] command doesn't work?
Q2: How do I get ext3 to be "friendly" because I want to save my work files there but I can't send any file there though I can open ext3?

---

### Post by jocko on 2008-07-10
> **badaveil said:**
> Q2: How do I get ext3 to be "friendly" because I want to save my work files there but I can't send any file there though I can open ext3?

What do you mean? Do you mean you don't have permissions to write to the file system?
Paste the outputs from these commands here, so we can see how you have mounted it and which permissions you have set to it:
```
cat /etc/fstab
mount
ls -l /media
```

---

### Post by Vivaldi Gloria on 2008-07-10
See this thread for labelling commands:

[http://ubuntuforums.org/showthread.php?t=824697&highlight=tune2fs](http://ubuntuforums.org/showthread.php?t=824697&highlight=tune2fs)

A piece of advice:

It is customary to mount disks to 

```
/mnt/mountpoint
``` 

via fstab. When you do, disks don't show icons on the desktop. Then you can put a symlink from /mnt/mountpoint to where ever you want and name it whatever you want. This is how it is supposed to be.

---

### Post by jocko on 2008-07-10
> **Vivaldi Gloria said:**
> When you do, disks don't show icons on the desktop. Then you can put a symlink from /mnt/mountpoint to where ever you want and name it whatever you want. This is how it is supposed to be.

What if someone actually wants links to the disk on the desktop?
I like it that way, so I dont have to browse my way through the file system to find my mounted disks... and mounting in /mnt just to manually put links on my desktop? That's a bit silly if it's done automatically if I mount it in /media, don't you think?
Why is that wrong? Just because you don't like it, it doesn't necessarily mean noone likes it.
And this thread have NOTHING to do with where links do or do not appear...
Of course if the op have mounted his disk in /mnt or /home or wherever he likes it, it would be obvious from his fstab, and someone who wanted to help him would have seen it and adjusted the command if he didn't do it himself.
I just included "ls -l /media", because that's where things end up in a default ubuntu install unless you change it yourself. Most instructions I have seen on mounting disks do it in /media, so I find it likely that this is where the op have it...

---

### Post by Vivaldi Gloria on 2008-07-10
> What if someone actually wants links to the disk on the desktop?

Well, then put a link there from /mnt/mountpoint.

> I like it that way, so I dont have to browse my way through the file system to find my mounted disks... and mounting in /mnt just to manually put links on my desktop? 

You add the disk to fstab once and you put a link to where ever you want once. You don't keep mounting them manually forever (unless you want that).

> That's a bit silly if it's done automatically if I mount it in /media, don't you think?

Not really.

> Why is that wrong? 

It's better to learn about preferred ways of doing things and get used to the OS you use. 

> Just because you don't like it, it doesn't necessarily mean noone likes it.

People can like a lot of things. This doesn't negate the fact that there is a preferred way of doing things. 

Another example. It is possible that someone likes downloading apps from their webpages and installing & updating them manually as it is in the case with windows. But I won't suggest it. Why? Because the suggested way of installing programs in linux is using the repos. So liking or not liking something doesn't necessarily make it the preferred way. 

> And this thread have NOTHING to do with where links do or do not appear...

Yep. You are right. If you think that it's a big sin to go slightly off-topic then I apologize. But I thought the OP should know the other way of doing things. 

> Of course if the op have mounted his disk in /mnt or /home or wherever he likes it, it would be obvious from his fstab, and someone who wanted to help him would have seen it and adjusted the command if he didn't do it himself. I just included "ls -l /media" ... 

I'm not critizing you at all for asking for those commands. I was pointing out the preffered way of doing things. If you or the op don't want to do it that way then fine. But I don't see what is wrong with giving more knowledge. The more knowledge, the better. 

> ... because that's where things end up in a default ubuntu install unless you change it yourself. 

Ubuntu doesn't put a line in fstab for extra disks. If you decide to put a line in fstab for one I suggest you mount it to /mnt/mountpoint.

> Most instructions I have seen on mounting disks do it in /media, so I find it likely that this is where the op have it...

I disagree with you on both parts of this sentence. There wasn't even a /media directory a few years ago. It was added for removable media. Linux Filesystem Hierarchy Standard says that

>  This (/media) directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks. 

To sum up, I really think that it's a good practice to point out the preferred way of doing things to new users. In the end, of course, it is their choice.

---

### Post by badaveil on 2008-07-10
> **jocko said:**
> What do you mean? Do you mean you don't have permissions to write to the file system?
Paste the outputs from these commands here, so we can see how you have mounted it and which permissions you have set to it:
```
cat /etc/fstab
mount
ls -l /media
```

Results below is after I did another fresh re-installation today and I still can't paste anything in the slave hard disk:

badaveil@mycomputer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d945382-55ba-4181-90c6-80972561a36a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4956f13-73e4-48c9-8a38-255d703c2aae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
badaveil@mycomputer:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/badaveil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=badaveil)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=badaveil)
badaveil@mycomputer:~$ ls -l /media

---

### Post by jocko on 2008-07-10
ok...
If I understand you correctly, your problem is with /dev/sdb1, which is mounted in /media/disk, but by some reason there is no entry in fstab for that disk.
Do you mount it manually on every boot, or are you using some method (other than fstab) for auto-mounting?

Here is how you can set it up correctly:

1. Unmount the disk if it is already mounted:
```
sudo umount /dev/sdb1
```2. Create an  entry in fstab for your disk:
```
gksudo gedit /etc/fstab
```You should make an entry looking something like this (but change the text in red and blue to match your disk's [COLOR=Red]uuid[/COLOR] and preferred [COLOR=Blue]mountpoint[/COLOR]):
```

# /dev/sdb1
UUID=[COLOR=Red]14a06299-44fd-4ed1-b410-7257dc712731[/COLOR] [COLOR=Blue]/media/disk[/COLOR]     ext3    defaults        0       2
```To find out which uuid the partition have, look at the output from this command: 
```
ls -l /dev/disk/by-uuid/ | grep sdb1
```you will get something like this:
```
lrwxrwxrwx 1 root root 10 2008-07-10 13:50 [COLOR=Red]14a06299-44fd-4ed1-b410-7257dc712731[/COLOR] -> ../../sdb1
```The mountpoint can be anywhere in the file system, but usually it is a folder in either /media or /mnt (see the off-topic discussion between me and vivaldi gloria if you want to know the differences)...

3. Make the mountpoint:
```
sudo mkdir [COLOR=Blue]/media/disk[/COLOR]
```4. Make sure you are the owner of the mountpoint:
```
sudo chown [COLOR=Red]username:username[/COLOR] [COLOR=Blue]/media/disk[/COLOR]
```Where [COLOR=Red]username[/COLOR] is your username.

5. Remount it with the new settings:
```
sudo mount -a
```

---

### Post by badaveil on 2008-07-10
Jocko,

Firstly, thank you, thank you for your immediate replies.

>If I understand you correctly, your problem is with /dev/sdb1, which is mounted in /media/disk, but by some reason there is no entry in fstab for that disk.

Yes, you are right about the /dev/sbb1 being mounted in the /media/disk but I'm not It savvy enough to answer the second part.

>Do you mount it manually on every boot, or are you using some method (other than fstab) for auto-mounting?

I was only asked to mount it the first time I clicked on the ext3 icon, from there onwards it goes auto-mounting.

I'm still at my office and will try what you advise when I get home.

Seriously, thanking you again.

---

### Post by badaveil on 2008-07-11
I got permission denied as below:

badaveil@mycomputer:~$ sudo umount /dev/sdb1
[sudo] password for badaveil: 
umount: /dev/sdb1: not mounted
badaveil@mycomputer:~$  /dev/sda1 UUID=8d945382-55ba-4181-90c6-80972561a36a /media/disk ext3 defaults 0 2
bash: /dev/sda1: Permission denied
badaveil@mycomputer:~$ 

The UUID was copied earlier after "gksudo /etc/fstab" was typed:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d945382-55ba-4181-90c6-80972561a36a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4956f13-73e4-48c9-8a38-255d703c2aae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by jocko on 2008-07-15
> **badaveil said:**
> I got permission denied as below:

badaveil@mycomputer:~$ sudo umount /dev/sdb1
[sudo] password for badaveil: 
umount: /dev/sdb1: not mounted
badaveil@mycomputer:~$  /dev/sda1 UUID=8d945382-55ba-4181-90c6-80972561a36a /media/disk ext3 defaults 0 2
bash: /dev/sda1: Permission denied
badaveil@mycomputer:~$ 

The UUID was copied earlier after "gksudo /etc/fstab" was typed:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d945382-55ba-4181-90c6-80972561a36a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4956f13-73e4-48c9-8a38-255d703c2aae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

You obviously didn't read my post properly.
I told you to make an **entirely new line** in your /etc/fstab, not to try to use an already existing line as some kind of command in a terminal...
You have lines for two partitions, both on the same hard drive (/dev/sda1 is the one you have ubuntu installed in, /dev/sda5 is a swap partition). You need one more line for the partition on your second hard drive.
To find out the correct uuid of the partition on your second hard drive (which is NOT in your fstab yet), type this command in a terminal:
```
ls -l /dev/disk/by-uuid/ | grep sdb1
```That will give you a result looking something like this (but with a different uuid):
```
lrwxrwxrwx 1 root root 10 2008-07-10 13:50 [COLOR=Red]14a06299-44fd-4ed1-b410-7257dc712731[/COLOR] -> ../../sdb1
```so copy the uuid from that result (whatever string of characters you see instead of the one I have highligthed in red in the example above).
Now open up your fstab in gedit to be able to add a new line to it:
```
gksudo gedit /etc/fstab
```And add this line to it (but with your uuid for your /dev/sdb1 partition that you got from the above command):```
# /dev/sdb1
UUID=[COLOR=Red]14a06299-44fd-4ed1-b410-7257dc712731[/COLOR] [COLOR=Blue]/media/disk[/COLOR]     ext3    defaults        0       2
```Instead of [COLOR=Blue]/media/disk[/COLOR] in that command, you can have whatever folder name you want (but normally it should be a subfolder in either /media or /mnt), but it has to be a folder that actually exists and does not already contain files or a mounted file system. To create that folder, you should use this command:
```
sudo mkdir [COLOR=Blue]/media/disk[/COLOR]
```And to make sure you own that folder and have permissions to read and write to it:```
sudo chown [COLOR=Red]username:username[/COLOR] [COLOR=Blue]/media/disk[/COLOR]
```Once you have added that line to your /etc/fstab and made sure the mount point (/media/disk in my example) exists and that you own it, you can mount it with:
```
sudo mount -a
```which will try to mount all file systems that are specified in /etc/fstab. After this it will always be automatically mounted when you boot your computer, and you will have full read-write acces to the files on it.

---

### Post by badaveil on 2008-07-16
jocko

I experimented with the fstab line and added the line below and followed the rest like you told me to and it worked:

/dev/sdb1	/media/disk	ext3	defaults	0	2

To make sure things went out A-OK, I rebooted the computer and the secondary hard disk is still on the desktop with full read-write access to the files in it.

Many thanks :guitar:

---

