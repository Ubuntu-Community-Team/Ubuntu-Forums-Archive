---
title: "Fresh install of Ubuntu besides Win10. Forgot to mount Win partition..."
date: 2015-10-05
forum: Hardware
---

### Post by webwiller on 2015-10-05
Yeah I know I know...I shouldnt put myself into these  things without having clear ideas....but the point is that I do it right that time cause it help me calm down. And loose partitions.

I try and explain my complicated partition table (but if unnecessary just put down the terminal code to have my partition rw back and we are fine.

/dev/sda1 -/dev/sda2 is a 1Tb disk devided into 2 partitions for storing data.
/dev/sdb1 is Ubuntu
/dev/sdb is root
/dev/sdb2 is Win (unmounted)
4 is extended (dont go into why pleaseee....
5 is swap

I also  see my disk /dev/sda....but they're mounted and look like directories lost in the middle of an ocean of directory....I'd like to have them as disks....same as my /dev/SDB is, just with the possibility to mount then rw all of them, partition by partiotion

I rememberred to mount all partitions but windows, which was my main and has all my staff right now...cause I had a problem (S.M.A.R.T.) with /dev/sda1 and for safety I backed it up here n there.

[https://www.flickr.com/photos/upload/]("https://www.flickr.com/photos/upload/")

[IMG]https://www.flickr.com/photos/upload/[/IMG]

---

### Post by Bucky Ball on 2015-10-05
How about the output from 

```
sudo blkid
```

Please use [code] tags. See last link in my signature for how.

[QUOTE=webwiller]I also see my disk /dev/sda....but they're mounted and look like directories lost in the middle of an ocean of directory....I'd like to have them as disks....same as my /dev/SDB is, just with the possibility to mount then rw all of them, partition by partiotion[/QUOTE]

Not quite sure what you mean. Could you attach a screenshot? The disk itself doesn't actually show up but the partitions on it do? 

sda is the disk, sda1 is a partition on it and what shows up for you to store data on. :-k

---

### Post by webwiller on 2015-10-05
> **Bucky Ball said:**
> How about the output from 

```
sudo blkid
```

Please use ```
 tags. See last link in my signature for how.



Not quite sure what you mean. Could you attach a screenshot? The disk itself doesn't actually show up. The partitions on it do. sda is the disk, sda1 is a partition on it and what shows up for you to store data on. :-k


[CODE]web@web-desktop:~$ sudo blkid
[sudo] password for web: 
/dev/sda1: UUID="01D0FE096804F320" TYPE="ntfs" 
/dev/sda2: UUID="01D0FE09D53140C0" TYPE="ntfs" 
/dev/sdb1: UUID="0e6b0951-9e0f-4949-bd26-d356c6d69bb2" TYPE="ext4" 
/dev/sdb2: UUID="ECDE4ECFDE4E922E" TYPE="ntfs" 
/dev/sdb5: UUID="4669fabf-c8c4-41df-8c56-79e24ff72166" TYPE="swap" 
web@web-desktop:~$ ^C

```

---

### Post by webwiller on 2015-10-05
OT: Which is the easiest and best way to post a screenshot??!!

---

### Post by Bucky Ball on 2015-10-05
I'm not using Ubuntu but I get there via Applications> Accessories> Screenshot. You should be able to find it using the Dash I think.

I can see fine by the output in your last post, though. Still not quite sure what the question is, sorry. :) How do they look different?

---

### Post by yancek on 2015-10-05
I'm not sure what your actual questions is.  If you have a recent standard installation of Ubuntu, you should see icons for the various partitions on the various drives in the panel on the left.  Mouse over them to find what they are.  If you open the nautilus filemanager, you can go to the /media/web directory and find them there, if web is your actual user name.

---

### Post by webwiller on 2015-10-05
I made a recent mess actually. I used to run Win10 only on thidìs PC, on the 256GB SSD A partioned 1TB into 2*500GB for Data Storage. Lately I decided to move lot of staff away , and resized /dev/sdb2 to make space for Ubuntu. I mounted wrong somewhere & the result is that I cannot mount into my Win partition, getting errors. At the same time I did mount the other 2+500GB partitions, but I mounted them as /data1 and /data2....but now in this way they result as directories...which I dont like....

The question is:

How to recover the possibiliti ti mount in rw /dev/sb2, the ntfs win10 partition, but resulting as an HDD, not a classic "mounted directory"(I'm thinking windows way if you follow me...)
And how to remount the other 2*500GB partitions (/data1 & /data2) but also appearing as they are: HDD, which I can mount in rw.

TY in advance:)

---

### Post by yancek on 2015-10-05
Windows doesn't understand Linux permissions so the standard method with rwx isn't going to work.  You will need to use umask.  Do you have entries in the /etc/fstab file of Ubuntu for the different windows partitions?  You can mount the different partitions outside the standard /media/username mount point with an entry in fstab.  I don't use windows but you can get info just googling umask partitions for windows on LInux or something similar.

> How to recover the possibiliti ti mount in rw /dev/sb2, the ntfs win10  partition, but resulting as an HDD, not a classic "mounted  directory"(I'm thinking windows way if you follow me...)

No, I don't.  If you just want an icon that looks like a hard drive instead of a folder I suppose you could do that.  You should already have that in the left panel on the Desktop.

---

### Post by Bucky Ball on 2015-10-05
You can think the Windows way, but that won't change the way things work in Linux where *everything* is mounted as a directory, including partitions. They have to be mounted somewhere. 'The Windows way' makes them *look* like they are drives, but they're not. They are partitions, exactly as they are in Ubuntu. That's just the way it is ...

Calling partitions D, C, E, etc., is, in fact, more confusing to a Linux user and gives less detail as it gives no details about which partition on which drive. sda2 tells you first drive, second partition. 

So, best to think in the 'Linux way' now you're here to avoid confusion. Which other way would you like the partitions to mount? As C, D, E? That is not going to happen, although you could create the mount points C, D and E. :)

```
sudo mkdir /media/C
```

---

### Post by Mark Phelps on 2015-10-06
Win10 uses a new form of Hiberation which is enabled BY DEFAULT -- meaning, you have to disable it yourself, otherwise.  If you don't disable it, every time you shut down Win10 it keeps all open Windows volumes still mounted -- which will prevent you from mounting those same volumes in a Linux distro.  As long as that hibernation is enabled, there is no way around it.

That hibernation is known as FastStartup (unrelated to Fast Boot):

There are two ways to disable FastStartup; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

