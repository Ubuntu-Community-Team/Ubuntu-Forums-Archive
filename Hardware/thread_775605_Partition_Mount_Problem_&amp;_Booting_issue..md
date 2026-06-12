---
title: "Partition Mount Problem &amp; Booting issue."
date: 2008-04-30
forum: Hardware
---

### Post by robelliott2125 on 2008-04-30
Hi all,

Sorry about the two threads, but since I'm feeling both these issues are related, I'm hoping someone will help...

Last night, I installed gparted, and formatted a 20gb hdd from NTFS to EXT3, in my bid to remove all winblowz formats off my system completely.

After I'd formatted successfully, I went to copy my documents back to that partition, and it wouldn't let me.

It doesn't allow me to write anything, which isn't helping my bid to do the above.

Well, to top this off, my system also seems to pass Grub without a problem, shows the loading screen (Ubuntu Splash with the orange/black bar) and then goes to what I can only say looks as a Dos screen, pure black, with a flashing cursor in the top left.

Nothing responds, Ctrl Alt F1-F7, except for hitting the escape key, which seems to reboot it (unless the ctrl alt delete did it).
Then I have to boot into recovery mode, and just exit, so I can load into ubuntu.

*Sorry about the longwindedness.*

When I'm shutting down, I saw a lot of red writing last night, and managed to catch something saying "saved to fstab if able to write".

So here is a copy of the fstab file.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=138A0271E3CE81F1 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=DAFCE3AFFCE383DB /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4C8857DB8857C25E /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=1425B8213EBA3559 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc6
UUID=556a9210-925d-49a8-8b68-2852a2101636 /media/sdc6     ext2    defaults        0       2
# /dev/sdc5
UUID=b00d73c8-29ba-484f-9359-97cb765ae9e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

Thank you guys!!!

BTW, if it helps, I'm running Gutsy.

---

### Post by em3raldxiii on 2008-04-30
Wow, that's a crazy FSTAB!  LOL.  Well, the only thing that immediately jumps out at me is that you said you formatted something to EXT3, but all I see in the fstab are EXT2 and NTFS partitions.

Also, you have an entry for "proc" which I don't understand (this doesn't mean it's not supposed to be there, but I have never seen it before).  I would be tempted to comment that one out and see what happens when you boot.  You shouldn't have any trouble putting it back if it causes problems.

And you said you were removing 'windowz off your computer completely' ... but you have a whole slough of ntfs partitions going on.

I think sdc6 is probably your 20GB drive.

When you installed Ubuntu, did you choose to make it format to EXT3?  If so, you have an issue where this fstab is telling us that your root filesystem is on an ext2.  Something is not jiving here.

I know I didn't "fix" anything, but sometimes it helps if you know where the errors are.

---

### Post by robelliott2125 on 2008-04-30
Yes,

Your right, about the EXT2, thats my FS, which I only did as EXT2, since I was having so many issues at the time.  I just wanted to get my installation up and running.

The NTFS partitions are slowly being changed, but I need the 20gb drive, which is currently showing in 'Computer' as 18.6Gb.  However gparted does confirm its EXT3.

The only options I have at the minute on the drive, is to Unmount.  I can't even make a text document on it.

Once I can move everything onto that drive, I can format another to EXT3, and so on.

Tbh, i think a lot of my problems are, because I was installing off an IDE DVDRW which is no longer connected.

I'm just hoping i can get these issues solved.

---

### Post by robelliott2125 on 2008-04-30
[ATTACH]68131[/ATTACH]]

Hopefully the above will help a little...

This is a screenshot from my gparted, which does show the drive as being EXT3.

Thank you.

---

### Post by robelliott2125 on 2008-05-01
Anyone???

I formatted to EXT2 last night, and still unable to write to it.

Its sort of important now I get this hdd back up and running.
Also, Since its still not allowing me to write since formatting it, i'm sure I'm going to encounter the same problem for the other drives.

Thank you,

---

### Post by nsche on 2008-05-01
When you change the partition the UUID changes AFAIK.  You can try to manually mount using the device name as in ```
sudo mount -t ext2 /dev/sdb1 [some directory]
```  The directory you mount it on for now doesn't really matter as long as it exists and is not a directory you need to access otherwise.

---

