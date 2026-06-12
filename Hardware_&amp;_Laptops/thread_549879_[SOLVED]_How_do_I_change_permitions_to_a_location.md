---
title: "[SOLVED] How do I change permitions to a location?"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by the.unclean.cpp on 2007-09-13
Hello. I have a problem accesing one of my HDDs. I managed to automount it at startup, but I can access it only if I'm root. I found a work-around for XMMS by starting it from the Terminal with : sudo xmms. The problem is that this trick doesn't work for all the programs, for example it's useless for VLC media player. How do I gain full access to that HDD?

Edit: It's a NTFS partition.

---

### Post by startherepodcast on 2007-09-13
Hey,

You could try running:

```
sudo nautilus
```

This should give you a file browser. In the file browser you can then right click the file or drive which you want to set the permissions of and select properties. In the properties set the file permissions and then you may want to click apply to enclosed files and folders.

Hope This Helps

Startherepodcast

---

### Post by the.unclean.cpp on 2007-09-13
> **startherepodcast said:**
> Hey,

You could try running:

```
sudo nautilus
```

This should give you a file browser. In the file browser you can then right click the file or drive which you want to set the permissions of and select properties. In the properties set the file permissions and then you may want to click apply to enclosed files and folders.

Hope This Helps

Startherepodcast

I tried that already, but with no use :( It says that it's a read-only file and I can't change permissions...

---

### Post by bapoumba on 2007-09-13
I will probably not be able to help you with this, but is it a NTFS partition?
Others will :)

---

### Post by the.unclean.cpp on 2007-09-13
> **bapoumba said:**
> I will probably not be able to help you with this, but is it a NTFS partition?
Others will :)

Silly me, I forgot to mention that. Yeah, it's a NTFS partition.

---

### Post by bapoumba on 2007-09-13
[http://ubuntuforums.org/showthread.php?p=685273]("http://ubuntuforums.org/showthread.php?p=685273")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows")
Try these links.

---

### Post by rsambuca on 2007-09-13
A couple of things.  First, I really would discourage you from running programs as sudo.  Kind of like playing with fire.

Anyways.  Are you just going to be using these files as read-only?  If so, then we can change your fstab file.  Post the output of

cat /etc/fstab

---

### Post by Bothered on 2007-09-13
You can get the permissions you want on an ntfs partition using ntfs-3g and customising your /etc/fstab file.

First install ntfs-3g:

```
sudo apt-get install ntfs-3g
```

Then back up your fstab file in case you mess it up:

```
sudo cp /etc/fstab /etc/fstab.bak~
```

and then edit your fstab:

```
sudo gedit /etc/fstab
```

Find the line that corresponds to the partition causing you problems (post your /etc/fstab if you're not sure which this is) and change it to:

```
[file system] [mount point] ntfs-3g defaults,umask=[desired mask],uid
=[desired owner],gid=[desired group] 0 1

```

where [file system] and [mount point] are left unchanged, [desired owner] is the owner you would like for all files and folders on the partition, [desired group] is the group you would like for all files and folders on the partition and [desired mask] is an octal permissions mask.

Note that [desired mask] is not the octal permission you would like - it is the mask. Hence is you want all files on the partition to have permission "xyz" then [desired mask] must be "(8 - x)(8 - y)(8 - z)". See [here]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation") for help on octal notation of permissions.

EDIT: You might also want to add ",locale=[your locale]" after the gid, but I'm not sure how essential this is.
EDIT2: You can get the correct locale by installing ntfs-config, letting this initially set up your ntfs partition and then editing /etc/fstab to set the permissions for it.

---

### Post by aysiu on 2007-09-13
There are so many things wrong here...

First of all, why is XMMS on an NTFS partition? Shouldn't it be on Ext3?

Secondly, do **not** launch graphical applications with *sudo*. You should use *gksudo* or *kdesu*. More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

Lastly, the easiest way to mount NTFS with read/write permissions is graphically, following [this tutorial](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html).

---

### Post by Bothered on 2007-09-13
> **aysiu said:**
> Secondly, do **not** launch graphical applications with *sudo*. You should use *gksudo* or *kdesu*. More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

I didn't know that. That's pretty important ...

> **aysiu said:**
> Lastly, the easiest way to mount NTFS with read/write permissions is graphically, following [this tutorial](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html).

Using ntfs-config is a good place to start (it'll select the correct locale for you for starters) but if you want specific permissions set on the partition you need to manually edit /etc/fstab.

---

### Post by rsambuca on 2007-09-13
> **aysiu said:**
> First of all, why is XMMS on an NTFS partition? Shouldn't it be on Ext3?

I was assuming he was just trying to access the media files on the ntfs drive, but the players can't access the files due to permissions.

Also, aisyu, with reference to the graphical tutorial - that is great, but what Bothered suggested is by no means "wrong".  It is just a different way of doing it than you like.

---

### Post by the.unclean.cpp on 2007-09-13
Thanks for your answers! I am just trying to access the partition for read-only purpose.
The fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=071098f2-f583-4150-9f54-bfb133c68fd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a10485fc-aef0-4e5c-b2c2-c2cced06523c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/iStuff auto defaults 0 0

```

Note: the last line was not there by default. I added it myself hoping that it will solve my problem, but it didn't.
Another note: I tried with ntfs-config, but it doesn't detect my second hdd(sdb1).
As you can see in the fstab file, linux is installed on sda.
I hope you can help me, and thanks for the answers you already offered.

---

### Post by Bothered on 2007-09-13
What are the permissions for /media/iStuff? That could be accessible only by root. Try making it accessible to all with:

```
sudo chmod a+r /media/iStuff
```

Also, if you only want read-only access then ntfs-3g is not needed.

---

### Post by rsambuca on 2007-09-13
If you are sure that sdb1 is the correct drive then try changing the last entry of your fstab to this:```
/dev/sdb1    /media/iStuff ntfs  nls=utf8,umask=0222 0    0
```

---

### Post by the.unclean.cpp on 2007-09-13
Thank you! It worked. I am so relieved!
I owe you guys one!

---

