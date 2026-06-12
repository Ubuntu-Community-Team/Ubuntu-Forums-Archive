---
title: "D600 running on battery"
date: 2008-10-17
forum: Hardware
---

### Post by lofgren on 2008-10-17
Hi people,

[B]wondering if anyone has had the same issues as me..?
[/B]
After a bit of mucking around (admittedly ages ago) I got the wireless card working on my D600 - it works great!

Until... I unplug the power lead and run off batteries.
**I will be in the middle of active browsing and find wireless has disconnected.**

Last night after repeated ***ifdown eth1/ifup eth1*** commands (this seems to fix it temporarily) I also experienced freezing.

The laptop wouldn't respond to anything but powering off and back on.

I suspected power saving, but couldn't find any settings or anything obvious in the system logs.

It is fine in Windows on the same machine.

cheers,
Matt

---

### Post by gargouille on 2008-11-25
I had the same problem:

> **gargouille said:**
> HARDWARE:
Dell Latitude D600
Broadcom BCM4309 (bcm43xx)


PROBLEM:
Wireless connection disconnects.  When shutting down, or rebooting, the following error appears and keeps repeating:  b43-phy0 ERROR: PHY transmission error

kern.log entry:
Nov 25 18:25:57 coruscant kernel: [   92.216246] wlan0: no IPv6 routers present
Nov 25 18:26:02 coruscant kernel: [   96.820027] __ratelimit: 386 callbacks suppressed
Nov 25 18:26:02 coruscant kernel: [   96.820027] b43-phy0 ERROR: PHY transmission error


FIX:
found in Ubuntu help:

3.3.6.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

### Post by MarkusAurelius on 2009-01-01
Hi,

I experience the same **freeze** problem.  I just received a comment on my blog from someone else having the issue with a D600..  It is not wireless only: it is the whole machine...

You are right that it has something to do with the *power saving*.  Although it does not happen all the time, the *Panel Icons* are completely non-responsive.  Even if you open a *Terminal Shell*, you can't type anything in it...  I tried that so that I could do a simple *reboot*, but I could not!

When this occurs, the process **hald-addon-dell-backlite** chews up the cpu!!  The only way out is to hard power Off & On.  Even if you plug it back in, it remains unresponsive!

The last time it occurred to me is when I unplugged the power cord, the *Brightness Applet* came on (that's OK) but it was frozen there...  And of course, **hald-addon-dell-backlite** went nuts as usual.

I highly suspect this is a bug on the D600 (I will be trying an Inspiron 6400).

That indicates to me that there is a bug in the power stuff...  Unfortunately I have no idea on how to report it.  Could anyone help out here?

As for the wireless, I have another issue for the D600 as I have a PCMCIA D-Link: I simply pull it out and put it back in (before it asks for the password again!!) and all is well... That occurs only when coming back from Hibernate or Suspend, never on battery only.

Incidentally, I have an Apple PowerBook G4 and an HP nc6220 on 8.10 as well, and these work flawlessly on and off battery mode.

Many Thanks & Regards!

---

### Post by hooksie007 on 2009-01-08
I also have a D600 that acts the same.  I switched from PcLinuxOs MiniMe which had no problems to UBUNTU 8.10, then I tried UBUNTU 8.04, and the same thing.  I like UBUNTU better, but if this is gonna be a problem that might not be fixed for a while, I will have to switch back to PcLinuxOs because plugging in isn't always an option...

Hopefully it get's fixed soon...:popcorn:

---

### Post by lordiaco on 2009-03-12
> **lofgren said:**
> Hi people,

[B]wondering if anyone has had the same issues as me..?
[/B]
After a bit of mucking around (admittedly ages ago) I got the wireless card working on my D600 - it works great!

Until... I unplug the power lead and run off batteries.
**I will be in the middle of active browsing and find wireless has disconnected.**

Last night after repeated ***ifdown eth1/ifup eth1*** commands (this seems to fix it temporarily) I also experienced freezing.

The laptop wouldn't respond to anything but powering off and back on.

I suspected power saving, but couldn't find any settings or anything obvious in the system logs.

It is fine in Windows on the same machine.

cheers,
Matt
My advice, my man:
Have same Latitude and have tested all existing Ubuntu and other Linux dists in many years and never get "every thing" into the Dell to work....until i picked up a newest XP Pro pack 3 again, loaded down origin but newest Dell drivers and...it is only then all completely works as its meant and made to do! Just bought an ESET Smart Secutity för 50-60 $
Dell is a PC/Intel machine at the end, isn't?

Have a nice day

---

### Post by lordiaco on 2009-03-12
> **hooksie007 said:**
> I also have a D600 that acts the same.  I switched from PcLinuxOs MiniMe which had no problems to UBUNTU 8.10, then I tried UBUNTU 8.04, and the same thing.  I like UBUNTU better, but if this is gonna be a problem that might not be fixed for a while, I will have to switch back to PcLinuxOs because plugging in isn't always an option...

Hopefully it get's fixed soon...:popcorn:
My advice, to all my Dell D600's :
Have same Latitude and have tested all existing Ubuntu and other Linux dists in many years and never get "every thing" into the Dell to work....until i picked up a newest XP Pro pack 3 again, loaded down origin but newest Dell drivers and...it is only then all completely works as its meant and made to do! Just bought an ESET Smart Secutity för 50-60 $
Dell is a PC/Intel machine at the end, isn't?

Have a nice day

---

