---
title: "Upgrade to Grub2/Error 15-Computer down!"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Rifester on 2009-10-17
I followed the GRUB update instructions perfectly. I did a test boot from the chainload menu and everything booted up.   So I:
 $sudo upgrade-from-grub-legacy
Everything ran fine in terminal.    I rebooted the system and now I get grub error 15 and the system locks up.  I had to dig out my Jaunty live disk to get online.    PLEASE HELP!

---

### Post by mac9416 on 2009-10-17
Others have had this problem. Someone found [this fix]("http://kubuntuforums.net/forums/index.php?topic=3106892.0").

```
$ sudo update-grub2
```

Hopefully that fixes it.

---

### Post by Rifester on 2009-10-17
After researching my problem I found out that the instructions posted were for updating to grub legacy.   I am in terminal on the live CD trying to update to grub 2 but terminal states:

ubuntu@ubuntu:~$ sudo update-grub2
grub-probe: error: cannot find a device for /.

What do I do to fix this from terminal in the Live CD?

Mark

---

### Post by mac9416 on 2009-10-17
I'm shooting in the dark now. Can you try chrooting into your main install from the live CD and running 'update-grub2'?

```
$ sudo chroot /media/<your_hard_drive_mount_point>
```

Another person with the same problem: [http://alicious.com/2009/grub-2-install-error-15/](http://alicious.com/2009/grub-2-install-error-15/)

He was able to boot using his 8.04 live CD by choosing "Boot from first hard drive" in the live CD menu. If that worked for you, you could run update-grub2 in your main install.

---

### Post by Rifester on 2009-10-17
The live CD won't let me boot from hard drive.   It gives me the same Grub Error 15.

---

### Post by mac9416 on 2009-10-17
I was afraid that would happen. Do you need instructions for chrooting in from the live CD? Sorry about all this trouble.

---

### Post by Rifester on 2009-10-17
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566   83  Linux
/dev/sda2            9404        9729     2618595    5  Extended
/dev/sda5            9404        9729     2618563+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo chroot /media/dev/sda1
chroot: cannot change root directory to /media/dev/sda1: No such file or directory


Any ideas?

---

### Post by mac9416 on 2009-10-17
You're getting close. Run this and post the output:

```
$ ls /media/
```

---

### Post by Rifester on 2009-10-17
ubuntu@ubuntu:~$ ls /media/
ubuntu@ubuntu:~$ 

No output.


Is it possible for me to download and install grub directly from the repository?   I don't understand the terminal that well and and cannot figure out why it won't allow me to re-install grub.

---

### Post by mac9416 on 2009-10-17
I wish I knew GRUB better, but I don't really. I believe you must chroot into your main install to run 'update-grub2'. this much I know how to do, and I hope you can hang with me long enough to give it a try.

The reason you're getting no output is I forgot we need to mount the Ubuntu partition. You can do that by going to Places>Computer, and double-clicking your Ubuntu partition's icon. Then it will appear in /media/. Once it's there you can run 'sudo chroot /media/<mountname>'. Then in the chroot, you can run 'sudo update-grub2'.

Sorry this is taking so long, but I am really as much a n00b as many others. I'm just trying to help out where I can, and I do sometimes do poorly. Try and hang with me.  :)

---

### Post by Rifester on 2009-10-17
ubuntu@ubuntu:~$ ls /media/
disk
ubuntu@ubuntu:~$ sudo chroot/media/sda1
sudo: chroot/media/sda1: command not found
ubuntu@ubuntu:~$

---

### Post by mac9416 on 2009-10-17
We are geeting very close, my friend. Now run...

```
$ sudo chroot /media/disk/
$ sudo update-grub2
```

Fingers are crossed...

---

### Post by Rifester on 2009-10-17
ubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# sudo update-grub2
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /.

---

### Post by mac9416 on 2009-10-17
Drat. At least we're now chrooted in. I'm going to look for a howto reinstall GRUB2.

I'm terribly sorry nothing seems to be going right. Like I say, I'm not particularly knowledgeable about GRUB, but I'm willing to do what I can to help as long as you're willing to deal with me. :)

---

### Post by mac9416 on 2009-10-17
From chroot:

```
$ dpkg-reconfigure grub2
```

```
$ grub-install /dev/sda
```

Both worth a go. :)

I'm afraid if those don't work, I'll have to turn it over to smarter people. I'm afraid I haven't helped much. Hopefully someone else can help you out.

Thanks for your patience!

---

### Post by Rifester on 2009-10-17
root@ubuntu:/# dpkg-reconfigure grub2
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
/usr/sbin/dpkg-reconfigure: grub2 is broken or not fully installed
root@ubuntu:/# grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/# 


I am lost

---

### Post by Rifester on 2009-10-17
Should I do a clean install?  Is there no hope?

---

### Post by mac9416 on 2009-10-17
A glimmer of hope! 

> /usr/sbin/dpkg-reconfigure: grub2 is broken or not fully installed

I know how to fix broken packages. From inside the chroot:

```
$ sudo dpkg --configure -a
$ sudo apt-get purge grub2
$ sudo apt-get install grub2
```

---

### Post by oldfred on 2009-10-17
I copied this as a full chroot command:

