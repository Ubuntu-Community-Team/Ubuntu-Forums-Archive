---
title: "Karmic failed upgrade rescue"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by poctob on 2009-10-31
Well I tried to upgrade my Jaunty system to Karmic.  I've been using Ubuntu for several years and didn't expect any problems.  I forgot that nobody repealed Murphy's law yet.

First issues were a long time and slow speed for the packages to download.  No problem.  I figured that servers are overloaded with a lot of people upgrading.  I left it running overnight and most of the day Friday.  When I got home I was happy to see that the install has started.  I had a Pam.d dialog on the screen that wanted me to restart some services.  Here comes the fun part - keyboard and mouse no longer worked, so I could not click on any buttons.  No CTRL+ALT+F7, no CTRL+ALT+BACKSPACE, no CRTL+ALT+DELETE, nothing.  I tried another keyboard and mouse, I even dug out an old PS/2 keyboard, still no luck.  Looks like upgrade process turned off some service like a hotplug or hald.  I could see that my machine wasn't locked since a system monitor applet was occasionally showing network activity.  I had ssh server turned off as well.  So I am in a middle of upgrade and have no way of continuing since I don't have an access to the machine.
I crossed my fingers and powered it off.  Finger crossing didn't help, machine would not get past first part of the kernel init.

Rescue time.  I downloaded and burned Karmic Install CD on my laptop and booted into the live session. Next thing I did was to mount my existing partitions.  First I opened a terminal, became root and created a mount point:
```
$ sudo su
# mkdir newroot
```


I needed to find my original partitions:
```
# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7  /dev/sda8  /dev/sda9  /dev/sdb  /dev/sdb1
```

I remembered to have my system on separate partitions but I could not remember the numbers.  So by trial and error I found one with a root and mounted it:
```
#mount /dev/sda6 newroot
```

Next I mounted my other partitions:
```
#mount /dev/sda7 newroot/var
#mount /dev/sda8 newroot/home
#mount /dev/sda9 newroot/usr
```

Next thing is to change system root to the original partition so it can be repaired:

```
#chroot newroot
```

I proceeded to create some generic devices, it may not be necessary but I did it anyway:
```
#cd /dev
#MAKEDEV generic
```

I got a bunch of error messages, but nothing serious.  Next thing was to mount proc system:

```
#mount -t proc proc /proc
```

Now everything is ready it is time to resume the upgrade:
```
#dpkg --configure -a
#apt-get update
```

Process has started.  After some time I got more errors and it didn't finish, it got stuck on some OpenOffice and KDE packages.  Well, I tried to boot it anyway.  I restarted the machine and I got karmic splash screen.  Great! Not so fast.  GDM never started and all I got was a command shell.  Not a problem once again:
```
$sudo dpkg --configure -a
$sudo apt-get update
```

Failed immediately, however
```
$sudo apt-get dist-upgrade
```
worked!  That went on for a while, told me it was complete and gave me some broken packages warning at the end.  

Reboot and I have GDM login.  Everything worked!  I logged into the system, used Synaptic to locate broken packages, reinstalled them and ran an update. 

I ran an update on my laptop and that worked flawlessly.  So I don't know if the issue is the particular hardware on my desktop (Dell Precision 380) or something else.

Good luck with your upgrade!

---

### Post by Axed on 2009-11-14
Thanks for posting this, it was helpful.

My situation was a bit worse however as my computer seemed to have crashed in the middle of the upgrade (while installing packages), due to disk corruption caused by some bad ram... the system was severely broken. Fsck confirmed there was disk corruption so I repaired it.

On reboot I got "general error mounting filesystems", recovery mode or not.

So I followed these directions, had many errors as expected, but the same problem persisted on reboot. Turns out the kernel package hadn't been properly installed, and there was a problem with initramfs. So from the chroot environment I had to do (as root):
```
cd /var/cache/apt/archives
dpkg -i ./linux-image-[TAB]

```
[TAB] means press the tab key to autocomplete the file name

You may also want to run:
```
update-initramfs -u -k all
update-grub
```
(should be done as part of the package install but can't hurt in case of error)

This got the system to boot into recovery mode, but that wasn't the end of the problems. I also had to install the kernel headers again as the DKMS modules were failing to build. After a few rounds of "dpkg --configure -a" and "aptitude remove [package name]" for a few remaining packages that refused to configure, I managed to get the system up and running again.

So all's well that ends well :)

---

