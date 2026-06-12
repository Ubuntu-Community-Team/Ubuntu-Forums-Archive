---
title: "sl-modem-daemon problems"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by Jimmy Riddle on 2006-05-01
The sl-modem-daemon package i down loaded from the miscellaneous > mutiverse repos has been causing me quite afew problems. the package contains three items namely :-

slmodemd - a daemon to provide higher level comm functions for linmodems (installed to
 user/sbin)

sl-modem-daemon - a script to activate slmodemd (installed to /etc/init.d)

sl-modem-daemon - a config file in which the user can enter options read by the sl-modem-script. Although the script and the config file have the same name they are installed in different directories. (installed to /etc/default)

The problem is entirely with the script, the config allows the user to specify which low level driver the slmodemd daemon should use for communicating with the kernel in this case either one of three alsa drivers (snd-atiixp-modem,snd-via82xx-modem,snd_intel8x0m) or slamr & slusb the later two being commercial drivers provided by the smartlink corp. Which driver is applicable is determind by the chipset of the modem. The options which the user enters in the config file are :-

slamr0 - for the slamr driver
slusb0 - for the slusb driver
auto   - to load any one of the three alsa drivers.

The problem occurs when the last option is used in every instance i have used this option it has destroyed the root file system and made the system inoperable not immediatly but on rebooting the computer.On reboot #fsck attempts to run but fails and returns the system to a root prompt with the message to run #fsck without options, this also fails and then gives a recommendation that #e2fsck should be run accepting this destroys the grub config files amongst others i suppose making the computer totaly unbootable.
I am a new user to Linux and Ubuntu should i report this as a bug? i am unsure what to do as this is from the unsupported multiverse repo.
cheers Jimmy

---

