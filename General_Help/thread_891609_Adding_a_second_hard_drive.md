---
title: "Adding a second hard drive"
date: 2008-08-16
forum: General Help
---

### Post by YigalB on 2008-08-16
I added a second hard drive. It was detected by Ubuntu - I can see it under /media, called "disk". But I cant find a way how to actually use it - it wont give me permission to create directories. I don't get even asked for root password.
1- how can I open it for access?
2- can i just tell Ubuntu to add the extra storage into it;s work space, so I will not have to remember which hard drive I need?
3- The hard drive is 40GB, of which I can see 33.8GB free. Does it make sense? How can I claim the whole 40GB? ( I formatted via GPARTED, but without any success).

Thanks

---

### Post by Hilipatti on 2008-08-16
See [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

You won't actually be able to get 40 GBs of space..

---

### Post by YigalB on 2008-08-16
Thanks for the info.

But how do I add make Ubuntu to let me use those many bytes I got?

---

### Post by clueless on 2008-08-16
You should set a mount point in fstab.
To do that you need to know:
1) where is the partition or hard drive. If, for example, your new hard drive has only one partition and it is connected on the second SATA channel it will be /dev/sb1
2) how is the drive formated (ntfs, ext3, ext2 etc.)

Then you open your fstab file and enter a new line. I, for example, have added a new hard drive and would like to use a partition. It is the 4th partition of the hard drive mounted on the second channel and I want to mount it under /media/new_hd:
```

/dev/sdb4 /media/new_hd ext3    relatime,user_xattr   0   2

```

I created a blank directory called new_hd under /media:
```

sudo mkdir /media/new_hd

```

and changed the permissions so that I can have read/write privileges:
```

sudo chown clueless:clueless /media/new_hd

```

I have no idea if there is some tool to do this in Ubuntu.

---

### Post by linux_tech on 2008-08-16
1. make a directory
2. change permissions on dir
3. mount the dir
4. to make permanent add line to fstab

this page explains commands-
[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)
(use sudo before commands)
[http://psychocats.net/ubuntu/mountwindows#fstab](http://psychocats.net/ubuntu/mountwindows#fstab)

---

### Post by az on 2008-08-16
> **YigalB said:**
> Thanks for the info.

But how do I add make Ubuntu to let me use those many bytes I got?

What version of Ubuntu are you using?

Also, see here:
[https://help.ubuntu.com/community/Mount/USB#User%20Privileges](https://help.ubuntu.com/community/Mount/USB#User%20Privileges)

---

### Post by YigalB on 2008-08-16
I use Ubuntu 8.04, Kernel 2.6.24-19-generic
GNOME 2.22.3.

Is there a way to add it via GUI and not to change system files?
I dont like the file way because I can make mistakes.

BTW - my main disk (160GB) is connected via SATA
this additional disk(40GB) is connected via IDE, and it's mounted as ext3

---

### Post by drs305 on 2008-08-16
> **YigalB said:**
> I use Ubuntu 8.04, Kernel 2.6.24-19-generic
GNOME 2.22.3.

Is there a way to add it via GUI and not to change system files?
I dont like the file way because I can make mistakes.

Take a look at pysdm. It's a gui-based fstab editor. I've written a tutorial, including a "3 Minute Guide" that covers what you need to get it working. See the link in my signature line.

You can still make mistakes, and it does have to change system files, but it will be safer than changing them yourself. ;-)

---

### Post by carolinason on 2008-08-16
A 40GB drive doesn't have 40GB of space

> 1 GB == 2^30 bytes
But according to the hard drive company
> 1GB = 10^9, so (40 * 10^9) = 40GB.

PC thinks base 2
> 1GB == 2^30
so,
> 40 * 10^9/2^30 = 37 GB
and Linux wants 5%, so you can't fill the drive
> 37 GB * 5% = ~35GB
If your drive is in the primary slave position. You can drop the 5% to 3 % by
```
tune2fs -m3 /dev/sdb1
```

---

### Post by YigalB on 2008-08-16
Thanks, DRS305!!

I located your "3 minutes guide" using google, but I am stuck at:
[I]Into the Options window, copy/paste the bold portion of the applicable line (there should be no spaces): 
For ext2/3 data partitions:
root partition ( / ):    **relatime,errors=remount-ro**
home partition (/home):  **nodev,nosuid,relatime**
other partitions:        **defaults,users**[/I]

I am stuck because I have a one line "options" window, and it is written inside already "defaults".
Should I simply copy the bold lines as is? what about the toot/home/other partitions?

Thanks

PS
Why couldn't it be as simple as: "Ubuntu detected new hard disk, press here to increase your disk space without knowing how ubuntu does it for you, same way you eat ice-cream without knowing how was it done"?

---

### Post by drs305 on 2008-08-16
> **YigalB said:**
> Thanks, DRS305!!
I am stuck because I have a one line "options" window, and it is written inside already "defaults".
Should I simply copy the bold lines as is? what about the toot/home/other partitions?


I'm assuming from what you stated this is an ext3 partition. If so, then yes, just copy/paste the contents over "defaults". Defaults will be replaced by what you copied.

You would repeat the process for each of your partitions. They should appear in the left pane. Each time you select one for the first time you will get the 'configure' question.

> 
PS
Why couldn't it be as simple as: "Ubuntu detected new hard disk, press here to increase your disk space without knowing how ubuntu does it for you, same way you eat ice-cream without knowing how was it done"?

If it were easy, there wouldn't be a need for the ubuntu forums would there?  ;-)

---

### Post by carolinason on 2008-08-16
relatime should be adequate

> /dev/sdb1    /path/to/mount/point   ext3    relatime     0  2

---

### Post by drs305 on 2008-08-16
> **carolinason said:**
> relatime should be inadequate.

Do you mean 'unnecessary'? It *is* the default now, if that's what you meant, and thus wouldn't need to be in the options.

---

### Post by carolinason on 2008-08-16
spell check sorry(it's a madhouse here today), correction made to post

replace inadaquate with adequate

---

### Post by YigalB on 2008-08-16
> root partition ( / ): relatime,errors=remount-ro
home partition (/home): nodev,nosuid,relatime
other partitions: defaults,users

Sorry for being slow:
In the left window (partition list) I have SDA, and SDA1 under it.

I also have SDB and SDB1, SDB5 under it - but they relate for the original disk.
I don't have any root partition, home partition, other partitions.

The options window is for one line only. So how do I paste 3 lines inside? one after the other? how do I relate it to the root partition, home partition, other partitions?

and yes- it's ext3.

---

### Post by drs305 on 2008-08-16
> **YigalB said:**
> Sorry for being slow:

No problem. I'm going to send you a PM.

---

