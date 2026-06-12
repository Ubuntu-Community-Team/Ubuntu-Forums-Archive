---
title: "upgraded to jaunty, black screen after booting"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by TPC on 2009-05-04
Hello.

I run ubuntu on my grandparents computer (they start xubuntu mostly, but kubuntu-desktop is installed as well). Earlier today I upgraded it to jaunty for them, the upgrade went fine. Since I don't have physical access to the box myself I did it trought ssh by editing sources.list manually and running aptitude -t jaunty dist-upgrade.

After the upgrade completed I called my grandfather and rebooted the box while he was sitting in front of it. He said that the boot progress bar showed up, but after that the monitor turned blank. The monitor went into power saving mode because there was no signal to it. I figured that it was a video mode problem, so I checked his xorg.conf and the xorg log file trought ssh, but everything seemed fine.

I then asked him to switch to a virtual console by pressing ctrl+alt+f1, but nothing happened. I tried other random things like restarting kdm, but he saw no reaction on the screen. When I rebooted the screen a second time he did not mention seeing the shutdown progress bar, I didn't specifically ask him about it, but he mentioned every little detail he saw so I think he would have mentioned that too if he saw it, so I don't think he could see that either. But when the box came back up again after the second reboot he did see the start progress bar, until the same thing happened again, the monitor turned on power saving mode.

I'm at a loss as to what to try next. Any suggestions?

---

### Post by soulmatic09 on 2009-05-04
this is happening to me too.

anyone seen a solution?

---

### Post by soulmatic09 on 2009-05-04
hey, i figured this out on my computer:

[http://ubuntuforums.org/showpost.php?p=7213863&postcount=2](http://ubuntuforums.org/showpost.php?p=7213863&postcount=2)

basically, i went into recovery mode at startup, and recovered everyting i could think of (disk check, reset the video card drivers, etc.) after that it worked.

---

### Post by TPC on 2009-05-05
The fix soulmatic0915243 suggested didn't work here.

This in the process list is probably a major clue:
15164 ?        Ss     0:00 /usr/bin/kdm
15242 ?        S      0:00 xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X -br -once -config /etc/X11/xorg.conf.failsafe -
15243 ?        Z<s    0:00 [Xorg] <defunct>

Defunct Xorg is strange. And why would it start the failsafe mode when xorg log isn't giving any errors for the normal mode in the log?

I'm still not sure what I can do next.

---

### Post by TPC on 2009-05-05
I may have solved the problem, when I tried running /usr/bin/X manually to see if it gave any errors not in the log it gave me an unresolved symbols in /usr/lib/xorg/modules/extensions/libdri.so. According to packages.ubuntu.com this file can be provided by either xserver-xorg-core and xorg-driver-fglrx. Since the computer doesn't use the fglrx driver I simply uninstalled xorg-driver-fglrx. Now things look much better in the process list, X started normally, without being defunct or trying to go to failsafe.

The person who owns the computer is not home at the moment, so I can't confirm visually that the problem is fixed yet. I will report back once I've gotten confirmation that the problem is fixed, in case it will be useful to someone else in the future who has the same problem and finds this thread when searching.

---

### Post by soulmatic09 on 2009-05-05
yes, my system is acting up again. if you find something let me know.

---

### Post by soulmatic09 on 2009-05-05
i've got a hunch the problem may be kdm. i'm going to switch to gdm and see what happens.

edit:

no joy. the problem happens in gdm too:

[https://bugs.launchpad.net/ubuntu/+bug/369760](https://bugs.launchpad.net/ubuntu/+bug/369760)

---

### Post by soulmatic09 on 2009-05-06
hmm, it seems to be working fine after switching to gdm after all.

---

### Post by skippuff54 on 2009-05-17
What video cards do your machines have in them? I experience the issue on a Dell Dimension 2400 with a Radeon 300 [ATI] video card, which would follow due to Jaunty's lack of support for ATI.

I do get the splash screen. My login settings skip the login window, so once the splash screen clears it should display the desktop.

The screen goes blank. I use S-video output to my TV.

Network services are up.

---