Of course you must first know what partition you want to mount, in this example I'm using sda5:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf (may or may not be necessary to establish an internet connection)
sudo chroot /mnt
Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
update-grub2
When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by Rifester on 2009-10-17
root@ubuntu:/# sudo dpkg --configure -a
sudo: unable to resolve host ubuntu
Setting up grub-pc (1.97~beta4-1ubuntu2) ...
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
/etc/default/grub: 8: cannot create /dev/null: Permission denied
/var/lib/dpkg/info/grub-pc.postinst: line 26: /dev/null: Permission denied
sed: warning: failed to get security context of /tmp/grub.FN3358WvBs: No data availablesed: warning: failed to get security context of /tmp/grub.FN3358WvBs: No data availablesed: warning: failed to get security context of /tmp/grub.FN3358WvBs: No data availableCan't open /dev/null: Permission denied
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 13
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc; however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 grub2
root@ubuntu:/#

---

### Post by Rifester on 2009-10-17
root@ubuntu:/# sudo apt-get purge grub2
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevolution5.0-cil libqt4-sql-mysql libqt4-dbus libqt4-qt3support
  libboost-thread1.34.1 libass1 libboost-date-time1.34.1 libx264-65
  libboost-signals1.34.1 libboost-iostreams1.34.1 libffado0 libqt4-sql
  libqt4-xml libqt4-designer libavahi1.0-cil liblrdf0 libqt4-script
  qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 270kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 184002 files and directories currently installed.)
Removing grub2 ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-pc (1.97~beta4-1ubuntu2) ...
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
/etc/default/grub: 8: cannot create /dev/null: Permission denied
/var/lib/dpkg/info/grub-pc.postinst: line 26: /dev/null: Permission denied
sed: warning: failed to get security context of /tmp/grub.aVkv52TQLP: No data availablesed: warning: failed to get security context of /tmp/grub.aVkv52TQLP: No data availablesed: warning: failed to get security context of /tmp/grub.aVkv52TQLP: No data availableCan't open /dev/null: Permission denied
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 13
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# sudo mount /dev/sda1/mnt
sudo: unable to resolve host ubuntu
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab
root@ubuntu:/# sudo mount /dev/sda/mnt
sudo: unable to resolve host ubuntu
mount: can't find /dev/sda/mnt in /etc/fstab or /etc/mtab
root@ubuntu:/# sudo apt-get install grub2
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevolution5.0-cil libqt4-sql-mysql libqt4-dbus libqt4-qt3support
  libboost-thread1.34.1 libass1 libboost-date-time1.34.1 libx264-65
  libboost-signals1.34.1 libboost-iostreams1.34.1 libffado0 libqt4-sql
  libqt4-xml libqt4-designer libavahi1.0-cil liblrdf0 libqt4-script
  qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  grub2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2,602B of archives.
After this operation, 270kB of additional disk space will be used.
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
dpkg-preconfigure: unable to re-open stdin: 
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub2.
(Reading database ... 183990 files and directories currently installed.)
Unpacking grub2 (from .../grub2_1.97~beta4-1ubuntu2_i386.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-pc (1.97~beta4-1ubuntu2) ...
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
/etc/default/grub: 8: cannot create /dev/null: Permission denied
/var/lib/dpkg/info/grub-pc.postinst: line 26: /dev/null: Permission denied
sed: warning: failed to get security context of /tmp/grub.EMx4YYZ4m0: No data availablesed: warning: failed to get security context of /tmp/grub.EMx4YYZ4m0: No data availablesed: warning: failed to get security context of /tmp/grub.EMx4YYZ4m0: No data availableCan't open /dev/null: Permission denied
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 13
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc; however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

---

### Post by fhumayun on 2009-10-25
Unable to resolve host implies you don't have a live network connection (to the internet)..  Make sure you're connected/ authenticated.

---

### Post by mac9416 on 2009-10-25
"Unable to resolve host *usually* means the you aren't connected, but "sudo: unable to resolve host ubuntu" means that there is a problem with /etc/hosts or /etc/hostname.

Because MRife has root privileges (note the "#"), he does not need to use sudo (though it does not hurt).

---

### Post by fhumayun on 2009-10-25
@mac9416: Thanks for the pointer I'm pretty much having the same issue as MRife; but, I got farther along, because the commands executed successfully on my console -- and even as far as the update-grub2.  Since we had different result, I simply wanted to nudge MRife to spot check whatever might be preventing good execution on his end.

In my case, however, the g-probe module of grub still isn't able to reconcile the already mounted drives. 

I've been checking out the various HOW-TOs and the outcome is looking bleak for continuing to dance around the grub2 config files.  I'm rolling back to using a prior version of grub.

---

### Post by humphreybc on 2009-10-27
I'm having the EXACT same problem as the original poster.

All the error messages are the same. It might help that the package name is "grub-pc" not "grub2"

Anyway, I haven't found a solution, so I'm currently on the LiveCD trying to remove grub2 and replace it with old grub till this gets fixed.

---

### Post by jfreak on 2009-10-27
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and did step 13
worked for me

---

### Post by thedude01 on 2010-11-23
thank you jfreak for pointing that out. I had the same problem as the original poster and your tip solved it for me.

---

