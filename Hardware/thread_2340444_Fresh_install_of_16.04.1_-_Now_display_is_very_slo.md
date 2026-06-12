---
title: "Fresh install of 16.04.1 - Now display is very slow"
date: 2016-10-18
forum: Hardware
---

### Post by oygle on 2016-10-18
Here are some brief specs for the computer, which was purchased in 2008 ([ASUS P5Q Pro ]("https://www.asus.com/Motherboards/P5Q_PRO/specifications/")

* ASUS Motherobard -- Model: P5QL-PRO
* 4GB RAM 2x 2GB Sets -- T800UX2GC4 (DDR2 800)
* Asus Video -- Model: Card EN9400GTSLN-HTP-512
* Intel CPU (BX80562Q6600) 2.4Ghz Quad Core 

The computer is "old" but it ran 14.04 very well. There are about 293,000 files and folders to sum at 207 Gb, and file searching and general navigating was never a problem with 14.04. Under 14.04 when a character was keyed in, the character would display immediately as it was being keyed in. Never any problems with the display side of things. There were **NO** Nvidia drivers installed. The video side of things worked just fine without those drivers.

Yesterday, did a fresh installation of 16.04.1 . The installation worked flawlessly. But after a reboot, Kubuntu is **SO** _slow_. When data is entered via Kate, it takes 3 to 4 seconds, sometimes much more, for the characters to appear. Even at a terminal, when a command is entered, it takes about 4 seconds to display. Poor response in other applications.

The display for any 'window' activity is very poor, sometimes black, or parts of grey, and then finally some words appear. Trying to use the mouse results in nothing, video problems; eventually is does display. The main problem is video - VERY **SLOW**.

Just ran a search on Nvidia drivers. Can't seem to find a guide or tutorial on how to trouble shoot this, or install the drivers. ??

Should I try to 'fix' any problems with the Nouveau drivers first ? Where is support for these drivers please ?

---

### Post by oygle on 2016-10-21
There was also a [mount problem]("https://ubuntuforums.org/showthread.php?t=2340456&p=13560128#post13560128") after doing a fresh install of 16.04.1

The mount problem is now resolved, and since then, the display/video side of things has improved a lot. There is now no delay when entering data; although sometimes just a minor delay. The video side of things is still not up to what it was beforehand. Some instances of greyed out or black out video, just for a few seconds. Then it comes good.

So, ...how did a mount problem cause a video problem ??  Was it just resources ?

---

### Post by Bashing-om on 2016-10-21
oygle; Hey, hey ...

Seems to me that the 1st order of troubleshooting is to know IF a driver is loaded .
What returns:
```

sudo lshw -C display

```

as to:
> 
So, ...how did a mount problem cause a video problem ?? Was it just resources ?

possible that resources were taxed to the limit, - system was hunting hunting (??) -  though not likely .


[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by oygle on 2016-10-21
> **Bashing-om said:**
> oygle; Hey, hey ...

Seems to me that the 1st order of troubleshooting is to know IF a driver is loaded .
What returns:

```

sudo lshw -C display

```

```

sudo lshw -C display
```

>  
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:28 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe880000-fe8fffff


> **Bashing-om said:**
> 
as to:

possible that resources were taxed to the limit, - system was hunting hunting (??) -  though not likely .

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

That could well be. The computer is 8 years old now. It has 4 Gb of ram, and I'm not too sure how many Gb the video card was. No doubt as I load more packages (still need to finish the installation), the computer will be more taxed. :)

Thanks for your help.  :D

---

### Post by Bashing-om on 2016-10-21
oygle; K ..

The open source driver nouveau is loaded.
Anything reported in X's log file ?
```

cat /var/log/Xorg.0.log

```

or any errors reports in the GUI log:
```

cat .xsession-errors

```


so far
[INDENT][INDENT]so good
[/INDENT][/INDENT]

---

### Post by oygle on 2016-10-21
> **Bashing-om said:**
> 

Anything reported in X's log file ?
```

cat /var/log/Xorg.0.log

```

It is 505 lines, and because I rebooted, there is another one there with todays date - 473 lines

> **Bashing-om said:**
> 
or any errors reports in the GUI log:
```

cat .xsession-errors

```

There is quite a lot there also. Because of some KMail issues, the backend to it has errors showing in that command.

---

### Post by Bashing-om on 2016-10-21
oygle; Well ..

If those files are too large to paste - between code tags - direct into the forum one can post to a pastebin site and pass that link back here .
Not a thing I can relate to if I do not see the log files .

a busted crystal ball
[INDENT][INDENT][INDENT]is no help
[/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-10-21
> **Bashing-om said:**
> Anything reported in X's log file ?
```

cat /var/log/Xorg.0.log

```

[http://paste.ubuntu.com/23362544/](http://paste.ubuntu.com/23362544/)

> **Bashing-om said:**
> 
or any errors reports in the GUI log:
```

cat .xsession-errors

```

[http://paste.ubuntu.com/23362554/](http://paste.ubuntu.com/23362554/)

---

### Post by Bashing-om on 2016-10-22
oygle; Hey ...

Be careful what I ask for, I may just get it !

What have we here ?
Is this a server that you added the KDE desktop to ?
Or KDE that has the mail server installed to ?

In any event as you know got to fix/remove the mail server .. I can not see the tree for the forest .. and getting way above my experience level .

Now what I might see:
> 
Matched nvidia as autoconfigured driver 0
LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(EE) Failed to load module "nvidia" (module does not exist, 0)

tells me that something is wanting the nvidia driver .. 
As the nouveau driver is installed begs the question :
Did you at some point install the proprietary driver ?
Do you want the proprietary driver installed ?
Give the system what it is asking for ?

Installing the proprietary driver may resolve several issues - but again - I am not real sure . Might be worth a shot and see how the system reacts .

What is installed for nvidia at this time ?
```

dpkg -l | grep -i nvidia

```

Maybe all we need to do for the driver is clean up and re-install ??

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-10-22
> **Bashing-om said:**
> 
Is this a server that you added the KDE desktop to ?
Or KDE that has the mail server installed to ?

In any event as you know got to fix/remove the mail server 

Nope, no mail server. KMail runs akonadi , which I think is some sort of mail server ??

> **Bashing-om said:**
> 
Did you at some point install the proprietary driver ?

Nope, I have always preferred open source to proprietary.

> **Bashing-om said:**
> 
Do you want the proprietary driver installed ?

No thanks.

> **Bashing-om said:**
> 
Installing the proprietary driver may resolve several issues - but again - I am not real sure . Might be worth a shot and see how the system reacts .

I would prefer to try and get the Nouveau driver issues fixed.

> **Bashing-om said:**
> 
What is installed for nvidia at this time ?
```

dpkg -l | grep -i nvidia

```

There is nothing displayed when I try the above command ?

---

### Post by Bashing-om on 2016-10-22
oygle; K

Lemme have a spell to think this over .. maybe have an inkling tomorrow.
Presently I am drawing a blank .

[INDENT][INDENT]study twice
[INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-10-22
okay, thanks.  :)

---

### Post by Bashing-om on 2016-10-22
oygle; Jey;

Well, even after a sleep-on-it; nothing definitive has come to mind.

Let's look at the memory usage:
```

free -m

```
and what the system is automounting:
```

sudo blkid -c /dev/null -o list
cat /etc/fstab
cat /proc/mounts

```

see if these give us any hints on what is going on.

[INDENT][INDENT]just do not know
[INDENT][INDENT][INDENT]maybe this, maybe that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-10-22
> **Bashing-om said:**
> 
Well, even after a sleep-on-it; nothing definitive has come to mind.

We have probably done all we can, considering the "old" computer. The video/display is 'acceptable'. Definitely slower than 14.04, but hey, old equipment.  :)

Here is the info you asked for ...

```
free -m
```
> 
              total        used        free      shared  buff/cache   available
Mem:           3951        1673         241          53        2036        1855
Swap:          4102           6        4095


```
sudo blkid -c /dev/null -o list
```
> 
device                                 fs_type        label           mount point                                UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                              ext4                           /                                          855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
/dev/sda2                              swap                           [SWAP]                                     82e48eb2-0c33-4696-9154-d921da42bbd2
/dev/sda3                              ext4                           /home                                      4925dcbd-b2a1-4db6-adc0-69a9f05ad473
/dev/sdb1                              ntfs                           /media/Winxppro                            8EFC2D0BFC2CEF61
/dev/sdc1                              ext4           Backups         /media/externaldisk                        bbff7f7d-5db9-467c-b1c4-5831cc6870d6


```
cat /etc/fstab
```
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=4925dcbd-b2a1-4db6-adc0-69a9f05ad473 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=82e48eb2-0c33-4696-9154-d921da42bbd2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# / Windows XP pro hard drive - 250 Gb
UUID=8EFC2D0BFC2CEF61  /media/Winxppro  ntfs-3g  defaults,windows_names,locale=en_AU.UTF-8  0 0
# / external hard drive - 500Gb
UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk               ext4    noauto,errors=remount-ro 0       1


```
cat /proc/mounts
```
> 
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=2002760k,nr_inodes=500690,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=404596k,mode=755 0 0
/dev/sda1 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
/dev/sdb1 /media/Winxppro fuseblk rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/sda3 /home ext4 rw,relatime,data=ordered 0 0
tmpfs /run/user/118 tmpfs rw,nosuid,nodev,relatime,size=404596k,mode=700,uid=118,gid=126 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=404596k,mode=700,uid=1000,gid=1000 0 0
/dev/sdc1 /media/externaldisk ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0


---

### Post by Bashing-om on 2016-10-22
oygle; welp;

Again, I can not point a finger at any issues here :
> 
/dev/sdb1 ntfs /media/Winxppro 8EFC2D0BFC2CEF61
UUID=8EFC2D0BFC2CEF61 /media/Winxppro ntfs-3g defaults,windows_names,locale=en_AU.UTF-8 0 0
/dev/sdb1 /media/Winxppro fuseblk rw,relatime,user_id=0,group_id=0,allow_other,blksi ze=4096 0 0

/dev/sdc1 ext4 Backups /media/externaldisk bbff7f7d-5db9-467c-b1c4-5831cc6870d6
UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk ext4 noauto,errors=remount-ro 0 1
/dev/sdc1 /media/externaldisk ext4 rw,relatime,errors=remount-ro,data=ordered 0 0


All looks good . The system is not "ahunt'n we will go" and memory is being managed .
 
I also run on old gear - 2007 - dual core Athlon CPU with 4 Gigs of ram .
I have had no issues with the system loading down or GUI problems ( until I installed a newly released graphics's card that has no support in 14.04 - that has no bearing on your issue ) . I have several installs on this box . xfce is very fast; however I do notice that unity is a lot slower than xfce .. lubuntu and xubuntu also are very responsive  though the champ remains xfce on a minimal install. Honestly, almost as fast installed on a conventional hard drive as that of xubuntu installed on a SSD. Might give it some thought to try a different DE ? Maybe a nice clean fresh start ?

I keep this in mind and see what else I can come up with to know the nature of problem .

[INDENT][INDENT]there is no quit
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2016-10-23
The Xorg log looks good. I would look at KDE's graphics settings (Kwin), since you mention it ran better on KDE4 in Ubuntu 14.04. I wish I could be more specific, but I'm not a big KDE user..
Trying lxqt desktop is another option.

> ```
Matched nvidia as autoconfigured driver 0
```
tells me that something is wanting the nvidia driver ..
As the nouveau driver is installed begs the question :
Did you at some point install the proprietary driver ?
Do you want the proprietary driver installed ?
Give the system what it is asking for ?


No, this is just how X's autodetection works. The message does not indicate a problem in and of itself, nor does it mean the user had the proprietary driver installed previously (or needs to install it).

---

### Post by oygle on 2016-10-23
> **Bashing-om said:**
> 
I keep this in mind and see what else I can come up with to know the nature of problem

Okay thanks, but I think it is as good as it gets, considering the "old" equipment.

> **Temüjin said:**
> The Xorg log looks good. I would look at KDE's graphics settings (Kwin), since you mention it ran better on KDE4 in Ubuntu 14.04. I wish I could be more specific, but I'm not a big KDE user..

When I enter 'kwin'  in the Application Launcher, there is about 10 options, all to do with window settings and display settings. I will try a few of those. That said, the system is "stable" at present, albeit slow in regards to video issues.

> **Temüjin said:**
> 
Trying lxqt desktop is another option.

Okay, I will take a look at that also.  :)

---

### Post by oygle on 2016-10-30
The video problems have now increased. Almost unusable.  :(

Is there anyone I can contact in regards to the Nouveau display driver ?

Some entries from system.log ..

> 31/10/2016 12:31 PM	*****-asus64	org.kde.KScreen[1255]	kscreen: Primary output changed from KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" ) to KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" )
31/10/2016 12:31 PM	*****-asus64	org.kde.KScreen[1255]	message repeated 7 times: [ kscreen: Primary output changed from KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" ) to KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" )]


---

### Post by oygle on 2016-11-13
Plasma has crashed about 30 times today. No doubt associated with the video problems.

---

### Post by oygle on 2016-11-20
Plasma is still crashing many times a day. Plus the video is still slow, sometimes, on boot, no display at all. Plus many KMail bugs.  :(

---

### Post by Bashing-om on 2016-11-20
oygle; Well ..

Back to square one.
A graphic's driver loaded ?
```

sudo lshw -C display

```
Make sure there is no driver conflicts:
```

dpkg -l | grep -i nvidia

```

What does X have to relate ?
```

cat /var/log/Xorg.0.log

```

Now we see what we can make of the sloppyation.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there is no problem
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-11-20
> **Bashing-om said:**
> A graphic's driver loaded ?

```

sudo lshw -C display

```

> 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:28 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe880000-fe8fffff


> **Bashing-om said:**
> 
Make sure there is no driver conflicts:
```

dpkg -l | grep -i nvidia

```

Nothing returned.

> **Bashing-om said:**
> 
What does X have to relate ?
```

cat /var/log/Xorg.0.log

```

[https://paste.ubuntu.com/23504625/](https://paste.ubuntu.com/23504625/)

---

### Post by Bashing-om on 2016-11-20
oyglel Well ..

Nouveau - open source driver - is in use .. and system is happy to use it . I do not see a problem.

How about you load up the system as you normally would with all the apps and browsers and tabs firing away .. and let's see what the system load is:
```

free 

```
for what is in use and what it has to spare .. how is swap here holding up ?

Now what tale
[INDENT][INDENT]gets told
[/INDENT][/INDENT]

---

### Post by oygle on 2016-11-20
Here is the output of the **free** command

---

### Post by Yellow Pasque on 2016-11-20
[http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Tumbleweed-Bad](http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Tumbleweed-Bad)

> Just ran a search on Nvidia drivers. Can't seem to find a guide or tutorial on how to trouble shoot this, or install the drivers. ??

I'm sure Kubuntu has the "additional drivers" GUI somewhere in the menus, but to me, this is easier:
```
sudo apt-get install nvidia-340
```

EDIT: Before you install the proprietary driver, you may want to see if this helps with the video playback:
```
sudo apt-get install mesa-vdpau-drivers vdpau-va-driver
```

---

### Post by oygle on 2016-11-20
> **Temüjin said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Tumbleweed-Bad](http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Tumbleweed-Bad)

Thanks for the link to the article. I'm not sure how OpenSuse and Kubuntu 'line up' in regards to releases ??

> **Temüjin said:**
> I'm sure Kubuntu has the "additional drivers" GUI somewhere in the menus,

I ran the 'driver manager' and it is still "collecting information' (see attachment).   lol

> **Temüjin said:**
> .. but to me, this is easier:
```
sudo apt-get install nvidia-340
```

Hmm, my understanding is that the Nvidia drivers were always proprietary, and that's one reason I never used them. Seems they are open source now, is that correct ?

> **Temüjin said:**
> 
EDIT: Before you install the proprietary driver, you may want to see if this helps with the video playback:
```
sudo apt-get install mesa-vdpau-drivers vdpau-va-driver
```

I don't really have any video playback issues. The main video/display problem I have is outlined in the first few posts in this thread.

Both mesa-vdpau-drivers and vdpau-va-driver are installed by default it seems.

---

### Post by Yellow Pasque on 2016-11-20
> Hmm, my understanding is that the Nvidia drivers were always proprietary, and that's one reason I never used them. Seems they are open source now, is that correct ?


No, they're still closed source. If you're set against using them (even as a test), then I'd still recommend installing lxqt desktop and trying that.

> I ran the 'driver manager' and it is still "collecting information' (see attachment). lol

Probably: [https://bugs.launchpad.net/ubuntu/+source/libqapt/+bug/1530523](https://bugs.launchpad.net/ubuntu/+source/libqapt/+bug/1530523)
Oh, just saw you commented on it. LOL

---

### Post by oygle on 2016-12-07
Thanks for that.  :)

Have been informed in [this post]("https://ubuntuforums.org/showthread.php?t=2341803&p=13579200#post13579200") that a backport for KMail will also include Plasma updates.

---

### Post by oygle on 2017-01-08
Plasma crashes at least 30 times a day and KMail at least that many times. KMail is broken in 16.04.1  :(

---

### Post by oygle on 2017-02-19
The Plasma problems haven't appeared now for several days, so there must have been a fix for it in the updates. Thanks muchly.  :)

---

