---
title: "Fluxbox Problems on upgrade?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Flotter on 2009-04-28
I upgraded from intrepid to jaunty on two machines here, an IBM Thinkpad T22 and a homebrew workstation.  The Thinkpad upgrade went flawlessly.  I'm having problems logging into Fluxbox though.

Here is my .xsession-errors file:

Xsession: X session started for jamstar7 at Tue Apr 28 16:34:43 MST 2009
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/kubuntu-default-settings/kubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
wmnet: using devstats driver to monitor eth0
Failed to read: session.screen0.maxIgnoreIncrement
Setting default value
Failed to read: session.screen0.maxDisableMove
Setting default value
Failed to read: session.screen0.maxDisableResize
Setting default value
Failed to read: session.screen0.noFocusWhileTypingDelay
Setting default value
Failed to read: session.screen0.tooltipDelay
Setting default value
Failed to read: session.screen0.clientMenu.usePixmap
Setting default value
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 128 requests (48 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1456 requests (142 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 321 requests (240 known processed) with 0 events remaining.
No protocol specified
bt::Display: failed to open display ''


Fluxbox works perfectly on the Thinkpad.  What can I do to fix it on the desktop?

---

### Post by Anzan on 2009-05-01
Ask at [email]fluxbox@googlegroups.com[/email]

---

