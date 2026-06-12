---
title: "Ethernet bugs / freeze when unplugging ethernet + AC"
date: 2010-05-12
forum: Hardware
---

### Post by W. Irving on 2010-05-12
After upgrading 9.10 to 10.4 my HP 5310m now freezes hard when disconnecting both AC power and the ethernet cable (in any order)! The screen stops updating, switching to a TTY doesn't work, and magic sysrq is ineffective. Only holding down the power button kills it.

Killing gdm and doing the unplugging while viewing a TTY results in the insanity picture in the attached photo to roll by perpetually. Nothing ever makes it into syslog. Kernel panic?

Other nasty network related issues have appeared since upgrading to Lucid.

[LIST]
[*]eth0 not detected at boot unless ethernet cable is connected
The switch in the other end confirms the cable is plugged into the laptop.
[*]no wired network connections shown in System->Preferences->Network Connections
This in spite of ifconfig reporting eth0 has an IP address and having a VNC session open! My interfaces file didn't have an entry for eth0, I added it, but it made no difference.
[*]network connections panel icon gone missing
It used to be there, up until about an hour ago.
[/LIST]

Very appreciative of any help I can get with these quite serious problems! :(

---

