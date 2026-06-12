---
title: "Gutsy install Xorg problems"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by HeresJohnny on 2007-10-20
I'm going to cross-post in Launchpad so hopefully we can get this issue resolved.  I run a Compaq Presario V2000 series, 1.5 GB Ram, 60GB hard drive, running ATI Radeon Xpress 200M.  I tried to do a clean install of Gutsy, which seemed to go well.  Once I rebooted, though, at the point where the splash screen starts going as Xorg gets going and modules are loading, before you log in, my screen died.  Nothing at all.  Repeatedly.  Every time at exactly the same moment.

I booted using recovery mode and it dropped me to a command line.  I called the gnome desktop manager (gdm) with some success, but it wouldn't initialize HAL.  After a lot of head scratching and searching the forums, I figured out it was a problem with X.  Looking into it more revealed that X crashed because it was trying to load fglrx, but fglrx wasn't there.  Ok, no problem right?  I tried to apt-get install xorg-driver-fglrx, but the error message read 'failed to resolve 'archive.us.ubuntu.com' (or something like that).  I'm guessing I have to edit my sources.list file, but I don't know how to do that from the command line- I've always used Gedit.

I'm really frustrated at this point.  Why call a driver that isn't there yet?  Why didn't it install during the process, if it was going to call the driver right after boot?  Rats!

If anyone can help me to either:  edit my sources.list file from the command line, switch to a different driver and restart X, or give some other solution, I'd be thankful.  Right now, I don't have the knowledge of how to post my xorg.conf file; all I have is the command line.  I'm typing this using the liveCD; I'll check back later.

---

### Post by shouravv on 2007-10-20
I had this same problem, this is caused by too high default refresh rate set by Gutsy that is not fully compatible with your monitor / VGA card / driver.

I solved it by replacing the new xorg.conf file with the old auto backup one.

First, do a ls on /etc/X11/xorg.*

Second, back up your current xorg.conf

Third, replace the current xorg.conf with an older version, preferably with the xorg.conf.original one.

For me, it worked like this:

{{{

bob@bob:~$ ls /etc/X11/xorg*

/etc/X11/xorg.conf                 /etc/X11/xorg.conf.20061201143855  /etc/X11/xorg.conf.failsafe      /etc/X11/xorg_config_back
/etc/X11/xorg.conf.1               /etc/X11/xorg.conf.20061201232715  /etc/X11/xorg.conf.failsafe.bak  /etc/X11/xorg.conf.original-0
/etc/X11/xorg.conf.20061027062407  /etc/X11/xorg.conf.20071019        /etc/X11/xorg.conf.fglrx-0


bob@bob:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-latest

bob@bob:~$ sudo cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf

}}}

Now reboot the machine. If something goes and you can't get GUI, you can restore the backup you just made, or try other automatic backup the system made earlier.

Note: The other solution might be to edit xorg.conf by hand editing the refresh rate. My montior's manufacturer suggested rates are 42-72 Hz, whereas Gutsy set it at 75. I prefer having it at 60.

---

### Post by HeresJohnny on 2007-10-20
[FONT="Trebuchet MS"]Okay, I have repaired the damage, but I'm not sure I would recommend the process by which it came about.  
1.  Reinstall 7.04 Feisty
2.  Enable fglrx through the 'Restricted Drivers Manager'
3.  Do the basic updates that come up.
4.  Reboot.
5.  Call for the Update Manager.  At this point, you'll get a message near the top that says a new release is available.  
6.  Use this channel to upgrade your system to Gutsy.

Because I did a clean install, it removed my fglrx settings, and for some reason, didn't replace it.  This way was a huge PITA, but it got done.  I'm glad, too, because Gutsy rules.  SCIM works as soon as you configure it, wireless works out of the box, the only thing I have to work on is enabling desktop effects, which was also a pain in Feisty.  Go Gutsy![/FONT]:guitar:

---

