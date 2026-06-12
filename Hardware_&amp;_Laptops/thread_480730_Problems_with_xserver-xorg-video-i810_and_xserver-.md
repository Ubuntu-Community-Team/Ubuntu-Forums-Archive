---
title: "Problems with xserver-xorg-video-i810 and xserver-xorg-video-intel packages"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by VirtualCLD on 2007-06-21
I understand that xserver-xorg-video-intel is not an official Ubuntu package, but I'm having problems with the xserver-xorg-video-i810 drivers (or at least I think I am).  I'm not sure which issue to address first, so I decided let's see if I can get the xserver running with xserver-xorg-video-intel.

I'm running Kubuntu Fiesty and Ubuntu Edgy on some Dell GX280 workstations with the Intel integrated graphics card 900GM.  The problem started when a commercial program would not display on these machines and the program segfaults (I say display because it doesn't matter if I use the machines to remotely log onto a server where this program is installed or if I install the program locally, it segfaults either way).  Interestingly enough, my Fiesty Kubuntu machine at home with an ATI card can works fine.  The workstations can also display this program (remotely, haven't tested locally since it would require a reformat) with a live CD of Dapper (but the live CDs of Edgy and Fiesty do not work), they work with other distros of Linux (Fedora Core), and they even work with (dare I say it) X-Win32.  I'm not sure if it's specific to Edgy and Fiesty or if the xserver-xorg-video-i810 driver changed from Dapper to Edgy because as I said, the program runs/displays with the -i810 driver in Dapper, but not in Edgy and Fiesty.

So I decided to try a different driver and see if that works, but every time I try to install the xserver-xorg-video-intel package and change the line in my xorg.conf from "i810" to "intel", the xserver doesn't start.  Well, to be specific, I can get to the login splash screen, but it fails to login, it just brings me back to the login screen.  Oh yes, I've tried sudo dpkg-reconfigure -phigh xserver-xorg and that doesn't work either.

I guess my question is to fold, one, am I doing anything wrong with the xserver-xorg-video-intel package?
Two, am I barking up the wrong tree with trying to hunt down this problem?  All I know is that this program fails to display with these Dell GX280 with K/Ubuntu Edgy and newer.  Older versions and other distros work, and different computers with different hardware work with the newer versions.  If I am barking up the wrong tree, maybe I should start a seperate thread about this specific problem.  One other note, does K/Ubuntu use a generic driver when you login to Failsafe mode?  I ask, because the program still fails in Failsafe mode, but is it using the i810 drivers?


EDIT:  Update #1:
Ok, so I never found out why I can't get the intel drivers to run instead of the i810 drivers, but I found the solution to my original problem which made try to update my drivers.  I was working with a commercial product called Cadence IC6.10.  While they officially support only RedHat Enterprise 3.0 (RHEL 3.0), I was trying to ssh in (with X forwarding) and run it remotely from Kubuntu/Ubuntu Dell GX280 machines.  I also tried installing and running it locally and I got the same error message as running it remotely:
A bunch of:
```
Qt Warning: X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 2 (X_ChangeWindowAttributes)
  Resource id:  0x2e00011
```
followed by a bunch of:
```
Display :0.0 Error "BadWindow (invalid Window parameter)"
\e  request 18 error 3 serial 1392
``` errors.

I found out that disabling composite extensions (which are enabled by default starting with Edgy and later), fixed the problem by modifying my xorg.conf file and adding these lines:
```
Section "Extensions"
        Option "Composite"      "Disable"
EndSection
```
The reason why this worked on the computer with the ATI drivers?  Apparently the deb package I installed with apt added these lines to the xorg.conf file.  I guess I should have known to disable this extension anyway, but I never ran into a problem until now.

---

