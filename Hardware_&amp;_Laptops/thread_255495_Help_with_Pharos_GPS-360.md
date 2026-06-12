---
title: "Help with Pharos GPS-360"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by proteo on 2006-09-11
I have a Pharos GPS-360 that come with Microsoft Streets & Trips 2006 (it was cheaper than any other gps i could find :biggrin: ), and i want to use it with my laptop, but its not recognized, the product id is 0xaaa0 instead of 0x2303, after some searching i found this:
[http://archives.neohapsis.com/archives/fulldisclosure/2004-10/0310.html]("http://archives.neohapsis.com/archives/fulldisclosure/2004-10/0310.html")
 and tried to follow the instructions, but i don't have the file pl2303.h ](*,) , can somebody help me?

thanks :-D

PS: my laptop is an eMachines m6810, athlon64 3200+, Ubuntu 6.06 AMD64.

---

### Post by Mud.Knee.Havoc on 2007-10-19
I would have sent an email to you, but it's not listed in your profile.

Any luck with this?  Has anybody gotten this to work properly?

---

### Post by tgalati4 on 2007-10-19
I assume that you are using the USB dongle that comes with the gps?  The driver loads automatically with my Pharos 360 in Dapper.

With the gps plugged in, post the output of:

>lspci -vv

and

>lsmod

---

### Post by Mud.Knee.Havoc on 2007-10-20
Okay, I have attached the output of both commands.  The output of lspci -vv doesn't seem to show anything about the gps puck... although I can't make out all of it. :D

You also hit upon the initial thread that I made the other day... I'll quote a bit:

> I assume that you are using this outdoors.

The Pharos GPS-360 uses the SirFStar II chipset which is weaker than the current SirFStar III units out now. You need to be outside, in the clear to get decent satellite lock. If you are inside or under trees, satellite lock is spotty.

Grab the latest gpsdrive and compile it from source. It's much better than the old version in the repos. You don't need gpsd if you set the correct /dev/ttyUSB0 port in gpsdrive's preference settings.

I am using this both in my office and testing it outdoors whenever I think I might be on to something.  Unfortunately, I'm not too optimistic at this point.  Others have gotten SeaClear for Windows running under wine.  When I try to get it going, I get an error that the COM port isn't found, even though I made the symbolic link (properly, I hope) that was suggested somewhere else.  GPSdrive just comes up with simulation mode, although I will compile the newer version as you suggest. 

I can't find enough info out there about this gps, though.  For example, in GPSDrive, there are four check boxes in the GPS setup (for serial, Garmin, etc).  Should I run it with everything unchecked, or should I select serial (if I understand correctly, the bulge in the gps cord is a serial/usb converter) and just keep the /dev/ttyUSB0 as the port?

Thank you very much for the help!

---

### Post by Mud.Knee.Havoc on 2007-10-21
I'm still having no luck.  I did notice, though, after running "dpkg-reconfigure gpsd", in order to have gpsd run automatically at boot,that it says:

> * Starting GPS (Global Positioning System) daemon gpsd_____________        [[COLOR="Red"]fail[/COLOR]]

---

### Post by Mud.Knee.Havoc on 2007-10-24
I finally got to the bottom of my problems.  I installed Win XP in order to test everything out - turns out the gps puck was bad.  I returned it for a new one and everything works fine now. :)

---

