---
title: "[SOLVED] Where did all my free space go (on LiveUSB)?"
date: 2008-11-26
forum: General Help
---

### Post by pavel123 on 2008-11-26
I have been successfully using Ubuntu on my HDD 4GB partition for about a year. Recently, I installed Ubuntu 8.10 on my 4GB USB flash drive with all drive space dedicated to persistence (using built-in &#8220;USB-creator&#8221;).

Everything went well until I updated the packages several times with update manager. Suddenly I noticed that a free space on the file system dramatically decreased. I used all the recomendations from [Cleaning up a Ubuntu GNU/Linux system]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html") and run [Ubucleaner script]("http://www.ubuntips.com.ar/2007/12/12/ubucleaner-10-limpia-tu-ubuntu/") but with no luck. Then I uninstalled Mono, GIMP, games and few other things; removed all localization stuff. But nothing helped me to reclaim free space. 

Finally, it came to the point, when 0 bytes of free space left. However, that fact don't prevent me to copy ~100MB of new files to the file system (I wonder how it could be possible). Now, it seems, that persistence works only partially, and I can't update system packages with update manager (because of the lack of free space). Whole system is unstable.

What can be the cause of such strange system behavior, where did all free space finally go?

---

### Post by taurus on 2008-11-26
Try removing the cache.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Also, look in /var to make sure your log files are not taking up all the space.

```
sudo du -h /var
```

---

### Post by pavel123 on 2008-11-26
I've already done all the magic with apt cleans, removes, orphan packages, locales, browser caches and logs...

ubuntu@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M   88K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.8M 1010M   1% /dev
tmpfs                1013M   12K 1013M   1% /dev/shm
rootfs                2.0G  1.9G  2.6M 100% /
/dev/sdc1             3.8G  2.7G  1.1G  73% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.0M   16K 1008K   2% /tmp
df: `/media/disk': No such file or directory
df: `/media/disk-1': No such file or directory
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/disk': No such file or directory
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/disk': No such file or directory
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
df: `/media/disk': No such file or directory
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
tmpfs                1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

I've just found [another forum thread with the similar problem]("http://ubuntuforums.org/showthread.php?t=984276") and ["Root fs full -> free space always below 0"]("http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2004-07/1577.html") (on FreeBSD). But all without solution...

---

### Post by pavel123 on 2008-11-26
[Another similar case with free space disappeared]("http://tennessee.ubuntuforums.com/showthread.php?t=980794")

---

### Post by pavel123 on 2008-11-26
Here's a screen-shoot of space usage analyser:
[[IMG]http://img222.imageshack.us/img222/4392/screenshotdiskusageanalap5.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshotdiskusageanalap5.png)[[IMG]http://img222.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by pavel123 on 2008-11-27
I created [a bug report]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/302703") on launchpad.

---

### Post by pavel123 on 2008-12-03
I've figured-out the root of the problem. It's not a true bug, it's a «feature», resulted from the way usb-creator works.

Architecture assumes using [SquashFS]("http://en.wikipedia.org/wiki/SquashFS") together with [UnionFS]("http://en.wikipedia.org/wiki/UnionFS") to create semi-writable compressed file system ([explanation of the technique]("http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html#sqwrite")). As such, [copy on write (COW)]("http://en.wikipedia.org/wiki/Copy-on-write") used when any file from squashed file system must be rewritten. No wonder this doubles space consumption every time you modify (or just touch) a file from original installation. Also, there's no way to delete these files.

Two file storages are mounted through [loop devices]("http://en.wikipedia.org/wiki/Loop_device") (/dev/loop0, /dev/loop1) so you can see all newly created additional files by mounting /dev/loop1.

Hence, it seems that installations made with usb-creator are good for small flash drives (because of the SquashFS usage), but running update manager with SquashFS is not such a brilliant idea (because this may require much more space comparing with direct installation, and can create problems resulted from inability to delete files).

So if you want to create installation to update it later, it's better to avoid using usb-creator and perform direct setup to flash-drive.
 
As for usb-creator, maybe we should provide a choice to avoid SquashFS usage and to install the whole system on a writable destination.

---

### Post by homer693 on 2008-12-20
.

---

### Post by dcstar on 2008-12-20
> **pavel123 said:**
> I've figured-out the root of the problem. It's not a true bug, it's a «feature», resulted from the way usb-creator works.
..........
So if you want to create installation to update it later, it's better to avoid using usb-creator and perform direct setup to flash-drive.
 
As for usb-creator, maybe we should provide a choice to avoid SquashFS usage and to install the whole system on a writable destination.

The desired feature of minimising writes to things with a finite quantity of write cycles - like USB stick drives - is probably why this happens.

Given the improving lifetime of USB sticks now, and their low cost, it may be worthwhile to just do the "Standard" install and then tweak to filesystems to reduce writes etc.

---

### Post by pavel123 on 2008-12-21
The main reason for such a work of the usb-creator is not a desire to minimise writes, it is all about minimising an initial system space consumption.

SquashFS do a good job by compressing system files to about a third of original size, so the whole system can be installed on a relatively small flash drive. However, when it comes to the updates, there's no way to delete obsolete initial files from the root file system, thus space used very inefficiently.

Hence, if you are going to keep you system up-to-date, it is definitely better to avoid using usb-creator. The solution is direct installation to a usb flash drive. 

I recommend formating the flash drive to ResierFS (mounted with 'noatime,nodiratime,notail' options) and mount tmpfs to /tmp, /var/tmp and /var/log (like EeePC does) to increase speed and minimise writes.

I have been using Ubuntu 8.10 on my 4GB flash drive for some time and everything seems to work fine.

---

### Post by jpmur on 2008-12-27
Hello,

I am new to ubuntu so I used the script Ubuntu810.bat from windows to install it on my usb key. Easy.

So, pavel123, is there a tutorial to install it the way you recommand ?
Or, is there a way to extend the rootfs ? which is included in the casper-rw file as I understood. On my 4GB key, there is in fact 2GB free.

JP

---

### Post by pavel123 on 2008-12-29
There's nothing particular in the installation to a flash drive. Just boot from Live CD and select flash drive as a target for root file system (format as reiserfs) and GRUB loader, don't create swap.

I recommend running installation inside [VirtualBox]("http://www.virtualbox.org/") because it provides safe environment, completely separated from your host system (also, it can boot directly from an ISO-image file).

[Here]("http://www.psychocats.net/ubuntu/virtualbox") is a detailed explanation of how to run installation from Live CD using VirtualBox. Don't create HDDs, add your usb drive to virtual machine's configuration.

---

### Post by jpmur on 2008-12-31
Thanks for your answer.

I installed virtualbox, but it cannot see my usb key (whereas it can see my keyboard or mouse). So unable to install this way.

On a second PC, I will create a new partition and install ubuntu...
It is not the easiest way, but il would work a least ;-)

JP

---

