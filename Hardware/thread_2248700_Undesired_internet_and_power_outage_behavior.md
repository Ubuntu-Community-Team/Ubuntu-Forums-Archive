---
title: "Undesired internet and power outage behavior"
date: 2014-10-16
forum: Hardware
---

### Post by AFriendlyNerd on 2014-10-16
A first world problem, to be sure!

My Ubuntu 14.04 works great, running on a budget ASUS laptop, thanks in part to the help I've gotten here! Its main purpose is running all kinds of media server applications.

There are two little issues I would like to get a handle on:

1) I've noticed that after an electrical power outage occurs in the home, and when power is restored, the machine will not automatically reconnect to the internet, even though it's connected by ethernet, and even though the laptop battery kept it running during the outage. I have to log in with my username and password first. Is there a fix or failsafe for this undesired result?

2) I have also noticed that I am sometimes connected wirelessly as well as wired, and while this presumably does no harm, I am under the impression it's best to just have one network connection. Why is this happening? I could swear that I uncheck "enable wireless networking". Does that re-enable itself somehow?

---

### Post by Vladlenin5000 on 2014-10-16
1. This is normal and should be expected. It depends mostly on the other elements of the network (router) that haven't emergency power supplies like the one provided by the laptop's battery. Just unplugging the Ethernet cable and plugging it again should be enough. Otherwise it would be interesting to know about your router and other devices in that network.

2. Yes, only one is preferable and it shouldn't be connecting to the WiFi if you disable it.

---

### Post by AFriendlyNerd on 2014-10-16
Thank you, fellow Hitch fan. RIP </3

I have a motorola comcast modem (the white non-wifi one you buy yourself) and an ASUS RT-AC68R.

Is there a way to get the Ubuntu machine to attempt to re-establish that connection on autopilot?

---

### Post by Vladlenin5000 on 2014-10-16
Perhaps a new firmware for the ASUS router is what it needs...

[http://www.asus.com/Networking/RTAC68R/HelpDesk_Download/](http://www.asus.com/Networking/RTAC68R/HelpDesk_Download/)

---

### Post by tgalati4 on 2014-10-16
Put the modem and router on an UPS.  When you lose power, the devices get reset and the order of reset is important.  The Network Address Tables (NATs) get recreated, and they will be incorrect if the router is booted before the cable modem.  The cable modem needs to be booted first--and it could take several minutes to get the DNS established.  Then boot the router so it gets the correct DNS from the cable modem.  Then your network should auto-negotiate.  If you have an UPS for these devices, they may stay up.  However a power distruption will probably disrupt your neighborhood switches, so you will probably lose service regardless.

---

