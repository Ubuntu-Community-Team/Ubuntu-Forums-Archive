---
title: "Update manager - &quot;linux-image-2.6.27.7-generic (and now 2.6.27.11)"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by iaswni on 2009-04-10
Hi my friends,
I have a problem that unfortunately I can't find a solution in the forums and I don't know what is causing it.
I had a fresh install of 8.10 a few days ago, and as I was running the updates I had and error in package named above:

[I]E: /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-11-generic' before installing new version
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version[/I]

And this from the terminal..

[I](Reading database ... 124851 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-11-generic 2.6.27-11.27 (using .../linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-11-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-11-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted
Running postrm hook script /sbin/update-grub.
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_i386.deb
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb

    You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.

    Nothing to be done, exiting ...

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/I]

Then I just close it and it goes back to normal, but the updates stay there. Now from the description of the packages I see "on x86/x86_64" and I have the impression it shouldn't be there as my pc is 32bit..

Appreciate the advice.. thanks a lot
Iasonas

---

### Post by drs305 on 2009-04-10
In response to the initial failure for the system to make a backup of vmlinuz...  Have you checked your available disk space? Often the failure is due to insufficient free disk space to create a backup. 

You can open baobad/Disk Usage Analzer to explore your system if you aren't sure. If you do, open it as root so you can see all the files:
```

gksudo baobab /

```

You can also just run a quick check from the command line:
```

df -h /
df -h /boot  # If you have a separate /boot partition

```

---

### Post by coffeecat on 2009-04-10
> **iaswni said:**
> [I]You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.[/I]

Did you try 'sudo dpkg-reconfigure localepurge' and, if so, what happened?

---

### Post by iaswni on 2009-04-10
@ drs 305,
I did what you said, GB are plenty so i dont think that is the problem..

@ coffeecat
Did what you said, it deleted a lot of files.. that was irrelevant though with the error.. localepurge i installed after the problem. deleted it anyways but nothing.

But it is really strange as this appeared since i installed ubuntu and I never had this problem before.

I found a post with almost the same file but a different problem.
[http://art.ubuntuforums.org/showthread.php?t=955956](http://art.ubuntuforums.org/showthread.php?t=955956)

The description in the package is 
[I]This package contains the Linux kernel image for version 2.6.27 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. [/I]

Thanks guys

Any ideas....

---

### Post by newenglandcs on 2009-04-15
I think I'm having the same issue.  I installed localepurge and still no luck with installing these 2 kernel updates.

Does anyone have any suggestions?

Thanks.

---

### Post by drs305 on 2009-04-15
> **newenglandcs said:**
> I think I'm having the same issue.  I installed localepurge and still no luck with installing these 2 kernel updates.

Does anyone have any suggestions?

Thanks.

First, welcome to the ubuntu forums!

If you run this command, which will try to install the latest linux kernel compatible with your machine, what messages do you get? If you don't know how to open a terminal, Applications, Accessories, Terminal:
```
sudo aptitude install linux-image
```
You will be asked for a password. Enter your password and hit ENTER, even though you won't see what you type.

---

### Post by newenglandcs on 2009-04-15
> **drs305 said:**
> First, welcome to the ubuntu forums!

If you run this command, which will try to install the latest linux kernel compatible with your machine, what messages do you get? If you don't know how to open a terminal, Applications, Accessories, Terminal:
```
sudo aptitude install linux-image
```
You will be asked for a password. Enter your password and hit ENTER, even though you won't see what you type.

Thank you for the welcome.  I ran the command and the following was the output.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  linux-image 
0 packages upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 2880B of archives. After unpacking 32.8kB will be used.
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com intrepid-updates/main linux-image 2.6.27.11.14 [2880B]
Fetched 2880B in 0s (8041B/s)     
Selecting previously deselected package linux-image.
(Reading database ... 132088 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.27.11.14_i386.deb) ...
Setting up linux-image (2.6.27.11.14) ...
localepurge: checking system for new locale ...
localepurge: processing locale files ...
localepurge: processing man pages ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


```


linux-image-2.6.27-11-generic (Version 2.6.27-11.31)
linux-image-2.6.27-7-generic (Version 2.6.27-7.16)

...still fail to install and continue to show in the update manager.  Any thoughts.

Thanks for your help.

---

### Post by drs305 on 2009-04-15
> **newenglandcs said:**
> 

**linux-image-2.6.27-11-generic (Version 2.6.27-11.31)**
linux-image-2.6.27-7-generic (Version 2.6.27-7.16)

...still fail to install and continue to show in the update manager.  Any thoughts.

Thanks for your help.

I just installed it via Update Manager (from -14 to -31) without problems. Perhaps you could try investigating the inability to update by opening Synaptic.

Hit "Reload" to refresh the data.
Highlight linux-image or linux-image-2.6.27-11-generic. 
Does it show .14 in the "Installed version" column?
Does it show .31 in the "Latest version" column?
If you click on "Package" in the top menu, is "Locked" unticked?
In Settings, Preferences, Distribution: Is "Always prefer highest version" selected?
If you choose "Mark All Upgrades" is the linux-image package (or -14) marked? If so, "Apply" and see if it installs that way.
You could also go to Edit, Preferences, Files and select "Leave all downloaded packages in cache". If it doesn't install, you could check to see if the .31 deb exists in /var/cache/apt/archives. If it does, try installing it by double-clicking the package.

If none of that works, just keep trying Update Manager. Other users with problems with previous kernels eventually got the upgrade to 'take'.

Good luck, hope you find something that works.

---

### Post by newenglandcs on 2009-04-21
I found another thread tracking a similar issue (older kernel updates), that referenced another site/post.  Using steps 1-3, I renamed all *-generic files in \boot with an ".old" suffix.  I was then able to install the 2 kernel updates that were left in the update manager.

[http://ubuntuforums.org/showthread.php?t=935295]("http://ubuntuforums.org/showthread.php?t=935295")
  \
  [https://bugs.launchpad.net/wubi/+bug/252900/comments/37]("https://bugs.launchpad.net/wubi/+bug/252900/comments/37")

After installing the updates, I tried booted into 2.6.27-11, but my network connection stopped working.  I'm now using 2.6.27-7 which I haven't had any problems with.  I guess I'll wait for the next update to try 2.6.27-11 again.

Thanks for your help drs305.

---

