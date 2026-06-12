---
title: "issues with fglrx and usb boot"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by replacement on 2005-10-06
i try to install breezy on a usb hard drive through my thinkpad t42p. i encountered two problems. i hope someone can give me a hint as to how to solve them. thanks in advance

1. usb boot through customized initrd worked fine with kernel 2.6.12-8, but what strange is i have to keep the installation cd in the drive to boot the ubuntu installed on the usb drive. otherwise, it will report /dev/sda2 not found. after i upgraded the kernel to 2.6.12-9, the usb drive wouldn't boot any more no matter whether i had the CD in the drive or not. it will consistently tell me there is no /dev/sda2 even though it unpacks the kernel from the usb drive and starts the graphical boot screen. 

2. has anyone got fglrx working on breezy (kernel 2.6.12-8)? i followed numerous threads on the forum, but none seems successful. everything was tried after fresh system installation. and i did notice the fglrx.ko file in /lib/module/volatile and it's persistently created. any cure for this?

---

### Post by mlomker on 2005-10-06
```
2. has anyone got fglrx working on breezy (kernel 2.6.12-8)?
```

Many people have and it's the latest version of ATI's drivers.  I'm not sure which how-to's you looked at but [mine]("http://www.ubuntuforums.org/showthread.php?p=348911") works pretty well.

If you let us know what results you're getting then someone will probably have an idea.

---

### Post by replacement on 2005-10-07
[QUOTE=mlomker]```
2. has anyone got fglrx working on breezy (kernel 2.6.12-8)?
```

Many people have and it's the latest version of ATI's drivers.  I'm not sure which how-to's you looked at but [mine]("http://www.ubuntuforums.org/showthread.php?p=348911") works pretty well.

If you let us know what results you're getting then someone will probably have an idea.[/QUOTE]
thanks for the reply. there've been too many tutorials on this subject. yours is perhaps the longest discussion :D  anyway, i read carefully, but it didn't work for me. here is what i did. 

1. a fresh install of breezy (kernel 2.6.12.8 and headers are installed)
2. install fglrx driver using apt-get
3. set driver to fglrx in xorg.conf and set UseInternalAGPGART to no

from Xorg.log.0, it said DRI initialization failed ...etc... no 3D acceleration. from "dmesg | grep fglrx", there is a big ERROR line ... couldn't remember the details. "lsmod | grep fglrx" showed fglrx module loaded, but no GLX from ATI. i tried to overwrite the library file you mentioned in your tutorial. it didn't work. i tried and installed the driver through ATI's source (ie. download the driver, alien, ..., sh make.sh ... ). not working. then i realized there are two fglrx.ko after the ATI's source driver is compiled. and they have different size. the one looks suspicious is in that volatile directory, and it gets generated at every boot time. do you see this file in your /lib/module/volatile? which version of ubuntu have people got ati driver working on? anyway, this isn't just me complaining. if i got rid of the one in volatile, and insmod the one compiled from ATI source. then after restart the server, i can see DRI successfully initialized from xorg.log.0, but still GLX through mesa. someone mentioned volatile/fglrx.ko is created by a process in /etc/init.d/, but no mention of the name. anyway ...

---

### Post by mlomker on 2005-10-07
>  file in your /lib/module/volatile? 

Let me try deleting that file on my test box and I'll see if it comes back.  My personal desktop is Hoary and the 'volatile' directory seems to be new with Breezy.

> which version of ubuntu have people got ati driver working on? 

Both, but it does vary.  The stock Hoary driver worked for a lot of people as well but didn't for me.

> from xorg.log.0, but still GLX through mesa. someone mentioned volatile/fglrx.ko is created by a process in /etc/init.d/, but no mention of the name. anyway ...

I just found one other [thread]("http://www.ubuntuforums.org/showthread.php?t=59299") about this.  The poster thought it was due to having the **linux-restricted-modules-*** package installed.  Do you have that package installed for wireless support or something else?  That package will reinstall the fglrx.ko file every time that you have a kernel update (which is pretty frequent in Breezy right now).

---

### Post by replacement on 2005-10-07
[QUOTE=mlomker]I just found one other [thread]("http://www.ubuntuforums.org/showthread.php?t=59299") about this.  The poster thought it was due to having the **linux-restricted-modules-*** package installed.  Do you have that package installed for wireless support or something else?  That package will reinstall the fglrx.ko file every time that you have a kernel update (which is pretty frequent in Breezy right now).[/QUOTE]

yes. isn't this package required by fglrx? thanks.

---

### Post by mlomker on 2005-10-07
[QUOTE=replacement]yes. isn't this package required by fglrx? thanks.[/QUOTE]

No.  It appears that the linux-restricted package is now being installed by default, but that was not the case a few weeks ago.  You can remove the linux-restricted package and then install xorg-driver-fglrx instead.  That package doesn't get updated with every kernel update.

I just ran a test and removing the restricted package does stop creation of the contents of the volatile folder.

---

### Post by replacement on 2005-10-08
[QUOTE=mlomker]No.  It appears that the linux-restricted package is now being installed by default, but that was not the case a few weeks ago.  You can remove the linux-restricted package and then install xorg-driver-fglrx instead.  That package doesn't get updated with every kernel update.

I just ran a test and removing the restricted package does stop creation of the contents of the volatile folder.[/QUOTE]

okay, now i removed the restricted module and installed the ATI driver the hard way through (sh make.sh and sh make_install.sh). the outcome is fglrx loads, DRI enabled. everything (xorg.0.log and dmesg | grep fglrx, and lsmod | grep fglrx). but no GLX, still mesa 3D. anything to install/remove?

---

### Post by mlomker on 2005-10-08
Are you using the drivers that came with Breezy or a downloaded file?  I ask because they are different.  The ATI ones require overwriting one of the MESA libraries before it works, which is why I have to use a --force option in my how-to.  The Breezy driver doesn't require that because it is packaged differently, from what I understand.

---

### Post by replacement on 2005-10-09
[QUOTE=mlomker]Are you using the drivers that came with Breezy or a downloaded file?  I ask because they are different.  The ATI ones require overwriting one of the MESA libraries before it works, which is why I have to use a --force option in my how-to.  The Breezy driver doesn't require that because it is packaged differently, from what I understand.[/QUOTE]

i installed the ATI driver. which file needs to be overwritten? libGL.so.? is it done by the "sh make_install"?

---

### Post by mlomker on 2005-10-09
> i installed the ATI driver. which file needs to be overwritten? libGL.so.? is it done by the "sh make_install"?

It's the /usr/X11R6/lib/libGL.so.1.2 file.  It gets overwritten when you install the .deb file (assuming you did the alien conversion with my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911")).  If you used their .sh installer then it is supposed to install it.

---

### Post by replacement on 2005-10-10
[QUOTE=mlomker]It's the /usr/X11R6/lib/libGL.so.1.2 file.  It gets overwritten when you install the .deb file (assuming you did the alien conversion with my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911")).  If you used their .sh installer then it is supposed to install it.[/QUOTE]

eventually, it's working. what i had to do is to delete all files with fglrx in their names, download the ati 50MB driver file and did "sudo sh" on that.

---

