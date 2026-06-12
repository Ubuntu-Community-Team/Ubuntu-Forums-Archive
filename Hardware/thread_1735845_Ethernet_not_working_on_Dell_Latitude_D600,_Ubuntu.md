---
title: "Ethernet not working on Dell Latitude D600, Ubuntu 10.04"
date: 2011-04-21
forum: Hardware
---

### Post by ChaseMDuffin on 2011-04-21
Hey guys, so I just installed 10.04 on my Latitude D600, and neither the Ethernet nor the Wireless card are working. I did a "sudo lspci" in a command window and strangely enough, the Wireless card showed up but the Ethernet did not. I know the Ethernet card works because it was operational in Windows. Any suggestions are welcome.

---

### Post by LinXNut on 2011-04-21
I had the exact same problem (sort of) in my Dell Latitude D520. Just to be sure, check your BIOS settings at startup. That was the problem I had. The installation of Xubuntu on my laptop kind of changed it around.

---

### Post by shansen5 on 2011-05-24
I've been having a similar problem.  I installed Ubuntu 11.4, and the ethernet worked during installation.  The wireless didn't work and I read several posts about that and followed this guide for it:

After a few reboots, the wired networking stopped working, too.

I checked the BIOS settings and they look okay.

I reinstalled, using Kubuntu the second time.  I got the same results--no wireless and then a few reboots later, no wired.  

I see in /etc/network/interfaces that the eth0 line looks like it is commented out:
# The primary network interface
auto eth0
#iface eth0 inet dhcp

I wonder what did that?

nm-tool says:  State: disconnected

---

