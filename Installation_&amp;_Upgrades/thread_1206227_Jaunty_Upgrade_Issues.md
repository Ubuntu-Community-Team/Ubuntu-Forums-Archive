---
title: "Jaunty Upgrade Issues"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Dorzu on 2009-07-06
I just upgraded from 8.10 to 9.04. ("Just". I did it a couple of hours ago.) In short, the update manager claims that some part of the process failed, so I need to do a Partial Upgrade. I click Partial Upgrade, and get the following back: "linux-ubuntu-modules-2.6.24-21-generic: subprocess post-removal script returned exit status 1". Now, I'm assuming due to this error, I can't update any of my packages. Neither the Update Manager, nor Synaptic, nor apt-get on the CLI work. (Synaptic shows the package marked for removal, but can't/won't remove it.) 

I've done some searching on the web and found multiple attempts to fix it, all of which I've tried. Off of the top of my head: Using dpkg -i with install/remove on the package doesn't help at all. My /etc/apt/sources.list file is identical to the one on my Jaunty netbook.

I can't install/modify anything, and this is getting _very_ frustrating. Can anyone help me? Please?

---

### Post by Dorzu on 2009-07-07
bump

---

### Post by dstew on 2009-07-07
One method to work around this problem is to remove the -e switch with which the post-removal scripts are invoked. That switch makes them quit if any error is found, halting the removal process.

Look in /var/lib/dpkg/info for the scripts having a file name linux-ubuntu-modules-2.6.24-21-generic*:```
ls -l  linux-ubuntu-modules-2.6.24-21-generic*
```Open the .pstrm file with an editor, and look for the shell invocation, which is usually #!/bin/sh -e, or possibly```
#!/bin/sh
set -e
```Remove the -e, or the set -e, and save the file. Then try```
sudo dpkg -r linux-ubuntu-modules-2.6.24-21-generic
```again. See this [Debian page]("http://www.debian-administration.org/articles/251") for more info.

---

### Post by Dorzu on 2009-07-07
There  was no "-e" in the postrm file. Error message: 

FATAL: Could not open '/boot/System.map-2.6.24-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Cannot find /lib/modules/2.6.24-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--remove): subprocess post-removal script returned error exit status 1
Errors were encountered while processing: linux-ubuntu-modules-2.6.24-21-generic

---

### Post by dstew on 2009-07-08
Please post the entire contents of the .pstrm script.

---

### Post by Dorzu on 2009-07-08
% cat linux-ubuntu-modules-2.6.24-21-generic.postrm
#!/bin/sh

case "$1" in
  remove)
    depmod -a -F /boot/System.map-2.6.24-21-generic 2.6.24-21-generic
    update-initramfs -u -k 2.6.24-21-generic
    ;;
esac

---

### Post by dstew on 2009-07-09
It seems that the post-removal script expects to see the file System.map-2.6.24-21-generic in the /boot directory. If you look in there, do you see that file? If that file is gone, it is likely you have a partially uninstalled kernel. Sometimes you have to install it again to get it to uninstall. You can try```
sudo apt-get -f install
```without an argument to try to fix (re-install) the broken package. If that works, maybe it will uninstall properly. You can also try```
sudo dpkg --configure -a
sudo apt-get update
```to fix things, before uninstalling. You might also try to check the file system for errors. If the suspect file system is your root, you need to boot a Live CD, and do```
sudo fsck -y /dev/sda1
``` (substitute the correct name of course) on the unmounted partition.

As you can see, I am running out of ideas for you.

---

### Post by Dorzu on 2009-07-09
I'm actually at work, and going out of town afterward, so I won't be near the desktop for a few days. I'll try that when I can. Thank you for the help. Even running out of ideas is better than where I was at previously.

---

### Post by hmich176 on 2009-07-10
Here's the problem I have:
```
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by DontThinkSo on 2009-07-12
I'm having the same problem. I tried removing the kernel then re-installing it, here's the output:

