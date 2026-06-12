---
title: "Blank screen before desktop loads"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by fishwebby on 2009-04-26
Hello,

I've just upgraded Xubuntu 8.10 to 9.04 without any problems, except that now after logging in, it shows a blank light blue screen for 15 seconds or so before starting to load the desktop. Not a massive problem, but just wondering if there's some way to find out what it's doing.

Not sure if it's related, but sometimes when I boot the computer it goes through the boot process, and at the point where it should show the login screen it just goes black. Sometimes ctrl-alt-f1, f2 etc. work and I can login to a console but ctrl-alt-f7 (which sometimes worked) no longer gives me the graphical login screen. Other times these buttons don't work at all (nothing does) so I have to use the power switch to switch it off (which from the sounds of it my hd doesn't like). Does anyone have any ideas how I could start to diagnose what might be going on?

Any help is greatly appreciated.

Cheers
Dave

---

### Post by shogunami on 2009-04-26
I also get the black screen, except I get it EVERY boot, the regular Ubuntu version, Upgraded from 8.10 as well as a fresh reinstall. Cant even use Ubuntu at all.. :(

Help ?

---

### Post by jasontango on 2009-04-26
Upgrading from 8.10 to 9.04 I had the same problem as shogunami.  I would see the xubuntu progress bar during boot (and could switch to console output via Ctrl-Alt-F1), but then instead of the login screen, the screen would flash and blank a few times before seeming to hang.  I could not switch consoles, and couldn't even Ctrl-Alt-Del.

I assumed there was some kind of xserver problem and booted into recovery mode.  I tried some of the options to no avail, then dropped into the root console and started poking around.  After a few fruitless cycles of rebooting and tinkering with my /etc/X11/xorg.conf files, I found the following in /var/log/gdm/:0.log.1

```
2546 2514
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X 
:0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt8 -br -once -config /etc/X11/xorg
.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux JasonLaptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Sun Apr 26 19:09:08 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libdri.so: undefined symbol: atiddxAbiDixLookupPrivate
2546 2514
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```I googled for the "symbol lookup error" and that brought me to this page: 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/345669](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/345669)

I tried the following advice (and agree it's not a long-term solution)
> 
I solved this problem for me by temporary removing libdri.so file - X server reported errors(Failed to load module "dri" (module does not exist, 0)) but it is bad solution, i think

I renamed /usr/lib/xorg/modules/extensions/libdri.so to libdri.so.xxx and then ran "/etc/init.d/gdm start".  It allowed me to finally be able to run X and reach gdm's graphical login prompt, but keyboard still didn't respond.  After a full reboot, I was able to login properly.  I still have to do some tinkering to restore my proper display resolution, but it beats a blank screen!

I'm running an emachines E520 laptop, with a 15.4in display and Intel(r)Cantiga Graphics Controller.

I hope that helps.

---

### Post by jasontango on 2009-04-26
A solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/283836/comments/15](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/283836/comments/15)

I followed the instructions to remove/purge and reinstall, and was able to reboot into the graphical login successfully.  The installed package will restore the file /usr/lib/xorg/modules/extensions/libdri.so, and that seems just fine.

---

### Post by fishwebby on 2009-04-27
Hi,

I couldn't find anything that related to what you guys mention in the logfiles, but now I know where to look :-) this is the contents of one of the files where it failed (":0.log.2"):

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux noddy-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 27 16:57:12 2009
(==) Using config file: "/etc/X11/xorg.conf"
WARNING: All config files need .conf: /etc/modprobe.d/sl-modem-daemon.modutils, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
get fences failed: -1
param: 6, val: 0
get fences failed: -1
param: 6, val: 0
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Fatal server error:
Failure to wait for IRQ: Device or resource busy


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


FatalError re-entered, aborting
Failure to wait for IRQ: Device or resource busy
```

From what I can tell from Googling these errors, it looks like it might be a problem with the Intel graphics driver... how to fix it though is another matter - anyone any ideas?

Cheers
Dave

---

### Post by shogunami on 2009-04-29
I have tried many things now, many "solutions", some have worked temporarily, and then fails when I reboot, or some that works but the graphics is very limited. I feel that for once Ubuntu has failed me, and it's not a pleasant feeling. Like, how does it actually feel when Windows Vista is more stable and works better than Ubuntu? :S

I hate Vista, but I HAVE to use it to get things done.

I'll just stand by for a while, or try another distribution =/

Thanks for the many answers and suggestions.

---

