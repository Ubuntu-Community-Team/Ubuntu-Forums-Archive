---
title: "VirtualBox and Kernel Updates"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by PerfectReign on 2009-10-23
I'm wondering if there's  an Ubuntu solution to this. (I'm also going to post on the VB forums.)

All of my Ubuntu workstations - two laptops and one desktop - as well as my mom's Ubuntu workstation got kernel updates. Each are running VirtualBox. (I have XP, my son has Vista and my 67-year-old mother runs Windows7.)

In each case, I was forced to do a virtualbox update as a result of the kernel update. Normally, this isn't a big deal, but today I got a call from my mom, who's needing to finish a Photoshop (she tried for years to learn GIMP and gave up) project for her church. I spent half an hour on the phone walking her through the virtualbox setup. Eventually, I wrote a quick shell script to run it, since she (a) couldn't type it correctly having to downgrade to the command line and (b) would mess something else up while typing.  (Clicking is MUCH preferable for her.)


Why in the blazes do we need to go through this setup process at all? I installed VB, it should stay installed.

What is broken here?

How do we fix it?

---

### Post by snowpine on 2009-10-23
Did you read the error message from VirtualBox? (I bolded the relevant part)

> Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. **Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.**

You can also, of course, select to boot into the old kernel from Grub, if you have a tight deadline and need it to just work.

---

### Post by james_xxx on 2009-10-23
I ran into the same thing on three different machines running Virtualbox, and also had to do manual fixes to get everything up and going again. 

I have had dkms installed all along, on all three boxes. This time dkms didn't take care of everything, so that may *not* have been your problem.

---

### Post by PerfectReign on 2009-10-23
Well, she and I both have dkms installed. Not sure if there's configuration needed. 

This should just work, right?

Here's a screen from my computer just now.

---

### Post by snowpine on 2009-10-23
The solultion is in the error message. :)

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by PerfectReign on 2009-10-23
Well, with all due respect, I fail to understand why I would have to do this in the first place. Seems so - erm - '80s in nature.  As it is I'd have to downgrade to the command line and type something.

You'd think that the virtualbox people would have made this less obnoxious.

In any case, running sudo /etc/init.d/vboxmanager is what I'm trying to get away from. There's no reason one should be forced to do this and then have to spend time on the phone walking relatives through this mess.   :(

I've looked up dkms and don't find much of use. I also looked in the menu and can't find it under System Tools or Accessories.

Where is it?

---

### Post by snowpine on 2009-10-23
Hi PerfectReign, when you upgrade the kernel, you have to upgrade your modules as well... it's just part of using Linux. I don't consider using the command line a "downgrade" nor do I think anyone forced you to install that new kernel. :)

Also, did you install virtualbox from the Ubuntu repositories, or from the Sun website?

---

### Post by PerfectReign on 2009-10-23
I'm just complaining about the fact that the average user - my mother for example - shoudn't have to go through this. I understand kernel modules, but the install/upgrade should take care of such things.

As for no one forcing me to upgrade the kernel, I didn't do it. It just happened. 

VB is installed from the Sun site. I needed USB for various reasons.

---

### Post by snowpine on 2009-10-24
> **PerfectReign said:**
> VB is installed from the Sun site. I needed USB for various reasons.

Ubuntu can only upgrade applications you install from the repositories using the package manager. If you install a 3rd party application from some website, YOU are responsible for maintaining it. ;)

---

### Post by AlfyBoy on 2010-06-24
You only need to install "dkms" package from synaptics if you dont want to go to the terminal each time you update.

> Well, she and I both have dkms installed. 

And you are right it should just work each time you reboot your system.


:guitar:

---