### Post by robelliott2125 on 2008-05-01
Thanks for your reply.

I'm not really sure what you mean?

I'm completely new to ubuntu, and seem to only be getting it wrong, and messing my system up more.  However I'm keen to learn, and want to solve all the current issues i'm having.

I need to type in;

```
sudo mount -t ext2 /dev/sdb1 [some directory]
```

What does this do?

How come once the drive is formatted, it doesn't mount itself, and register on the system?

---

### Post by robelliott2125 on 2008-05-02
Anyone???  Is there any way I can get ubuntu to re-detect all drives and mount them?

---

### Post by robelliott2125 on 2008-05-02
Seems there has been a further problem...

I no longer have access to any of my drives now.

Only drives showing in Computer are:

Cdrom1
Cdrom2
18.6 Volume:  Disk (The ext3 drive, unwritable)
Filesystem.

I **really** need help now.

---

### Post by robelliott2125 on 2008-05-02
Anyone???

---

### Post by robelliott2125 on 2008-05-02
I've had some help, but i'm now unable to write to the partition...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=138A0271E3CE81F1 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=DAFCE3AFFCE383DB /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4C8857DB8857C25E /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
/dev/sdc1 /media/disk ext3 rw,nosuid,nodev 0 0
# /dev/sdc6
UUID=556a9210-925d-49a8-8b68-2852a2101636 /media/sdc6     ext2    defaults        0       2
# /dev/sdc5
UUID=b00d73c8-29ba-484f-9359-97cb765ae9e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

I'm still needing help, and I don't want to seem as if I'm being rude bumping this hourly, but i do want to get this sorted.

Thank you,

---

### Post by cisforcojo on 2008-05-03
Hey bud,

Sorry I took a while getting to this. I've been a bit busy.
First, you'll want to take a look at this, it's an fstab howto:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Then since you're having trouble with other things, boot up then take a look at:
/var/log/messages

That will report your system startup and you can look for any errors that might be occuring. Feel free to post that file up on this thread if you like. 

Here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8383f18c-114e-4b94-8647-7beb23e3a74a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=168d8606-1727-4a88-9b2f-d861090afbca /home           ext3    relatime        0       2
# /dev/sda3
UUID=d3446fa2-b03e-46a1-9281-36b85205effc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Do you still have trouble booting up Ubuntu? (ie go into safe mode and then exit)

Try this:
Comment out /dev/sdc1 in your /etc/fstab. 
```

sudo gedit /etc/fstab

```
Put a '#' before the /dev/sdc1 line.

Reboot your computer. 

```

sudo mkdir /media/tmp
sudo mount -t ext3 /dev/sdc1 /media/tmp

```

Then try writing files to /media/tmp (your new ext3 partition)
(This is how to use the 'mount' command)

Let me know if this works or not.

The person who told you to run 'mount -t ext2 /dev/sdb1 [some directory]',
what they meant was something like 'sudo mount -t ext2 /dev/sdb1 /media/tmp'
That won't work though because /dev/sdb1 is ntfs, not ext2. You can mount ntfs but that requires ntfs-3g, so let's just get the ext2, ext3 partitions working first :)

---

### Post by robelliott2125 on 2008-05-03
> **cisforcojo said:**
> Hey bud,

Sorry I took a while getting to this. I've been a bit busy.
First, you'll want to take a look at this, it's an fstab howto:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Then since you're having trouble with other things, boot up then take a look at:
/var/log/messages

That will report your system startup and you can look for any errors that might be occuring. Feel free to post that file up on this thread if you like. 

Here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8383f18c-114e-4b94-8647-7beb23e3a74a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=168d8606-1727-4a88-9b2f-d861090afbca /home           ext3    relatime        0       2
# /dev/sda3
UUID=d3446fa2-b03e-46a1-9281-36b85205effc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Do you still have trouble booting up Ubuntu? (ie go into safe mode and then exit)

Try this:
Comment out /dev/sdc1 in your /etc/fstab. 
```

sudo gedit /etc/fstab

```
Put a '#' before the /dev/sdc1 line.

Reboot your computer. 

```

sudo mkdir /media/tmp
sudo mount -t ext3 /dev/sdc1 /media/tmp

```

Then try writing files to /media/tmp (your new ext3 partition)
(This is how to use the 'mount' command)

