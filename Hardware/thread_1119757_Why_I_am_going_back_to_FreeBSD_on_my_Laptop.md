---
title: "Why I am going back to FreeBSD on my Laptop"
date: 2009-04-08
forum: Hardware
---

### Post by lparsons42 on 2009-04-08
My ThinkPad R32 has been dual booting WinXP and Kubuntu 8.10 for a few months now.  I previously dual booted WinXP and FreeBSD, but as people know the support for wine and flash in freebsd are both rather awful, so I decided to try Kubuntu.
However, I encountered several problems in Kubuntu that apparently are issues that will not be addressed, but have worked fine for some time in FreeBSD:
First, wireless networking.  I don't understand why this has to be so complicated in Kubunutu.  I leave my home wireless "open" because we have no neighbors close enough to access our network.  However, Kubuntu refuses to ask for a DHCP address on boot, I have to invoke dhclient manually every time.  This has never been an issue in FreeBSD, it will happily grab an open wireless network and connect at will.  Secured wireless networks are just as bad.
Second, network printing.  I have an older parallel printer at home that connects to my network through a wireless print server.  Connecting to this in FreeBSD (via cups) was a cake-walk.  Doing the same in Kubuntu (also via cups) was a major chore.  
Third, connecting to external monitors or projectors.  This is the straw that breaks my camel's back.  If I boot my system in Kubuntu and then connect a projector or external monitor, I get a message that I have connected to another display, and I can set it up but it never works.  I can configure it, but when I click apply settings, it drops the configuration of the new display and never uses it.  And if I attempt to boot while connected to an external display, life is even worse; my system will never boot to a usable state!  I very shamefully had to deliver a presentation from Windows XP this week - the first time in at least 5 years that I had to use Windows to give a presentation.
I don't see how none of these problems are considered worthy of addressing.  Especially as none of them have been problems in FreeBSD for several years.

---

