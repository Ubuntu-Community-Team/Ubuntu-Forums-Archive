---
title: "Unable to use nvidia-current driver"
date: 2011-03-27
forum: Hardware
---

### Post by Novemberox on 2011-03-27
Hi,

I've got problem with nvidia driver. After two restarts of my laptop it fails to start. Standard message error
```


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux mikoos-N-A 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-28-generic root=UUID=3f392d16-f19f-4254-8d22-be3c6b032ce4 ro quiet splash
Build Date: 09 January 2011  12:14:27PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 27 23:32:09 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
```

What is wrong? I tried to switch into nvidia-current in xorg.conf, but without success. 

I've got nvidia geforece 8600 for laptops. I installed Ubuntu yesterday, updated to new kernel and then installed from "Additionals Drivers" nvidia-current driver. As I said it work for some time, meanwhile, I've installed few programs like eclipse, gimp and so ons, nothing kinky. I've trying system few times before and always had this problem.

Any help would be appreciated.

---

### Post by Novemberox on 2011-03-29
This is ridiculous, unable to use graphic card, I feel as if it was 10years ago when that could be a problem. But now... wt? Even this crapy nvadasth isn't doing it's job. All I wonder is having nice resolution.

I removed all nvidla-glx and nvidia-nv* packets. Then installed drivers from nvidia page and it worked, till next reboot...

No one ever had problem on brand new ubuntu 10.10 with standard nvidia drivers on card like nvidia 8600? Why isn't it working out of the box?

I'm 64bit user, switch to 32bit could save me? Or it's not relevant?

---

