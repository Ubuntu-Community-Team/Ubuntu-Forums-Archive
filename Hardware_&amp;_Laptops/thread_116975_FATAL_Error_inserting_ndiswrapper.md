---
title: "FATAL Error: inserting ndiswrapper"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by Romualdo on 2006-01-13
Hello, I'm trying to get my MN-720 PCMCIA card to work with Ubuntu. (I'm a complete beginner please forgive me) I'm following this guide on the internet, and I open up terminal, and when I get to the part where it says "Call 'sudo modprobe ndiswrapper'". When I do this : 
"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted"

Please help!!

---

### Post by Romualdo on 2006-01-13
bump..Please help!

---

### Post by jimmyp on 2006-01-14
[QUOTE=Romualdo]bump..Please help![/QUOTE]

are you sure you put sudo in front?

---

### Post by Ptero-4 on 2006-01-14
You have to write sudo before the rest of the command and when asked for a password input your's. Also this only works when logged in as the user you created during installation.

---

### Post by Romualdo on 2006-01-15
Yes, I preceded it with sudo, and I am using the user I created at installation, please help! I am stumped, I don't want to have to change back to windows :(

---

### Post by cborge on 2006-01-17
I have the some problem. I typed sudo in front, and I'm logged in as the user I created when installing.. 

sudo ndiswrapper -l gives:
> Installed ndis drivers:
bcmwl5a driver present

So the driver is installed, but I can't get the command:
sudo modprobe ndiswrapper  to work without getting the same error as Romualdo referred to..

---

### Post by Lambert on 2006-01-17
Run these commands and post their output here.

```
sudo cat /proc/version
```
```
sudo modinfo ndiswrapper
```


How did you install ndiswrapper? From the repos(or cd) or did you build your own from source?

---

### Post by cborge on 2006-01-17
> cborge@cblinux:~$ sudo cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

> cborge@cblinux:~$ sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.12-9-386/misc/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.7
license:        GPL
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        usbcore
srcversion:     C6E1F41E97737CDB970D518
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)


I downloaded ndiswrapper-1.7 and followed a how to from this forum.

---

### Post by Lambert on 2006-01-17
Here's what I suggest trying for you cborge.

When ndiswrapper-utils are installed from repos they install in a different location then what you are showing. So try this command.

```
sudo cp /lib/modules/2.6.12-9-386/misc/ndiswrapper.ko /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/
```

This will copy the driver over to a different directory. Then run this command.
```
sudo depmod -a
```

Then try to modprobe to see what your results are.

One other note, check permissions on folder

```
ls -l /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/
```

If this doesn't work then I would suggest starting over from scratch. The fatal: error inserting error usually points to a driver compiled and installed incorrectly.

---

### Post by mpvano on 2006-01-17
Did you do anything to "install" ndiswrapper? You will have problems like this if you follow most of the instructions floating around here and elsewhere about "installing" ndiswrapper.

If you downloaded a source package and followed FAQ instructions from the ndiswrapper website or anywhere else to install it, you almost certainly have installed an incompatible driver.

If you have NOT done this, disregard the rest of this message.

The problem is that the correct ndiswrapper driver module is ALREADY installed in ubuntu's linux-image, and if you try to install a different one without knowing more than the FAQs tell you about the process, you will almost certainly build and install one using the wrong C compiler!

All the parts of the kernel and drivers need to be built using the same C compiler version - which is currently NOT the latest C compiler and is not the version installed when you install "build-tools".

The correct way to get ndiswrapper running is simply to install the prebuilt ubuntu package "ndiswrapper-utils" (which contains JUST the matching configuration program) using apt-get or synaptics, locate your windows drivers, and go ahead and configure the package.

If you have inadvertently gone ahead and installed sources and built a new ndiswrapper, it won't work unless you built it with the exact older Gnu C compiler used to build the kernel. You will, however be deceived by the fact that the newly built ndiswrapper configuration tool will work just fine! The kernel driver module is the part that's mismatched.

The simplest fix is probably to reinstall your "linux-image" and "linux-restricted-modules" packages (which you can do from synaptics) and then to install the ndiswrapper-util module from the standard repository. I'm sorry but I can't provide any more information about doing this if you don't understand how to do that.

If, on the other hand your card won't work without the very latest ndiswrapper driver, you'll have to learn how to install and use module-assistant (no mean feat), or learn how to install multiple C compilers, select the correct version manually, and then build modules correctly and install them. This is rarely needed - most likely it's your windows XP drivers that are out of date, or broken.

Having been there and done this myself, I can see how it's pretty easy to make this mistake. Fortunately, I'm experienced enough to have figured out what I did wrong and cleaned up the problem myself. I'm afraid that this may not be so easy for some ubuntu beginners.

hope this clarifies things - if not for you, then perhaps for other readers with this problem....

Mario

---

### Post by Lambert on 2006-01-17
That's actually a very good catch and what the problem is currently in this thread more then likely.

I do question the compiler version though as the above thread from cborge you can see is compiled with v 3.4 which is what the kernel is compiled in for breezy. The problem is probably two installed modules.

So in the howto's someone needs to add a section to remove the installed version before compiling. Which would be this command

```
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
```

And then after compiling if it won't work it needs to be copied to the kernl/drivers/net/ndiswrapper directory.

But as you said, it's best just to just use what comes with breezy and install ndiswrapper-utils. But of course it's an older version (1.1) and some devices depend on the newer ndiswrapper version to function.

---

### Post by mpvano on 2006-01-17
Agreed, I've got it working both ways here, but the confusion about needing to build it definitely needs to be addressed somewhere.

I suspect that a great deal of it could be eliminating by just making ndiswrapper-utils part of the base install. It's absence is what seems to start the tailspin.

Unfortunately, similar problems occur with a lot of other drivers that require "helper" packages as well. When I first started with messing with Ubuntu, I had the same problem with the lucent modem drivers - they were actually present and would have worked fine if I'd just installed the utilities package instead of trying to find new versions and rebuild them from scratch - a process I never DID get working...

hopefully some of the info in this forum will be sifted through, verified and someday become part of a great Ubuntu user's manual....

Mario

---

