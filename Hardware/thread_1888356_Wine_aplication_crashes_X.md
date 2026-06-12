---
title: "Wine aplication crashes X?"
date: 2011-11-29
forum: Hardware
---

### Post by Jail on 2011-11-29
Game started in wine: Drakensang - The Dark Eye is able to crash my display. Display goes black and I can't switch to console. I can only restart system with 'Alt'+'SysRq'+“REISUB”.
My system is Ubuntu 11.10 64bit Acer Aspire 7750G with AMD Radeon HD 6850M.
Drivers Catalyst 11.11 manually installed. I also tried official drivers from repository but it didn't solve the problem.
I verified notebook memory with mem test and it is OK.
```
$ lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc Broadway [ATI Mobility Radeon HD 6800 Series]
```
X-org log till crash:
```
X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux jaroslaw-Aspire-7750G 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.0.0-13-generic root=/dev/sda1 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
Build Date: 19 October 2011  05:21:26AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.22.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 20:03:45 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```
I installed Windows 7 to verify if my hardware is Ok. In Windows Drakensang also crashed resulting in BSOD but all other applications run without any problems. So it seams that the game is buggy, however none wine application should crash X.
**I need help to find out if it is a bug or hardware problem.**
Any clues appreciated.

---

### Post by Jail on 2011-12-03
**bump**

---

### Post by Jail on 2011-12-09
**bump** again

---

### Post by foresthill on 2011-12-10
Same problem trying to run Quake 3 Arena in 11.10 using Wine on Intel 4500 MHD graphics. I have tried running different versions of Wine as well as uninstalling and reinstalling the game. No dice.

I might attempt to run the game natively in Linux to see if I can isolate the problem.

This just one of many reasons I'm sticking with 10.10 for now, where the game runs perfectly in Wine.

---

### Post by Mark Phelps on 2011-12-12
You answered your own question:

> In Windows Drakensang also crashed resulting in BSOD but all other applications run without any problems. So it seams that the game is buggy, however none wine application should crash X.

Any application that is "buggy" has the ability to crash ANYTHING, including the X-server, or the OS.

If it fails BOTH in Windows and in Linux, there is little likelyhood that it can be solved in Linux.

---

### Post by Jail on 2013-05-06
After a long struggle I found that the problem is in AMD Catalyst driver. With open source drivers there are no problems except for poor performance, 50 % less comparing to fglrx. At least it works. Despite filling bug report for AMD drivers I really doubt that it will be ever fixed.

---

