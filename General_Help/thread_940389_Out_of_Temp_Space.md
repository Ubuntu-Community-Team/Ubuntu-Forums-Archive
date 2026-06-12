---
title: "Out of Temp Space"
date: 2008-10-07
forum: General Help
---

### Post by twodayslate on 2008-10-07
I am out of temp space. I believe this is what is making me not able to access root functions (sudo nautilus etc;). This a  pain. How do I fix this? Just delete everything in tmp is just a temp fix. 

```

There is not enough room on the disk to save /tmp/o+kqdM8G.zip.part.
Remove unnecessary files from the disk and try again, or try saving in a different location.
```

---

### Post by 3rdalbum on 2008-10-07
You should be able to free up some space with:
```
sudo apt-get autoclean
```

If sudo doesn't work, then you will need to boot into recovery mode through the Grub menu.

---

### Post by twodayslate on 2008-10-07
> **3rdalbum said:**
> You should be able to free up some space with:
```
sudo apt-get autoclean
```

If sudo doesn't work, then you will need to boot into recovery mode through the Grub menu.
That fixed it a bit. But that is only a temporary fix, this will happen again. What do I do to make my temp bigger? Mess with the partitions I assume.

---

### Post by jerome1232 on 2008-10-07
Well if you have alot of free space somewhere, you can shrink a large partition and make a new one, then mount it as /tmp.

The output of a few commands may help us with some suggestions
(a couple screenshots from gparted would suffice too)
```
sudo fdisk -l
df -h
```

that's a lowercase letter L after the dash

---

### Post by twodayslate on 2008-10-07
Thanks for the great support!```
~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           24201       24321      971932+  82  Linux swap / Solaris
/dev/sdb2               1          61      489951   83  Linux
/dev/sdb3              62        1277     9767520   83  Linux
/dev/sdb4            1278       24200   184128997+  83  Linux

Partition table entries are not in disk order
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             9.2G  7.4G  1.4G  84% /
varrun                506M  112K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   76K  505M   1% /dev
devshm                506M   48K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb2             464M  115M  325M  27% /boot
/dev/sdb4             173G   56G  109G  35% /home

```

---

### Post by Elfy on 2008-10-07
I would use the partition editor on the live cd to shrink sdb4 and give the space to sdb3. You'll want to shrink sdb4 from the lefvt so that it's contiguous with sdb3.

Backup - and it could take a long time

You can see from df -h that you have used 84% of your / drive

---

### Post by Idefix82 on 2008-10-07
I would recommend you to shrink the /home partition and to create a separate /var and maybe also a separate /tmp partition. This way when these two get cluttered up it won't halt your whole system.
I think around 4 gig for these two together should be more than enough.

Further, while it is a very minor point, half a gig for /boot is quite generous. How many different kernels have you got? In my /boot partition only 44MB are occupied. In any case, 200MB should be enough for your /boot partition if you are not going to always have four or five kernels installed

---

### Post by jerome1232 on 2008-10-07
Just to check and see what exactly is eating space in / one more command; This will tell us what directory is using the most space, and thus be the one that needs to be migrated out. (depending on what it is)
```
sudo du -hx --max-depth=1 /
```

/home is definitely the one we want to shrink up though.

---

### Post by twodayslate on 2008-10-07
Thank you everyone for a quick response.> **jerome1232 said:**
> Just to check and see what exactly is eating space in / one more command; This will tell us what directory is using the most space, and thus be the one that needs to be migrated out. (depending on what it is)
```
sudo du -hx --max-depth=1 /
``````
3.2G	/usr
4.0K	/mnt
4.0K	/srv
0	/dev
16K	/lost+found
0	/proc
706M	/lib
288K	/tmp
3.0K	/boot
5.2M	/bin
4.0K	/home
6.5M	/sbin
51M	/root
4.0K	/opt
12K	/Recycled
4.0K	/initrd
20K	/media
39M	/etc
3.3G	/var
0	/sys
7.2G	/

```

---

### Post by drs305 on 2008-10-07
You can check all your trash bins to see if you have a good deal of trash hanging about your system. Check my signature for a link on how to find and delete trash.

You can also check for very large files, which may have grown without you knowing about them:
```
sudo find / -size +500M
```

---

### Post by jerome1232 on 2008-10-07
> **twodayslate said:**
> Thank you everyone for a quick response.```
[COLOR="Red"]3.2G	/usr[/COLOR]
4.0K	/mnt
4.0K	/srv
0	/dev
16K	/lost+found
0	/proc
706M	/lib
288K	/tmp
3.0K	/boot
5.2M	/bin
4.0K	/home
6.5M	/sbin
51M	/root
4.0K	/opt
12K	/Recycled
4.0K	/initrd
20K	/media
39M	/etc
[COLOR="Red"]3.3G	/var[/COLOR]
0	/sys
7.2G	/

```

