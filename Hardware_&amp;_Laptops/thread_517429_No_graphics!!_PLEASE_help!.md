---
title: "No graphics!! PLEASE help!"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by Tranks on 2007-08-04
Hi guys,
I have tried to do some things (like an idiot) about the Xorg, i don't know what it was, just copied and paste like an idiot to the Console.

Anyways, I have no graphics at all now. When i start my computer, it starts an error that says:

> Failed to start the X server (your graphical interface). Is is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Than i click on "Yes", then it writes:

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol System 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Correct Operating System: Linux holder-laptop 2.6.20-16-generic #2 SMP
Build Date: 04 April 2007
                Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
                to make sure that you have to latest version.
Module Loader present
Markers: (--) probed,  (**) from config file,  (==) default setting,  (++) from command line,  (!!) notice,  (II) informational, (WW) warning,  (EE) error,  (NI) not implemented,  (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  4 21:26:07 2007
(==) Using config file: "/etc/X11/xorg.conf"

Then i press "OK", Then this appears:

> Would you like to view the detailed X server output as well?

Then "Yes", Then:

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol System 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Correct Operating System: Linux holder-laptop 2.6.20-16-generic #2 SMP
Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
                Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
                to make sure that you have to latest version.
Module Loader present
Markers: (--) probed,  (**) from config file,  (==) default setting,  (++) from command line,  (!!) notice,  (II) informational, (WW) warning,  (EE) error,  (NI) not implemented,  (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  4 21:26:07 2007
(==) Using config file: "/etc/X11/xorg.conf"

Then this box appears:

> The X server is now disabled. Restart GDM when it is configured correctly.

I don't know what to do but i have no computer now exept for my mom's sucks windows computer.

Thank you verry much,
~Tranks.

---

### Post by taurus on 2007-08-04
You need to reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by pbcartwright on 2007-08-04
upi should have an option to start in gdm safe mode..
You have basically screwed up your graphics settings, did you make a backup of those files befoer you played with them??
once you are logged into the command line moed, you can try sax2 , the graphics configuration program. this might allow you to configure things correctly.
or just reinstall it.

---

### Post by Tranks on 2007-08-04
Thank you guys, My computer is running normally or even faster. Real thanks =]

~Tranks.

---

