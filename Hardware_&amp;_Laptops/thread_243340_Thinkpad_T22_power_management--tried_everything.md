---
title: "Thinkpad T22 power management--tried everything"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by tessuraea on 2006-08-24
Maybe not everything; that's why I'm asking for help.  I'm a complete newbie; this is my first linux installation.  I've installed 6.06 on my Thinkpad T22 with very few problems.  I followed the instructions at thinkwiki to get the system to boot up properly:  added Option "BusType" "PCI" and Option "DmaMode" "None" to xorg.conf.  That worked perfectly.  Then shutdown started hanging on the LVM volume manager, and google searches found me several people suggesting removing that package.  That took care of that problem.

Those are the only substantive changes I've made to the system; other than that, it's a fully updated Dapper install.  I still have Windows on a partition but it's not currently bootable.

The problem is one common to the T2x thinkpads, according to all the sources I can find on the web; suspend and hibernate don't work.  The keyboard shortcuts lock the screen or turn it off instead of putting the computer to sleep, and choosing those options from the menu suspends but then the laptop won't wake up.  I have to remove the battery to get it to start up again.  Everything I can find online says that acpi doesn't work with the older systems, so I should stop using it and enable apm.  

I've done that, following various instructions about changing the kernel boot string and eventually the detailed instructions at [http://www.ubuntuforums.org/showthread.php?t=237264]("http://www.ubuntuforums.org/showthread.php?t=237264")

 I've tried combinations of noacpi acpi=off apm=on, etc.  The power management modes still don't work; the computer doesn't suspend. It does various things depending on whether I use the keyboard shortcuts or the menus, from blanking the screen and beeping to starting the screen saver and locking the screen, to flickering a bit and coming back to the desktop.  At that point it's usually completely unresponsive and I have to reboot.

Any suggestions would be appreciated greatly...  I've searched forums and googled, and I haven't found anything I haven't tried yet, except a few people offering scripts that I don't have a clue how to use.  Thinkwiki has detailed instructions for recompiling my kernel to make acpi work with the thinkpad, including an acpi driver I can download.  I'm afraid that still seems a little bit intimidating...

---

### Post by Bmbshl on 2006-09-01
This is way off your topic, but I'm desperate for help.

I have a T21. Have you tried to install video drivers on your T22?  I can't make the Savage card work and will ultimately have to go back to Windows if I can't figure it out soon.  Sorry for the abrupt change in direction, but like I say I'm desperate.  Thanks.

---

### Post by tessuraea on 2006-09-02
If the problem is that on boot up you end up with a white, unblinking cursor in the upper left and no picture, thinkwiki has a suggestion that involves editing your xorg.conf.  It worked for me.  Another user here on the Ubuntu forums had a different solution that worked for him but didn't work for me.

Instructions straight from thinkwiki.org:

1) Choose Safe Boot instead of Normal Boot. It is the second line on the boot menu.

2) Click Applications > Accessories > Terminal

3) Type: Sudo -H -s (This command gives you power to modify the xorg.conf file later.)

4) Type: gedit /etc/X11/xorg.conf (Make sure that the "X" in "X11" is capital X, and the "11" is number "eleven" not lowercase "LL".)

5) Add the following two lines into the "Device" section of your xorg.conf.

Option "BusType" "PCI"
Option "DmaMode" "None"

****************************

This works for me.  If that's not your problem, though, I don't have anything to offer.  I'm still new.

Oh, and alternately, user derekbei's solution:  exactly like the above directions, only instead of adding those two lines to the "Device" secion of xorg.conf, add 'VideoRam 8192'.  This works for him and seemed to work for me, but then stopped so I went back to thinkwiki's less elegant solution.

---

