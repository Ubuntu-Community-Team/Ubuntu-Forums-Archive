---
title: "Can't put hard disk in sleep mode using hdparm"
date: 2009-05-06
forum: Hardware
---

### Post by miro123 on 2009-05-06
I have installed Ubuntu 9.04 on an external usb hard disk, and I want to put the two internal hard drives to sleep. 

I have tried the sudo hdparm -Y /dev/sdX command, and it seems to work for the sata drive, sda. The other drive /dev/sdb is a pata disk and I can hear it spin down and immediately spin up again. 

I checked with
sudo hdparm -C /dev/sdb

and it says:
/dev/sdb:
 drive state is:  active/idle
Another  [thread]("http://ubuntuforums.org/showthread.php?p=6099044#post6099044") mentions a similar problem, and I tried the nautilus setting but it didn't work.

A while ago I had Ubuntu 8.10 installed on the internal sata drive, and could put the pata disk to sleep with hdparm.

Thanks for any suggestions!

---

### Post by ameno on 2009-05-09
ah i saw the other thread first ([my comment there)]("http://ubuntuforums.org/showpost.php?p=7247857&postcount=6"), lets continue here because the other one is "solved" anyway.

in my case its sdb too, but its an internal sata drive.
hddtemp and smartd are not the cause, the nautilus settings didnt work either (which was pretty obvious before... because the drive is not mounted).
lsof -n | grep sdb does not help either. im pretty much out of ideas atm.
my guess is udev (many changes in jaunty) or the kernel itself, but the latter is not likely.


edit: i found another one with the problem [here]("http://www.linux-archive.org/gentoo-user/269307-cant-put-hard-disk-sleep.html"). his kernel version is similar to the one used in jaunty.

another thing i just noticed: when the drive shuts itself down by the spindown timeout (hdparm -S), it works!

edit: since im pretty sure this is a bug, i reported it in launchpad: [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/374287](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/374287)

---

### Post by miro123 on 2009-05-10
I found these discussions and bug reports, it seems that it's udev.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522091]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522091")
[http://groups.google.com/group/linux.debian.user/browse_thread/thread/3119d3f49139b922]("http://groups.google.com/group/linux.debian.user/browse_thread/thread/3119d3f49139b922")
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=526516]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=526516")

---

### Post by j-g-faustus on 2009-05-16
Same issue here - /dev/sda works as expected, /dev/sd[bcd] does not.
The spindown timeout does not work either, whether I call hdparm directly or use hdparm.conf. (Using 3 WD Green disks)

I can make the disks sleep by invoking both spindown (hdparm -S) and sleep (hdparm -Y), but they still wake after a few minutes and do not spin down again.

What options do I have? Would downgrading to Ubuntu 8.04 fix it?

Thanks

---

### Post by j-g-faustus on 2009-05-16
Tried downgrading to Ubuntu Server 8.04, but the 8.04 installer refused to recognize the SATA CD-ROM it was running from. Tried searching for a fix and found a few posts and a bug report, but nothing useful except "try a later version".

Instead I upgraded the Server 9.04 kernel to 2.6.29, and it appears to work: /dev/sd[bcd] still do not spin down on their own accord, but at least they can be put asleep, and stay asleep, with hdparm -Y.

Isn't there a way to upgrade the kernel using apt-get? 

I tried this description: [http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/) but "apt-cache search kernel-image" returns nothing useful and "apt-get install kernel-image" says there is no such package.

So I went for the manual install described towards the end of this thread: [http://ubuntuforums.org/archive/index.php/t-1140437.html](http://ubuntuforums.org/archive/index.php/t-1140437.html)
* get 3 kernel files from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
I used kernel 2.6.29.3. You need 
* linux-headers-....-all
* linux-headers-...-i386 (32 bit) or ...-amd64 (64 bit)
* linux-image-...-i386 (32 bit) or ...-amd64 (64 bit)

Save to desktop, install by doubleclick.
The files must be installed in this order:
* linux-headers-...-all
* linux-headers-...-[i386 or amd64]
* linux-image...

Reboot, and there should be an entry in the GRUB boot loader for the new kernel.

---

### Post by j-g-faustus on 2009-05-18
Just some feedback on the kernel upgrade:
I have been running it for a day or two. It solves the spindown problem, the harddisks now work as they are supposed to.

I was worried that a new kernel would introduce new problems, so far it hasn't. Except that I couldn't install VMWare, it won't compile with the new kernel. 
There is supposed to be a patch somewhere, but haven't tried it - when you are new to this stuff it takes ages to track down how compilation is supposed to work, how to apply a patch, how to figure out where the patched files should go so the VMWare build script finds them. 

I think I've spent quite enough time already, so I'll settle for the new kernel - it works well enough, and VMWare will probably support it officially in another 6 months or so. I guess it's the smallest evil available :)

---

### Post by ameno on 2009-05-25
actually the problem was hdparm itself (which triggered udev unintenionally).
it is fixed in hdparm 9.14.

and the new kernel was just a temporary fix for me, with a later reboot the old behaviour was back, although i dont know why.

lets hope someone notices my bugreport and uploads the new version to karmic :/

---

### Post by miro123 on 2009-06-01
Is it possible to benefit from this new version of hdparm before it comes up in repositories? Do you know how difficult would it be to install it manually?

---

### Post by ameno on 2009-06-01
i just built my first .deb, although its probably not even necessary.
the problem is, that important (pseudo-)packages (acpi-support pm-utils ubuntu-standard) depend on it. this makes it a bit of a problem to just remove the debian package and replace it by a self-compiled version.
one could try to just replace the executable, this will probable work.

i didnt bother, because i wanted to try to build a .deb for a long time.
its pretty easy for such a simple package: download the source, run db_make to create .deb specific helper file templates, customize them (minimum: changelog name/mail must match a gpg key; the control file is important (version etc), run debuild. done

details can be found here: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

after that you will have an installable .deb, that replaces the existing one without much of a hassle. and... sleep mode works ;)

hth

---

### Post by miro123 on 2009-06-02
Well I just compiled from source and run the new executable in place - it works :) I think I'll just use it like this and leave the old one in /sbin...

---

