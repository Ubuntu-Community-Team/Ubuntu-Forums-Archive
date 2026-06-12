---
title: "touchscreen"
date: 2010-02-04
forum: Hardware
---

### Post by marquart on 2010-02-04
Hi there

Im t'trying to set up a touch screen with calibrate_touchscreen from ubuntu software center

it work - BUT the x-axis is inverted so the middle of the screen is ok up/down is ok but left-right is inverted

from the ter minal I get this:

Creating FIFO...
Starting calibration program...



X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux nikolaj-eee 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=5679664e-2b95-49de-9403-8a66b2716720 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.0.log", Time: Thu Feb  4 21:38:05 2010
(==) Using default built-in configuration (39 lines)
(EE) Failed to load module "i810" (module does not exist, 0)
Setting master 
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
State: S_UNTOUCHED	Action: No Action		Button: 0
State: S_TOUCHED	Action: No Action		Button: 0
State: S_LONGTOUCHED	Action: click		Button: 3
State: S_MOVING	Action: No Action		Button: 0
State: S_MAYBETAPPED	Action: click		Button: 1
State: S_ONEANDAHALFTAP	Action: down		Button: 3
min = (212/191)    max =(1961/1874)

(X0/Y0) = (800, 598)		
=> dx0 = -795 / dy0 = -593
(X1/Y1) = (394, 590)		
=> dx1 = 6 / dy1 = -585
(X2/Y2) = (3, 585)		
=> dx2 = 792 / dy2 = -580
(X3/Y3) = (795, 277)		
=> dx3 = -790 / dy3 = 23
(X4/Y4) = (398, 295)		
=> dx4 = 2 / dy4 = 5
(X5/Y5) = (5, 282)		
=> dx5 = 790 / dy5 = 18
(X6/Y6) = (795, 0)		
=> dx6 = -790 / dy6 = 595
(X7/Y7) = (400, 2)		
=> dx7 = 0 / dy7 = 593
(X8/Y8) = (6, 0)		
=> dx8 = 789 / dy8 = 595

waiting for X server to shut down Dropping master 
 ddxSigGiveUp: Closing log


the min = (212/191)    max =(1961/1874) seems correct 

Max = top left

min = buttom right

if i move around the screen doing calibration - the X/Y seems correct.

Does anybody know how to do this manualy+

Regards n thanks in advance
Nikolaj

---

