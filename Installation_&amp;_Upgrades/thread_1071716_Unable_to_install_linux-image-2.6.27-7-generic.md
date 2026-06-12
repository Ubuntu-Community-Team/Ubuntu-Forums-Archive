---
title: "Unable to install linux-image-2.6.27-7-generic"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by Neko_Master on 2009-02-16
I just installed Ubuntu on My PC through windows since when I did a direct install it screwed up and filled up the 32GB partition with randomness.

Anyways, now im in Ubuntu and im doing my updates and linux-image-2.6.27-7-generic fails to install, this is what I get in the terminal...

--------------------------------------------------------------------------
nekomaster@ubuntu:~$ sudo apt-get install linux-image-2.6.27-7-generic
[sudo] password for nekomaster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-2.6.27 linux-source-2.6.27
The following packages will be upgraded:
  linux-image-2.6.27-7-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.4MB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 132076 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-server
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

--------------------------------------------------------------------------

I even tried setting the folder permissions for the folders to allow me to edit them like I was root, but that didnt work either.

How to do fix this/ install this update (linux-image-2.6.27-7-generic)?

---

### Post by mcduck on 2009-02-17
Why are you even trying to install that in the first place? The latest kernel version in Ubuntu is 2.6.27-11, and as long as you have the "linux-generic"-package installed you should automatically get the latest kernel versions. Unless you have some very special reason you shouldn't be installing specific kernel versions at all.

Just run "sudo apt-get update && sudo apt-get upgrade" and everything you have installed should be updated to latest available versions (or use Synaptic or the Update manager to do the same thing).

(by the way, changing permissions or ownership of system directories is almost sure way to break things, hardly ever a thing you should be doing. The package manager runs as root, so it already has permissions to write where it needs to.)

---

### Post by rickjpelleg on 2009-03-28
There is a similar failure with:
  sudo apt-get update && sudo apt-get upgrade

The upgrade is "to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb)"

and the failure is:
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted

Full log of the apt-get session is attached.

---

### Post by TBerk on 2009-03-28
Are you sure you have enough hard drive space left? ("...filled up 32G w/ randomeness").

TBerk

---

### Post by rickjpelleg on 2009-03-29
There is disk space (see below). What does the "Operation not permitted" mean?

%  df -k /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/boot
                      27313168  19940048   7373120  74% /boot

%  df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       3844864   1495160   2154392  41% /
tmpfs                  1036168         0   1036168   0% /lib/init/rw
varrun                 1036168       100   1036068   1% /var/run
varlock                1036168         0   1036168   0% /var/lock
udev                   1036168      2796   1033372   1% /dev
tmpfs                  1036168       104   1036064   1% /dev/shm
/dev/sda1             27313168  19940048   7373120  74% /host
lrm                    1036168      2004   1034164   1% /lib/modules/2.6.27-11-generic/volatile
/dev/loop1              961192    768556    143808  85% /home
/dev/loop2             3844864   1749096   1900456  48% /usr

---

### Post by TBerk on 2009-03-29
What happens when you run the two command separately (esp after a restart.)?
```
sudo apt-get update && sudo apt-get upgrade
```

becomes
```
sudo apt-get update
```

then,
```
sudo apt-get upgrade
```  .

Also, did you have any apps running while this was performing it's update/upgrade?

btw- Google is our friend, unfortunately I seem to have found it in German:

[http://forum.ubuntuusers.de/topic/kein-upgrade-fuer-tzdata/#post-1154627](http://forum.ubuntuusers.de/topic/kein-upgrade-fuer-tzdata/#post-1154627)

Translated version:
[http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F1154627%2F&sl=de&tl=en&history_state0=](http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F1154627%2F&sl=de&tl=en&history_state0=)

I'm wondering if you are installing inside of Windows (via wubi)? Seems there is trouble w/ FAT32 partitions vs NTFS.
[https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)


TBerk

---

### Post by rickjpelleg on 2009-04-01
Thanks. Indeed I'm running a wubi installation.

The alternative workaround described by Agostino Russo in [_[COLOR="Blue"]bug #252900[/COLOR]_]("https://bugs.launchpad.net/wubi/+bug/252900") worked for me:
[INDENT]... remove the /boot mountpoint in /etc/fstab and
unmount /boot (this basically moves /boot inside
of the root filesystem), then copy over the files
from /host/disks/boot to /boot
[/INDENT]
with "/host/ubuntu/disks/boot" rather than "/host/disks/boot".

---

