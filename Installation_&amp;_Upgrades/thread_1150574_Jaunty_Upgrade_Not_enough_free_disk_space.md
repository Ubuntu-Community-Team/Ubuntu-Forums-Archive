---
title: "Jaunty Upgrade: Not enough free disk space"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by egtux on 2009-05-06
Hello,

I have Ubuntu 8.10 when I try upgrade to Jaunty using 'Update Manager'. I had this error :(

> 
Not enough free disk space
The upgrade is now aborted. The upgrade needs a total of 907M free space on disk '/usr'. Please free at least an additional 907M of disk space on '/usr'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


My '/usr' has 1.8 GB and 100% of usage , How can i solve this problem?

---

### Post by Partyboi2 on 2009-05-06
You could always use gparted  (System>Admin>Partition Editor) from a ubuntu live cd to increase the size of the partition.

---

### Post by drs305 on 2009-05-06
I wrote a guide on finding and recovering lost disk space. If your /usr partition is a separate partition, which would be unusual unless you created it that way, you need to look at it's contents and see what is taking up the space. If your /usr really is a separate partition with only 1.8GB it is probably too small and you need to make the partition larger. If you installed a lot of third party apps in the /usr directory you could try moving them (reinstalling) them somewhere else. 

Normally it it just part of the larger system partition, where the chances of freeing up space become much greater. In either situation, you are going to have to delete files or expand the partition.

Lost disk space, unless the partition was too small to begin with, is usually the result of unemptied trash bins, backups made to the wrong location, or accumulated packages that can be removed from the system.

Refer to this guide for steps to recovering lost space. If you can't figure it out, post the results of the "sudo du / -h --max-depth=1 " command from the guide.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by egtux on 2009-05-06
Thanks Partyboi2 for your response,but is this effect data on this partition ? and can you recommend me a tutorial?

---

### Post by Partyboi2 on 2009-05-06
It should not effect the data, but it is always recommended to backup your important stuff before working on any partitions.
You can get a general idea on how to resize partitions from this link. 
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
It all depends on what your setup is, as to which partition you need to shrink down to provided unallocated space to increase the size of the partition /usr partition.

Are you sure your /usr is on its own partition and not under /?

---

### Post by egtux on 2009-05-06
Thanks Drs,

I will follow your How-to and this is output of command you sent
> 
8.9M    /root
112M    /lib
4.0K    /mnt
du: cannot access `/home/mase/.gvfs': Permission denied
899M    /home
4.0K    /initrd
7.1M    /sbin
274M    /var
0    /sys
21M    /opt
4.7M    /tmp
12M    /boot
15M    /etc
6.1M    /bin
4.0K    /srv
du: cannot access `/proc/7646/task/7646/fd/3': No such file or directory
du: cannot access `/proc/7646/task/7646/fdinfo/3': No such file or directory
du: cannot access `/proc/7646/fd/3': No such file or directory
du: cannot access `/proc/7646/fdinfo/3': No such file or directory
0    /proc
3.0M    /dev
1.9G    /usr
16K    /lost+found
27G    /media
30G    /

Also, yes I separate it with this small size because my entire HD is only 40GB

that's all

---

### Post by drs305 on 2009-05-06
If you can open gparted and then post a picture of your partitions we might be able to give you an idea of how to make /usr larger. I've included one just so you know what we'd like to see.

First unmount your non-system partitions, if any, then start gparted. When you run the first command you will get messages about partitions being busy, that is ok.
```

sudo umount -a  
gksu gparted

```


**[COLOR="DarkRed"]ADDED:[/COLOR]** 
In recent versions of ubuntu there is an app called System Janitor. You access is from System, Administration, Computer Janitor. I noticed it finds unnecessary libraries in the /usr/bin folder and may help your situation.

---

### Post by egtux on 2009-05-07
**Partyboi2** thanks very much,Yes my /usr is not under /

> If you can open gparted and then post a picture of your partitions we might be able to give you an idea of how to make /usr larger. I've included one just so you know what we'd like to see.

thanks **drs305**, i attach image here, can i use System Janitor for 8.10?

---

### Post by Partyboi2 on 2009-05-07
I would suggest working through the how-to that drs305 posted in post #3 to try and free up some space and if there is anything on the LIFE, MEDIA, CONTAINER partitions  that you can move to another location like cds, dvds, external hard drive I would suggest doing that. If you can ideally free up 1 gig from LIFE then you could use that 1 gig to add to /usr.

---

### Post by drs305 on 2009-05-07
egtux,

I am sure I don't need to tell you that you need a larger drive.

I couldn't find computer-janitor-gtk listed in intrepid.

I started to type up instructions on how to move a bit of space from / to /usr but if it worked at all it would just barely meet the minimums and would then probably say you needed more space on /.

Your ubuntu partitions really don't have the space to do it. You need to free space in one or more of your other partitions, which are also all full. Moving things around just to get a small bit of space is not a long term solution - you would most likely have the same problem in a short time.

The solution I would recommend would be to create space in your LIFE partition by some means - copying old data to CD, etc so that you could reinstall ubuntu/xubuntu (smaller) into a partition at least 5GB. Having separate partitions doesn't really save or create space, so I would skip the separate /usr partition on a reinstall. Sorry I didn't provide a better solution.

---

### Post by egtux on 2009-05-13
Thanks all,

Of course, I agree with you about my disk space :(

By the way i upgraded to Jaunty by remove all gnome packages and install **xubuntu-desktop** package , then upgrade it to last version :) and i have now more free space.

It is my second time to use Xfce , first one from years ago and it is very bad memory but this time it is appear nice my pc more faster.

Thanks again **Partyboi2** and **drs305**

---

