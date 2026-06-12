---
title: "Doesn't seem to detect my DVD/CD Drive."
date: 2008-09-05
forum: Hardware
---

### Post by tracetheace on 2008-09-05
I'm running Ubuntu 8.04. It's to the point that I can't even open the drive by pressing on the actual button on my DVD/CD drive. Also I can't seem to find anything in ubuntu that refers to my drive besides the 'Blank Disk' on my Desktop and in Places>Computer.

So can some one please tell me how to mount? my dvd/cd rom drive.
thanks.

P.S. I'm really newb, 2nd day using Linux based OS. Go easy on me.

---

### Post by tracetheace on 2008-09-05
bump

---

### Post by jleduc on 2008-09-05
I'm having the same problem but with 2 installed drives. If I select Computer I can see the available drives there but they haven't been identified by the OS if I select properties. Is this the same problem you're having

---

### Post by pl@yer on 2008-09-05
> **tracetheace said:**
> I'm running Ubuntu 8.04. It's to the point that I can't even open the drive by pressing on the actual button on my DVD/CD drive. Also I can't seem to find anything in ubuntu that refers to my drive besides the 'Blank Disk' on my Desktop and in Places>Computer.

So can some one please tell me how to mount? my dvd/cd rom drive.
thanks.

P.S. I'm really newb, 2nd day using Linux based OS. Go easy on me.

If it says blank disk then it thinks you have inserted a blank disk or it cant read it. Sometimes it will just keep trying and trying to read a scratched disk and not let you eject it. Try manually ejecting it from the command line using the "lazy" option. 
```

# eject -l /dev/cdrom

```
If you don't have the lazy option you can use lsof to find out what has hold of you cdrom.
```

# apt-get install lsof
# lsof |grep -i cd

```
Then kill the process accessing you cd so you can eject it.

When *nix has an optical drive mounted it wont let you simply open it up (without unmounting it). That is probably what is going on. From the command line you can see what is mounted by simply running.
```

# mount

```
or 
```

# cat /etc/mtab

```
Have a look at those results to see if your cd/dvd is mounted.

 Linux has "device files" which represent your cd/dvd. You mount the device file to a mount point (directory) in order to read it. 
To find out what device files represent your cd/dvd drives you could look in the /dev/ dir and look for the ones that have links to cd or dvd. 
or you could run this from the command line
```

# for d in cd dvd;do ls -l /dev/dvd|grep -i $d;done

```
I usually confirm the device file is the one I'm after by ejecting it. So if you see /dev/cdrom ->/dev/hdb. This means that you can refer to your cdrom device by either /dev/cdrom or /dev/hdb. 
open it
```

# eject /dev/hdb

```
close it
```

# eject -t /dev/hdb

```
make a mount point (dir)
```

# mkdir /media/mycd

```
mount it
```

# mount /dev/hdb /media/mycd

```
Now that the cd is mounted we can look at it using the mount point.
```

# ls /media/mycd

```
Notice that if you try to hit the eject button on the cdrom it should not allow it to open.
unmount it
```

# umount /media/mycd

```
remove your mount point
```

# rm -r /media/mycd

```
now you can eject the cdrom with the button.

That is the manual way to mount umount a cd/dvd or another hdd.
When you get that down you should look into setting up /etc/fstab to simplify the process.
NOTE: there are exceptions to this when the device file is read or written to directly ie music cd, video dvd or burning a cd.

---

### Post by tracetheace on 2008-09-06
Alright, thanks alot, I've gotten closer to solving this problem.
I took a look in my /etc/fstab. The line for my cdrom is there, it looks like:
```
/dev/hda	/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

So once I saw that line and compared it to your suggestions I put them together and came up with this:
```
# mount /media/cdrom0
```

It worked right away, the cdrom was mounted and I could access/use it with no problem.

I rebooted wondering if it would auto mount the drive on startup, seeing as typing 'mount /media/cdrom0' in terminal is the same thing that's in /etc/fstab... right?

But it seems like I have to mount the drive every time ubuntu starts.
I saw that people suggest that you unmount any drive if you're not using it. Is this true?

---

### Post by tracetheace on 2008-09-06
> **jleduc said:**
> I'm having the same problem but with 2 installed drives. If I select Computer I can see the available drives there but they haven't been identified by the OS if I select properties. Is this the same problem you're having

You should have a look in your /etc/fstab
```
sudo gedit /etc/fstab
```

Compare your lines with mine, see if you can make sense of it.

---

### Post by tracetheace on 2008-09-06
YES! I figured out how to mount the drive at startup. :D
Thanks for the help, you pointed me in the right direction.

Funny... I look at it and think, jeez... It doesn't seem so complicated now.
Here's what I did for anyone having this issue.

I took a look in my /etc/fstab by typing in terminal:
```
sudo gedit /etc/fstab #found the line pertaining to my cdrom
```

The line looked like this:
```
/dev/hda	/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

So the important part here is '/media/cdrom0'. So I did as suggested and entered this in terminal.
```
mount /media/cdrom0
```

After doing that I could access my CD-ROM drive, just like normal.
But it wouldn't mount on startup. In fstab all you have to do is change this.
```
/dev/hda	/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```To:
```
/dev/hda	/media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
```
Now don't copy that line exactly! Just change the 'noauto' to 'auto' and reboot to see if it worked.
Now to figure out why my floppy isn't working :D

Thanks Again!

---

### Post by pl@yer on 2008-09-09
I have seen in the **distant past** where the cdrom/dvd drive doesn't spin down after it hasn't been used for a while but left mounted. When you finally umount and eject it that sucker is warm!

I normally set it up as follows, to allow non root access. Replace "username" with your username.
create a mount point username has rights to.
```

$ mkdir /home/username/cdrom

```
edit /etc/fstab and add a second line for your user and change "user" to "users" this allows non root user to mount and umount a drive.
```

/dev/hda	/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda	/home/username/cdrom   udf,iso9660 users,noauto,exec,utf8 0       0

```
now you can mount and umount your drive as "username"
```

$ mount /home/username/cdrom
$ ls /home/username/cdrom
$ umount /home/username/cdrom

```

---

