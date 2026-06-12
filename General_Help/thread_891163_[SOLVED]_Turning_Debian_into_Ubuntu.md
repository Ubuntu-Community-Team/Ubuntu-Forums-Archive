---
title: "[SOLVED] Turning Debian into Ubuntu"
date: 2008-08-15
forum: General Help
---

### Post by dodle on 2008-08-15
Okay, what I am trying to do may sound a little strange, so I will explain why I am doing it.  I have a laptop, which I got for free and fixed up, which is not exactly the best laptop out there.  It's got Windows XP and I wanted to dual-boot with Ubuntu.  I had tried for days to get Ubuntu installed with no success.  The laptop just rejects it I guess.  I have also tried about a dozen other Linux distributions and the only one that I can get to install is Debian Etch.  Which is great, but I have found that Etch doesn't provide many of the packages and updates that I would like.  So the first thing I tried was adding the Ubuntu Hardy repositories.  Well that didn't work too well because of software conflicts.  I then decided to comment out the Debian repositories and just use the Ubuntu ones.  I soon came across problems with dpkg.  I couldn't upgrade it, and without an upgrade I couldn't install all the ubuntu packages I wanted.  Soooooooo, (you can probably guess where I am going) I un-installed dpkg which in turn made everything else unusable (including Synaptic and apt).  To resolve this I downloaded (on another machine) a copy of the ubuntu dpkg deb package and extracted it.  Then I transferred the extracted files onto my Debian/Ubuntu machine a placed them in there designated folders.  dpkg now works fine but I am having another issue; Synaptic and apt don't recognize that it is installed.  So if I try to update something, like apt, it tries to install dpkg and gives me the following error message:```
 installing dpkg would break apt, and
 deconfiguration is not permitted (--auto-deconfigure might help)

```  Is there a way to get apt and Synaptic to recognize that dpkg is installed?  This should allow me to upgrade the rest of my packages to the current ubuntu packages.

Edit:  I'm actually a little afraid to restart my machine at this point.  I'm worried that it might not turn back on >.<

---

### Post by tippyknit on 2008-08-15
Did you try using the text-based install? Also, what was the problem with all other distros than Debian Etch?

---

### Post by dodle on 2008-08-15
> **tippyknit said:**
> Did you try using the text-based install?

Do you mean going to a terminal and inputting:```
sudo apt-get install dpkg
```Yes I tried that and got the same error.

> **tippyknit said:**
> Also, what was the problem with all other distros than Debian Etch?The Ubuntu distros installed but never started up.  Just got a blank screen.  Other distros, like Gentoo couldn't recognize my screen, and some others wouldn't even boot up the liveCD.

---

### Post by tippyknit on 2008-08-15
I'm definitely not a debian lover (nor user), but I would like to understand what you did when trying other distros.

Here's what I understand from your explanation:
1. You started up from the live CD of Ubuntu (but no other derivatives, i.e. xubuntu) and double-clicked on the install icon and followed the complete install procedure, choosing to install the GRUB boot loader. When the install told you the install was successful, you restarted and got a blank screen.
2. Again, I know nothing about Debian, but what bootloader does debian use?

---

### Post by dodle on 2008-08-15
> **tippyknit said:**
> 
Here's what I understand from your explanation:
1. You started up from the live CD of Ubuntu (but no other derivatives, i.e. xubuntu) and double-clicked on the install icon and followed the complete install procedure, choosing to install the GRUB boot loader. When the install told you the install was successful, you restarted and got a blank screen.

Yes, that's right, except I tried it with both Ubuntu and Kubuntu live CDs.  I may just end up with the same problem if I am successful.  Still, I am not satisfied with Debian.  I installed Ulteo, which worked fine but I didn't like it.

---

### Post by tippyknit on 2008-08-15
What about part two: what bootloader does Debian use?

---

### Post by dodle on 2008-08-15
It uses grub.

---

### Post by dodle on 2008-08-15
I guess I should clear something up.  After installing Ubuntu and Kubuntu, the system did boot up, it got through the bootloader and the splash screen.  But gdm/kdm never came up, just a blank screen.

---

