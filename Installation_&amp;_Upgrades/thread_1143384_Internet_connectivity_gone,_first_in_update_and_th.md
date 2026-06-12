---
title: "Internet connectivity gone, first in update and then in retro."
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by chonacky on 2009-04-29
I want to re-establish Internet connectivity between Ubuntu (any version 8.04 -> 9.04) and the wireless connection of my host operating system (OSX 10.5.4). Up until a week ago, I was productively using Ubuntu 8.10 with the Geany IDE for application development. In attempting the upgrade from 8.10 to 9.04 I encountered some errors that made Ubuntu inoperable - I couldn't even get to the log-in screen. I decided to "retreat," installing a previous version of Ubuntu and right now am just trying to get back in the business of writing code under any version of Ubuntu that I can install, and that works. unfortunately, as I have gone back and done fresh installs, I can no longer get connectivity to the Internet with either 8.04 or 8.10.

I have an Intel Macintosh and am running OSX together with Parallels. In this situation, Parallels runs as an application under OSX, which can then act as host for other operating systems - in this case Ubuntu. I had installed Ubuntu 8.04 a year ago when I was a complete Linux neophyte. Nevertheless, in that process I was able to seamlessly install Ubuntu and establish Internet connectivity. Now I find that I cannot re-establish this operating state. The problem is with getting Internet connectivity.

I would like to know whether Internet connectivity is a problem for others. But I would be especially grateful if someone else is operating in the same hardware/software environment that I am, and can tell me how she/he has fared.

Below I indicate what I have done most recently, using an installation of Ubuntu 8.04, in order to reestablish some capability to resume my coding work.

Cheers -- NJC
---------------------------------------------------------------
Upon the advice of persons who know much more about Parallels and Ubuntu than I do, I have configured the Ubuntu Networking Settings in the Connections pane:
    Wired connection (yes)
    eth0 Properties:
        Configuration:     Static IP address
        IP address:        10.0.1.4 (n.b. this is the local address assigned to this computer by my (Airport) router.)
        Subnet mask:    255.0.0.0
        Gateway addr:    10.0.1.1 (n.b. this is the local address assumed by my router for itself on my office intranet.)

    I went to the Parallels Networking Configuration and set the Network Adapter 1 parameters to:
    Enabled (yes) and Connected (yes)
    Shared Networking (yes)
    The MAC address was set by the system to: 00:1C:42:24:95:B2, and I just left it alone.

But all to now avail ... my Browser still comes up dry when trying to reach the net.

---