Red is your space eaters.

/usr is for programs that get installed (you have ALOT lol)
/var is where logs and some persistent tmp files are stored (/var/tmp get's cleared ~ every 7 days I think)
I also notice 51MB in /root, which is where roots trash is sometimes kept, I would check in there for trash and empty it (but 51MB isn't breaking you for space)


So since you install so many programs You might want to migrate out /usr in addtion to /var, they are useing up nearly all your space in /. You will have to do your operations from a live cd, I always suggest backing up your data before playing with partitions. Matter of fact I make monthly backups anyways.

---

### Post by twodayslate on 2008-10-07
> **drs305 said:**
> You can check all your trash bins to see if you have a good deal of trash hanging about your system. Check my signature for a link on how to find and delete trash.

You can also check for very large files, which may have grown without you knowing about them:
```
sudo find / -size +500M
```
Here is everything excluding the home files ```
/proc/kcore
find: /proc/7161/task/7161/fd/4: No such file or directory
find: /proc/7161/task/7161/fdinfo/4: No such file or directory
find: /proc/7161/fd/4: No such file or directory
find: /proc/7161/fdinfo/4: No such file or directory
                       //REMOVED ALL /home files
/var/log/messages.0
/var/log/kern.log.0
/sys/devices/pci0000:00/0000:00:00.0/resource3

```

I don't know if the /tmp issue is causing this...
```
~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.4.0
Initializing nautilus-share extension

(nautilus:7328): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7328): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7328): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7328): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```

---

### Post by jerome1232 on 2008-10-07
just an fyi some graphical apps don't play well when you use sudo, whenever you want to launch a graphical app with root priviliges use gksu for gnome/xfce and kdesu for kde instead.

So the proper way to launch nautilus as root is:
```
gksu nautilus
```

or if you wanted to launch it as another user on the system

```
gksudo -u joe nautilus
```

---

### Post by twodayslate on 2008-10-07
> **jerome1232 said:**
> just an fyi some graphical apps don't play well when you use sudo, whenever you want to launch a graphical app with root priviliges use gksu for gnome/xfce and kdesu for kde instead.

So the proper way to launch nautilus as root is:
```
gksu nautilus
```

or if you wanted to launch it as another user on the system

```
gksudo -u joe nautilus
```
Ran both and same error
```
$ gksu nautilus
/home/name/.themes/ClearlooksGray/gtk-2.0/gtkrc:330: Overlay image options specified without filename
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.4.0
Initializing nautilus-share extension

(nautilus:7428): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7428): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7428): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7428): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

```

Synaptic says I have 1648 things installed.

---

### Post by jerome1232 on 2008-10-07
I didn't think launching it via sudo vs  gsku was the problem, I was just giving you an fyi so you know that from now on.

You may want to try reinstalling it, I've seen in one post where this resolved the issue.

```
sudo apt-get --reinstall install nautilus
```

You may want to browse through [this]("http://ubuntuforums.org/showthread.php?t=820564&page=5") thread as it deals with the issue as well.

edit: You'll have to wade through alot of useless junk in that thread, pay more attention to what the mod's have to say on certain matters.

---

### Post by Idefix82 on 2008-10-08
Since your /usr directory eats up so much space, you might want to check whether there are any packages that aren't actually needed. There is a program that helps you identify "orphaned" packages, ie those which were installed as a dependency of something but are not needed anymore because this something is gone by now. There is also a plugin for Synaptic which highlights for you these orphaned packages.
[Here is a description]("http://ubuntuforums.org/showthread.php?t=140920") of how to install this program and how to set up the filter in Synaptic. It's very easy.

BUT:
1. The tutorial I sent you was written by a guy who first does things and then deals with the consequences. Personally, I would say that this is a bad way of doing things, unless you really have nothing to lose. So don't delete things as lightheartedly as this tutorial suggests.
2. On a related note: don't just purge all the orphaned packages. Just ask the filter to show them to you, then read the descriptions and the dependencies (right click on the package, then properties) and then decide whether or not you need it. Please read the following thread to illustrate my point: [http://ubuntuforums.org/showthread.php?t=939261]("http://ubuntuforums.org/showthread.php?t=939261")
3. The search depth of this filter is one level, meaning that after you delete an orphaned package, others may become orphaned. So repeat the process until the only packages that are shown as orphaned are ones that you actually want to keep.

Finally, if you are unsure whether you can safely delete something, just report back here.

---

### Post by hyper_ch on 2008-10-08
10 GB is small for a root partition... :( that's one of the reasons I don't run a seperate home anymore.

---

### Post by mixmaster on 2008-10-08
There is a quick and simple fix for this which does not require repartitioning.  Simply replace /tmp with a symbolic link to /home/tmp.
You may need to boot the live CD at some stage to do this.

---