```
keegan@keegan-desktop:~$ sudo apt-get install linux-generic linux-image-generic linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx11-xcb1 libmozjs-dev libnspr4-dev libmozjs0d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-generic linux-image-2.6.28-13-generic linux-image-generic
  linux-restricted-modules-2.6.28-13-generic linux-restricted-modules-generic
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 840kB/25.4MB of archives.
After this operation, 98.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://samaritan.ucmerced.edu jaunty-updates/restricted linux-restricted-modules-2.6.28-13-generic 2.6.28-13.17 [829kB]
Get:2 http://samaritan.ucmerced.edu jaunty-updates/main linux-image-generic 2.6.28.13.17 [3466B]
Get:3 http://samaritan.ucmerced.edu jaunty-updates/restricted linux-restricted-modules-generic 2.6.28.13.17 [3486B]
Get:4 http://samaritan.ucmerced.edu jaunty-updates/restricted linux-generic 2.6.28.13.17 [3482B]
Fetched 840kB in 4s (175kB/s)       
Selecting previously deselected package linux-image-2.6.28-13-generic.
(Reading database ... 188343 files and directories currently installed.)
Unpacking linux-image-2.6.28-13-generic (from .../linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb) ...
Done.
Selecting previously deselected package linux-restricted-modules-2.6.28-13-generic.
Unpacking linux-restricted-modules-2.6.28-13-generic (from .../linux-restricted-modules-2.6.28-13-generic_2.6.28-13.17_i386.deb) ...
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.28.13.17_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-generic.
Unpacking linux-restricted-modules-generic (from .../linux-restricted-modules-generic_2.6.28.13.17_i386.deb) ...
Selecting previously deselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_2.6.28.13.17_i386.deb) ...
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-13-genNo apport report written because the error message indicates its a followup error from a previous failure.
                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   eric; however:
  Package linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Before removing it, I would get the same message as hmich.

[Edit] Looks like it's a manifestation of this bug: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1572519.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1572519.html)

---

### Post by dstew on 2009-07-13
I agree, it looks like the bug listed above and in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/99547"). It was not fixed as originally thought.

---

### Post by Dorzu on 2009-07-13
Indeed, that file is _not_ in my /boot directory on the bugged machine. Neither of the suggestions changed anything, but that missing file seems to be _my_ problem, for the moment.

---

### Post by dstew on 2009-07-14
Since the bug is in the dpkg system, and only occurs when a broken package is present, you might be able to work around the bug by true manual removal of the remains of the broken package. See [this]("http://liquidat.wordpress.com/2008/08/22/short-tip-remove-packages-on-debian-systems-with-ultimate-force/") and [this]("http://www.debianhelp.org/node/7498#comment-26107").

To identify all the pieces, do```
sudo dpkg -L linux-ubuntu-modules-2.6.24-21-generic
```Then go to /var/lib/dpkg/info and delete linux-ubuntu-modules-2.6.24-21-generic.postrm. Then do ```
sudo apt-get remove --purge linux-ubuntu-modules-2.6.24-21-generic
```Then manually delete all the files that were listed by the dpkg -L command. Both posts listed above do these three things, but in a different order. Maybe the order doesn't matter.

After that, try apt-get update and apt-get upgrade and see if you are better.

---

### Post by DontThinkSo on 2009-07-14
Fixed the bug on my system.

Download and install the Debian Sid(unstable) version of module-init-tools for your architecture:

[http://packages.debian.org/sid/module-init-tools](http://packages.debian.org/sid/module-init-tools)

then dpkg will properly finish configuring the kernel on next use of aptitude or apt-get.

---

### Post by Dorzu on 2009-07-14
dstew, THANK YOU. That fixed it. I'm back to a working machine, with no partial upgrades hanging over my shoulder.

---

### Post by rtotheototheb on 2009-11-27
Thanks dstew.

The 1st link you supplied resolved a similar problem with a damaged/corrupt package on Ubuntu server 9.04.

---

