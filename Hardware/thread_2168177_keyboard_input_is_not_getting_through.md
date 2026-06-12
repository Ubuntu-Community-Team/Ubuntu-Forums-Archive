---
title: "keyboard input is not getting through"
date: 2013-08-16
forum: Hardware
---

### Post by ralmond on 2013-08-16
I'm currently having a very odd problem with keyboard input on my ZaRason Stratos 7330 laptop (Running Ubuntu 13.04).  The problem started as an intermittent problem, when I was running Ubuntu 12.04.  I would occasionally have problems when my external keyboard (an old keyboard rescued from a long dead Sun workstation) would stop generating input.  Unplugging and replugging it in would often solve the problem.  It then started spreading to the built-in laptop keyboard as well.  Here a reboot would usually solve the problem.  I tried upgrading to 13.04, hoping that there would be fix in the later version.  I'm now having the problem steadily.  The problem is not application specific, any application that accepts keystrokes does nothing.


Some details about the problem:
1) It is only the keyboard.  Both the external and built-in keyboard are affected.  The external mouse (same hub as the keyboard works fine).
2) The problem seems to be restricted to one user account:  The keyboard works find to enter my password on login.  I have a secondary account that seems to work fine (but does not have all of my files and stuff).  I can also ssh into the computer on the first account.
3) The computer seems to be generating errors related to gnome-user-share (I can't send these in as aport requires me to type a password :().  I tried reinstalling gnome-user-share, obex and related stuff as well as turning off bluetooth support, but the problem persists.
4) Here is a list of processes that are running when I log into the account that is not working that are not in the account that is working:
ralmond   2876  0.0  0.0  52844  3640 ?        SN   14:46   0:00 /usr/bin/desktopnova-daemon
ralmond   3001  0.7  0.0 135160 15960 ?        Sl   14:46   0:01 /usr/lib/gvfs/gvfsd-metadata
ralmond   3131  0.0  0.0 425448  9844 ?        Sl   14:46   0:00 /usr/lib/gnome-user-share/gnome-user-share
ralmond   3138  0.0  0.0  56356  2588 ?        S    14:46   0:00 /usr/bin/obex-data-server --no-daemon
ralmond   3186  0.3  0.2 562888 45096 ?        Sl   14:46   0:00 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
ralmond   3361  0.0  0.0 367396  4008 ?        Sl   14:48   0:00 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor

5) I also tried reinstalling ubuntuone and deleting various preference files, but the problem persists.

I'm getting really frustrated.  Any suggestions for troubleshooting steps would be welcome.

---

