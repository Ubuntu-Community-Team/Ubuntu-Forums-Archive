---
title: "Acer 5920G and infrared device"
date: 2010-01-15
forum: Hardware
---

### Post by daehenoc on 2010-01-15
Hi all,

I have an Acer 5920G (sub model number 5A2G25Bn) which I want to use as the frontend to my MythTV system.  (The unit was dropped while open and as a result the LCD panel was shattered, so I've pulled that out.)

It's all going well, and now I'm trying to get the infrared receiver working.  I think that the correct module is the lirc_wpc8769l one, and it is included in the lirc-modules-source package.  I've installed module-assistant and used that to build all the extra lirc modules.  However:
[list]
[*]When I do the following: sudo m-a auto-install lirc-modules, the modules (except lirc_wpc8769l!) get built into the /lib/modules/2.6.31-17-generic/updates/dkms/ directory, but then m-a reports "The source tarball could not be found! Package lirc-modules-source not installed?"  But it really is!
[*]I investigated the file /usr/src/lirc-0.8.6/lirc-modules-source.conf and lirc_wpc8769l *isn't included in the list of modules to build!*
[/list]
I've edited the lirc-modules-source.conf file to include the lirc_wpc8769l module.  So I need to figure out how to get module-assistant to go back and recompile the modules, and then how to convince m-a that lirc-modules-source really is installed!  Any tips?

---

### Post by daehenoc on 2010-01-16
OK, I've given up on trying to get the module compiled from the lirc-modules-source package and downloaded the lirc source code from sourceforge.  I have successfully compiled and loaded the lirc_wpc8769l module and got a /dev/lirc0 device created, woot!

I would like the lirc_wpc8769l module loaded automatically on boot, I created the /lib/modules/2.6.31-17-generic/kernel/ubuntu/lirc/lirc_wpc8769l directory and copied the module into it, with the correct permissions on the directory and module file, but of course the module won't load by running 'modprobe lirc_wpc8769l'.

What do I have to do to get this new module recognized by modprobe?

---

### Post by daehenoc on 2010-01-17
Righto - figured out what files needed to be patched in the lirc-0.8.6 directory.  The patches are on the bug logged against the lirc-modules-source (version 0.8.6-0ubuntu2) package: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/508266](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/508266)

I've 'fixed' this problem until the package is updated:
* Remove any previous lirc-modules-source install: sudo aptitude purge lirc-modules-source
* Use dpkg to unpack only the lirc-modules-source deb file: sudo dpkg --unpack /var/cache/apt/archives/lirc-modules-source_0.8.6-0ubuntu2_all.deb
* Download the patches from the bug into the /usr/src/lirc-0.8.6 directory (this directory created by dpkg when you use the --unpack)
* Apply the patches: sudo patch -i Makefile.patch, sudo patch -i dkms.conf.patch, sudo patch lirc-modules-source.conf.patch
* Complete the installation of lirc modules with aptitude: sudo aptitude, press 'g' to finish the installation of dpkg
* You should now have a working lirc_wpc8769l.ko module in the /lib/modules/2.6.31-17-generic/updates/dkms directory.

This worked for the x86_64 architecture, if you are using another architecture such as i686, you should be able to download the lirc 0.8.6 source from the lirc sourceforge site and compile the module manually after doing the above, then copy the .ko file from the lirc source directory to the /lib/modules/etcetc directory.

The module doesn't load automagically, so I added it to the /etc/modules file.

---

### Post by P4man on 2010-10-16
Hi,

I have the same laptop, at least also an 5920G but the sub version is different. I wonder if I have the same IR receiver, since lsusb and lspci show nothing? No option in the bios to enable it either (I vaguely recall it used to work with vista though, so it has one).

Now the bugs you encountered seem to have been fixed meanwhile, but I cant get lirc to recognise my IR. Any tips?

---

### Post by daehenoc on 2010-10-17
Oh thank god, I thought I was going insane talking to myself here :p

I can't remember how I knew what the type of hardware was...  That laptop has since been repaired and moved on, so I don't have it with me anymore to check.  I'm using a 5920 (non-G model) and it has the panel for an IR receiver, but I don't know if there actually is an IR receiver in this laptop.  lspci and lsusb also show no IR device on this laptop - as I type this, I think that I remember finding out what type of device it was from another forum somewhere.

What happens when you load the module?  I think there's an option for verbose mode when doing a modprobe, see if that gives you any further information.

---

### Post by P4man on 2010-10-18
I didnt try, since the bug report claims its fixed and it ought to autoload now.

Anyway, I decided to use a spare PC for this project and I hooked up a USB Ir receiver that works fine, so Im not going to look too hard for a solution any longer.

---

