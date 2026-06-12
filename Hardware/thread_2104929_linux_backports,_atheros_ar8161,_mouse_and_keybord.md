---
title: "linux backports, atheros ar8161, mouse and keybord.."
date: 2013-01-14
forum: Hardware
---

### Post by darkup on 2013-01-14
Hi all!

Premise:
they gave me a new pc with i5 processors 64-bit, with its "beautiful" windows 7 64bit installed and UEFI boot and obviously the first thing I do is groped to install ubuntu; I choose the 64-bit version but I messed up with the grub, then format it all, I partitioned as I want, I'll put a win7 and then the ubuntu 12.10 64-bit, first problem: the network card Atheros AR8161 works only installing linux-backports-modules-cw-3.6; then I mount version 3.5.0-22-generic and reboot: keyboard and mouse die... However, the network card is working!
To get back the control I have to restart using kernel version 3.5.0-17 (and not 22 which is the last, while both -18 -19 that do not work as much) but no network .. I worked around between software-center and synaptic package manager and then inexplicably  everything work! Well!

Premise 2:  I need virtualbox to run some programs with XP, so I install the latest 64-bit version, start the virtual disk but it crashed and It often also reboot ubuntu: useless.

Current status: I realize that  ubuntu 64 bit and virtualbox 64 bit do not get along and it seems I'm right, since replacing both with their 32-bit versions all is finally well ... except that ... I have to solve again the question of the network card!

I tried again to play around with the backports to get the network card work but I didn't manage :(

I currently have installed:
linux 3.5.0.21.27
linux-headers-lbm-3.5.0-21-generic
linux-backports-modules-cw-3.6-3.5.0-21-generic

keyboard and mouse do not work :confused:

Help please..

---

