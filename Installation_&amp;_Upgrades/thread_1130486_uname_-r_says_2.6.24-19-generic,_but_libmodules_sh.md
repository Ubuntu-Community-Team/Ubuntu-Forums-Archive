---
title: "uname -r says 2.6.24-19-generic, but /lib/modules shows 2.6.27-11-generic"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by azmanam on 2009-04-19
I'm trying to update drivers after ubuntu upgrade.

I'm following directions from this site for my sound card ([http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001))

When I run the apt-get command, I get the following output:

```
~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-19-generic has no installation candidate
```

but when I try the same command with the most current kernel...

```
~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-2.6.27-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So that all looks good, but then I try make:

```
~/Desktop/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.24-19-generic/build M=/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00
make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

Any suggestions?  I'm running mythtv, and I can't hear anything.

for the record, and in case it helps...

```
adam@adam-desktop:~$ uname -a
Linux adam-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

Thanks!
-AA

---

### Post by azmanam on 2009-04-19
PS, yes, I've run update manager, and it says everything is up to date.

---

### Post by azmanam on 2009-04-21
bump

Do I just need to 'reinstall' the OS upgrades?

---

### Post by cariboo on 2009-04-21
When the last kernel update was installed, did you get a message about updating grug and select keep the same file? When doing a kernel upgrade, always choose use maintainers version. You can probably manually add the newer kernel to grub manually, or you could try in a terminal:

```
sudo-reconfigure linux-image-generic
```

to see if that updates grub, so that you can use the newer kernel.

Jim

---

### Post by azmanam on 2009-04-21
> When the last kernel update was installed, did you get a message about updating grug

Probably.  I got 2 or 3 of them.  I'm running myth tv on this box and I had to manually change a few of the files to get everything to play nice with each other.  I knew one day I'd run an update and things would stop playing nice.  I thought if it was asking me to keep my version of the file that means I probably modified it along the way and that by keeping it I'd bypass redoing those modifications after the update... looks like my logic was wrong :)

btw, I did work around the problem temporarily by manually changing the corresponding likes in the make file from (uname -r) to explicitly the new kernel, like for the apt-get command.

I'll try your suggestion when I get home.  Thanks for taking a look at it!

Thanks,
-AA

---

### Post by azmanam on 2009-04-22
> or you could try in a terminal:

Code:

sudo-reconfigure linux-image-generic

to see if that updates grub, so that you can use the newer kernel.

Output:
```

adam@adam-desktop:~$ sudo-reconfigure linux-image-generic
bash: sudo-reconfigure: command not found
adam@adam-desktop:~$ sudo reconfigure linux-image-generic
bash: reconfigure: command not found
adam@adam-desktop:~$ sudo=reconfigure linux-image-generic
bash: linux-image-generic: command not found
```

Tried going to the package manager and reinstalling:
linux-headers-2.6.27-11
linux-headers-2.6.27-11-generic
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic

no obvious problems or error messages in the details for the reinstall.

tried op again:
```

~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-19-generic has no installation candidate
```

problem persists

I downloaded the iso for 8.10.  I'll try 'reinstalling' it tomorrow.

---

### Post by azmanam on 2009-04-26
Updated with the 9.04 distro

Made sure to accept updated versions to any files when prompted

Problem fixed.

Thanks for the help

---

