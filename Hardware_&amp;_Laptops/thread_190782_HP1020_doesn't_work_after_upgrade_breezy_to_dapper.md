---
title: "HP1020 doesn't work after upgrade breezy to dapper"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by gostview on 2006-06-06
Hi all, I've updated my Breezy to Dapper, all goes fine, but my printer HP1020 Laserjet now cannot be detected, although it was before and work fine.

It seems that the whole printing stuff got changed a lot with the latest updates and now it does not recognize anything, neither my usb connection.

my lsusb says it still there:
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:2b17 Hewlett-Packard
but gnome-cups-manager didn't find it.

I try to select the printer with cups web manager, but no printer on usb was detected.

I did install the foo2zjs drivers in my breezy, and I installed it again, but nothing happend.

What is going on?  
I try to see if  HP-LaserJet_1020-foo2zjs.ppd is still there, and I found it in /usr/share/ppd/linuxprinting.org-gs-builtin/HP/HP-LaserJet_1020-foo2zjs.ppd

So; is it a bug?
anyone can help me or have any suggest? 
tnx

---

### Post by poekie on 2006-06-09
Same here, only with my Canon 350i printer. Used to work fine, now CUPS doesn't see it. At least, CUPS finds it, but test pages aren't printed. And neither are normal pages.

---

### Post by poekie on 2006-06-17
And now even Cups can't find it anymore.... the new usbstuff f*cked up my printer, thanks :(

---

### Post by azc on 2006-06-17
Hello Gostview,

This is another thread I saw regarding the HP-1020 when I was trying to fix my printer problem:

[http://www.ubuntuforums.org/showthread.php?t=183557](http://www.ubuntuforums.org/showthread.php?t=183557)

I don't have the HP-1020, and so I haven't tried it. Best of luck.

---

### Post by poekie on 2006-06-18
[http://ubuntuforums.org/showthread.php?t=196499](http://ubuntuforums.org/showthread.php?t=196499)
This helped for me :)

---

### Post by coalastonmatt on 2006-11-23
Hi everyone

I am hoping someone out there can help me. I am running dapper i386 on a Sony Vaio P4 laptop (PCG-FRV26) where it has been great so far. The first time I plugged in my HP laserjet 1020 it was recognized by the system, everything looked good, except nothing would ever print.

I tried apt-get uninstall foo2jzs and apt-get install foo2jzs in case there was anything wrong with my driver. No dice.

I then followed the instructions at

[http://ubuntuforums.org/showthread.php?p=483421](http://ubuntuforums.org/showthread.php?p=483421)

the "make" went fine with no errors and only one warning. I then ran make install and make install-hotplug, then /etc/init.d/cupsys restart. When I power-cycled the printer it whirred twice, and /var/log/syslog indicated successful upload of the firmware. However, using gnome-cups-manager no printer was now detected, and I had no way of installing it. I tried stopping and restarting udevd but this didn't help.

I then tried the foo2jzs at [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/). This one won't compile:

foo2xqx.c:87: error: ‘DMMEDIA_STANDARD’ undeclared here (not in a function)
make: *** [foo2xqx.o] Error 1

I am now a bit stuck and would appreciate some help. Thanks!

---

### Post by coalastonmatt on 2006-11-24
Well, I fixed it, but had to upgrade the whole system to Edgy:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Then follow these patch instructions

[https://launchpad.net/distros/ubuntu/+source/foo2zjs/+bug/65618](https://launchpad.net/distros/ubuntu/+source/foo2zjs/+bug/65618)

The edgy upgrade also of course stopped my wireless working, eventually fixed that by following these instructions:

[https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983)

reboot was necessary after modprobe ndiswrapper.

Now it is working, about 5 hours in all. Hope this helps someone...

---

