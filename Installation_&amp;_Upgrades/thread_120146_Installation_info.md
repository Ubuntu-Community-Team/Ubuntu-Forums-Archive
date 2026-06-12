---
title: "Installation info"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by mh1 on 2006-01-20
Hi

I'm having trouble installing Ubuntu.. I'm using an older machine and although the BIOS apparently supports booting from CD, i am unable to get the to work.

As such i was wondering other installation possibilities? How do I install from a network? can i copy an install file to the hard drive and install from there?

In an (last ditch) attempt i was pretty certain was going to fail I placed the hard drive in a different computer and installed ubuntu. It boots but the GUI fails to load and i'm left with a command prompt. Being new to linux this doesnt help me... is there a way to reinstall from here to fix the numerous driver errors that no doubt occured.

Any help would be appreciated.
mh

---

### Post by morphodone on 2006-01-20
whew, goodness
there are many variables in your problem

what happens when you boot from the cd in the first computer?

---

### Post by mh1 on 2006-01-21
with the boot cd in the first computer it just boots from the hard drive. Removing the hard drive from the boot list in the BIOS provides and error, something along the lines of having nothing to boot.

In the second computer the boot cd runs normally and will install properly.

---

### Post by lha on 2006-01-21
[QUOTE=mh1]Hi

I'm having trouble installing Ubuntu.. I'm using an older machine and although the BIOS apparently supports booting from CD, i am unable to get the to work.

As such i was wondering other installation possibilities? How do I install from a network? can i copy an install file to the hard drive and install from there?

In an (last ditch) attempt i was pretty certain was going to fail I placed the hard drive in a different computer and installed ubuntu. It boots but the GUI fails to load and i'm left with a command prompt. Being new to linux this doesnt help me... is there a way to reinstall from here to fix the numerous driver errors that no doubt occured.

Any help would be appreciated.
mh[/QUOTE]

If you have Windows (DOS may also work), you can dowload a few MB's and start installation [like this]("http://ubuntuforums.org/showthread.php?p=647002#post647002").

---

### Post by mh1 on 2006-01-28
I attempted to do this a few minutes ago, the installation began but when installing the base system an error occured. It read...

Debootstrap Error
An error has occured:

Invalid release signature (key id 40976EAF437D05B5)
check /target/var/log/bootstrap.log for the details

What does this mean and how can I fix it?

thanks
mh1

---

### Post by lha on 2006-01-29
[QUOTE=mh1]I attempted to do this a few minutes ago, the installation began but when installing the base system an error occured. It read...

Debootstrap Error
An error has occured:

Invalid release signature (key id 40976EAF437D05B5)
check /target/var/log/bootstrap.log for the details

What does this mean and how can I fix it?

thanks
mh1[/QUOTE]

AFAIK, this error happens when signature on the files you are downloading during the install have a signature that installer doesn't recognize. Where did you get the files you are using to start installer? Maybe try to get the files from somewhere else.

As the error message says, looking into bootstrap.log might give more info on this. You can press <control>-<alt>-<f2> to get into a console. Press enter to activate it and type ```
cat /target/var/log/bootstrap.log
```. The interesting bits should be in the end of that file.

---

### Post by mh1 on 2006-01-29
I got the files to start the installer from the post above, which links to some other sites. It does state that these files can be copied from the installer iso so i will try that and see if that works.

I can have a look at that log but I'm pretty sure it wont mean much to me :)

Thanks for your help.

---

### Post by az on 2006-01-29
[QUOTE=mh1]Hi

I'm having trouble installing Ubuntu.. I'm using an older machine and although the BIOS apparently supports booting from CD, i am unable to get the to work.[/QUOTE]

There is a utility called smart boot manager.  It is in the install directory on the install cd.  You rawwrite it to a floppy and boot it.  It detects all possible boot options and you can boot the cdrom using it if your computer refuses to do that.


[QUOTE=mh1]
In an (last ditch) attempt i was pretty certain was going to fail I placed the hard drive in a different computer and installed ubuntu. It boots but the GUI fails to load and i'm left with a command prompt. Being new to linux this doesnt help me... is there a way to reinstall from here to fix the numerous driver errors that no doubt occured.

[/QUOTE]

All you need to do from that point is reconfigure your video card - it is looking for the video card from the computer you install it.

Boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

Then
init 2

Unless the drive orders are different, you should be good to go with just that.

---

### Post by mh1 on 2006-01-29
[QUOTE=azz]There is a utility called smart boot manager.  It is in the install directory on the install cd.  You rawwrite it to a floppy and boot it.  It detects all possible boot options and you can boot the cdrom using it if your computer refuses to do that.[/QUOTE]

I like this option. What exactly do you mean by rawwrite? Do i just copy the file/directory to a floppy and boot with the floppy and cd loaded?

Thanks for your help
A very frustrated mh1 :)

---

### Post by lha on 2006-01-30
[QUOTE=mh1]I like this option. What exactly do you mean by rawwrite? Do i just copy the file/directory to a floppy and boot with the floppy and cd loaded?

Thanks for your help
A very frustrated mh1 :)[/QUOTE]

You have to use a program called [rawwrite]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm") to copy sbm.bin to a floppy. Sbm.bin is in /install folder on the install cd.

---

### Post by mh1 on 2006-01-31
I'm just about to give up on this whole thing and chuck the computer in the bin.

This rawwrite program doesnt work, it just gives me an error and wont write the file or whatever its trying to do.

Error is: Write failed, The device is not ready.

Should i be trying to write the sbm.bin file? There are no instructions with the program so perhaps I am not using it correctly?

Any help you can give me would be great because I'm seriously starting to lose my cool over this.

mh

---

### Post by morphodone on 2006-02-01
[QUOTE=mh1]This rawwrite program doesnt work, it just gives me an error and wont write the file or whatever its trying to do.

Error is: Write failed, The device is not ready.
[/QUOTE]

Just copy the sbm.bin file to your hard drive and then use rawwrite.

When you run rawwrite be sure to have a formatted, writable floppy disk in your floppy drive.

Slackware has a small guide on using rawwrite.  [HERE]("http://www.slackware.com/install/bootdisk.php")

---

### Post by mh1 on 2006-02-01
After several attempts Ubuntu is up and running :)

I'd like to thank everyone who posted, your help was invaluable and much appreciated.

Thanks again
mh

---