### Post by tippyknit on 2008-08-15
I just investigated on the Debian website to see whether there was anything useful, but it doesn't appear that there is. I'm going to explore a little online and see what I can find.

---

### Post by dodle on 2008-08-15
The main thing I want (right now) is to get synaptic and apt to recognize that dpkg is already installed.  Is there a way to have apt-get force install dpkg?  I think I might try rebooting into a prompt.  Wish me luck.

---

### Post by rossjman1 on 2008-08-15
dpkg is a vital part of the system; it can't be installed or uninstalled. Dpkg is how Debian based distros install software. Apt-get is merely a front end to that system, and was only created to solve dependency issues. Basically, if dpkg is broken, then apt, aptitude, and synaptic will all be broken too.

You said in your first post that you uninstalled dpkg? Are you sure? I don't think you uninstalled it (didn't know it was possible from apt), just messed up the whole system. You'll be better off reinstalling Debian or installing an Ubuntu-based distro like Linux Mint.

Also, what don't you like about Debian? Etch is moving from testing to stable, so it will have older packages, but if you just change all instances of 'etch' in the /etc/apt/sources.list to 'lenny', then you should have a more up to date system. Also, when you were trying to get Ubuntu to work, do you get to a log in screen at all (even the command line one)?

---

### Post by dodle on 2008-08-15
Okay here is the output of the prompt:```
debian:~# apt-get install dpkg
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  dpkg
0 upgraded, 1 newly installed, 0 to remove and 460 not upgraded.
2 not fully installed or removed.
Need to get 0B/2299kB of archives.
After unpacking 7180kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  dpkg
Install these packages without verification [y/N]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg:
 dpkg breaks apt (<< 0.7.6ubuntu6)
  apt (version 0.6.46.4-0.1) is present and installed.
dpkg: error processing /var/cache/apt/archives/dpkg_1.14.16.6ubuntu3_i386.deb (--unpack):
 installing dpkg would break apt, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.16.6ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
debian:~#
```I would upload a screenshot, but I can't install xfce4-screenshooter-plugin or gimp.  According to Synaptic dpkg is not installed, but I have installed it manually.  If I can just get Synaptic to recognize that it is already installed, I should be able to update the rest of my packages.

---

### Post by rossjman1 on 2008-08-15
I think you can still take screenshots with the printsceen button like you would in Windows. I'm not 100% sure about that though.

To fix your problem you will probably need to get the Debian version of dpkg, but as I said earlier, it will probably be easier to reinstall.

---

### Post by dodle on 2008-08-15
I did it, I'm not sure why this worked but it did:```
apt-get remove apt
```then:```
apt-get install dpkg
```Afterwards, dpkg showed up as installed in Syaptic and I reinstalled apt.  I didn't think apt-get would work after I uninstalled apt. *sweating*

Also, when I removed apt it said that Synaptic would be removed as well.  But for some reason it wasn't.  I just typed in "synaptic" in the shell and it came right up.

It's letting me upgrade and install all my Ubuntu packages now, except it's still using Debian's kernel for some reason.  Is it the same kernel?

---

### Post by rossjman1 on 2008-08-15
I'm glad you figured it out, but does it seem to change Debian into Ubuntu after apt-get update and upgrade?

---

### Post by dodle on 2008-08-15
I'm going to restart it soon.  Usplash 'n stuff is installed so if all goes well is should act just like a normal Hardy installation.  So I guess I have an Ubuntu installation now, or maybe a Debuntu.

---

### Post by dodle on 2008-08-16
okay, I have a new problem.  After updating everything, I tried rebooting again and now I am stuck at a prompt:```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/d286688a-8587-4977-99b9-1414cf09c374 does not exist.
Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (as)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```This isn't the first time, in my experience, that I have been stuck at this shell.  But I have never been able to find a solution for it, I always end up doing a fresh install.  Is there a way to fix this without reinstalling?

---

### Post by kerry_s on 2008-08-16
you can't change debian to ubuntu, there both built very different.
ubuntu uses upstart
debian uses init
ubuntu uses a generic kernel
debian use processor specific kernels
etc...

just install ubuntu if you want ubuntu.

---