Let me know if this works or not.

The person who told you to run 'mount -t ext2 /dev/sdb1 [some directory]',
what they meant was something like 'sudo mount -t ext2 /dev/sdb1 /media/tmp'
That won't work though because /dev/sdb1 is ntfs, not ext2. You can mount ntfs but that requires ntfs-3g, so let's just get the ext2, ext3 partitions working first :)

Hi cisforcojo,

Thank you for your reply bud.

Tbh, I've backed everything up, so I don't mind reinstalling, but it comes to a point where when your just reinstalling for the sake of it, and not actually learning why things do what they do.

For instance, the current setup is no longer good for my installation of Linux, so I've been trying to make it less cumbersome, especially with the no titles, apart from in certain windows.

What i've been planning on doing, is once i've copied all files to an empty drive, remove any partitions which are no longer needed, and then format to EXT3.

So regardless of reinstalling, I'm going to have exactly the same problems with the drives, once I've done the next move, and reinstalling 3 more times isn't good, especially to just get the drives to mount.

I did find a tut on how to install a new hdd, which walked you through formatting, and mounting, just every time I try to mount that drive, it says I don't have any permissions to do it.

Here is my fstab again.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b1f4f01-e98a-4c15-858d-56898709b6fa /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=138A0271E3CE81F1 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=DAFCE3AFFCE383DB /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4C8857DB8857C25E /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
/dev/sdc1 /media/disk ext3 rw,nosuid,nodev 0 0
# /dev/sdc6
/dev/sdc1    /media/disk   fat32    defaults     0        0
# /dev/sdc5
UUID=b00d73c8-29ba-484f-9359-97cb765ae9e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

Hope this helps.

Once i've got all the hdd's to EXT3 or Fat32 (for network sharing) i'll happily reinstall to overcome the boot issues...

It'll also mean when I reinstall, I can install a Swap drive, /home drive as well as the main /.  So its not all bad, just need it working to a usable point at the moment.

Hope you can help bud.

Thank you,

---

### Post by cisforcojo on 2008-05-04
Yeah I've installed linux dozens of times. DOZENS. Finishing an install right now actually.

I'm not quite sure what you need help with now to be honest.
I think what you want is to copy everything from your ntfs drives to an empty drive?

If that's so, do something like this:
```

sudo mkdir /media/empty
sudo mkdir /media/ntfs1
sudo mkdir /media/ntfs2
sudo mkdir /media/ntfs3

```

This is just for simplicity's sake. You can make only one directory /media/ntfs and then mount one drive to it, copy everything and then unmount it, mount the next, copy, unmount, and so on.

To unmount a drive:
```
sudo umount /media/ntfs1
OR
sudo umount /dev/sda5
```
You can use the directory or the device, both are ok but regardless you have to use 'sudo'. Note that it's 'umount', not 'unmount'. That's not a typo.

Now that you've got your directories:
```

sudo mount -t ext3 /dev/sdc1 /media/empty
sudo mount -t ntfs /dev/sda5 /media/ntfs1
sudo mount -t ntfs /dev/sdb1 /media/ntfs2
sudo mount -t ntfs /dev/sdb5 /media/ntfs3
```

Now just go into those /media/ntfsX directories and copy everything out to /media/empty.

Here's an example of me mounting my XP partition:
```

cojones@tipping-point:~$ cd /media
cojones@tipping-point:/media$ sudo mkdir xp
cojones@tipping-point:/media$ sudo mount -t ntfs /dev/sda1 /media/xp
cojones@tipping-point:/media$ ls
cdrom  cdrom0  xp
cojones@tipping-point:/media$ cd xp
cojones@tipping-point:/media/xp$ ls
AUTOEXEC.BAT            IO.SYS        pagefile.sys               WINDOWS
boot.ini                MSDOS.SYS     Program Files
CONFIG.SYS              NTDETECT.COM  RECYCLER
Documents and Settings  ntldr         System Volume Information
cojones@tipping-point:/media/xp$ cp boot.ini /home/cojones
cojones@tipping-point:/media/xp$ cd /home/cojones
cojones@tipping-point:~$ ls boot.ini 
boot.ini
cojones@tipping-point:~$ 

```

And there you have it.

---

