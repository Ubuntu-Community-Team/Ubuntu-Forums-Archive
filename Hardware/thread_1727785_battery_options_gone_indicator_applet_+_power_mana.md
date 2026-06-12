---
title: "battery options gone indicator applet + power manager"
date: 2011-04-12
forum: Hardware
---

### Post by averyisle on 2011-04-12
the battery indicator has disappeared out of my system indicator applet leaving a blank space in its absence...
going to system>preferences>power management displays only "on ac power" and "general" with the "on battery power" tab missing.

this has happened in the past, but a restart would restore it.  when it happened most recently however, it did not. This last time my computer did a hard shut down when the battery ran out while running the power manager inhibit applet (oops!) (side note: it would be really nice if this did not remove notifications that the battery was low and instead just inhibited the screen saver, idle dim, etc like caffeine.  It even disabled the led warning on my laptop(!) which i didn't realize went through the os at all)

i tried refreshing the panel via 'killall gnome-panel' -nothing
...removing and readding the indicator applet -nothing
...restarting the computer -nothing

the computer still slightly dims the display when i remove ac power like it was set to before, but i have no other evidence of the computer understanding the battery is there (though my led power display is back).

another side note: my bluetooth display is also missing from the same applet.  Both the battery and the bluetooth were set to always display icons.
I have also lost the options to suspend and hibernate (only restart and shutdown listed) my session via system>shut down which is big pain #3! 

I apologize if this has been answered somewhere, I have scoured the forums and come up with a fist full of unresolved threads that hinted at similar issues. 

thanks

---

### Post by averyisle on 2011-04-13
huh, i wish that i could say more to be helpful, but my battery indicator is back, as is suspend and hibernate after another soft shutdown and reboot (though interestingly my computer saw fit to check the hard disks as if i'd done a hard shutdown).  This difference (and fix) may be because i uninstalled then reinstalled power management via the ubuntu software center prior to the reboot.

bluetooth icon is still gone, but i can live with that.

i hope this helps anyone facing the same issue!

---

### Post by averyisle on 2011-04-16
i suspended my session and everything was fine.  it sprang back up and everything seemed dandy, but after using it for awhile i noticed that the onboard led was blinking to tell me that my battery was low and my battery in the indicator tray was telling me that i had 2 hours left.  I wasn't sure what was causing this, but i tried "killall gnome-panel" and it continued to report that i had 2 hours left.  I plugged it in and the icon did not change to indicate that it was receiving a charge (though my led's did) so i restarted it.  After rebooting, my battery indicator was gone as was my ability to suspend/hibernate.

This is becoming a very obnoxious issue and i would appreciate some voices other than my own in here!

---

### Post by lukeanders70 on 2011-05-02
I have found two other problems in the forum Identical to  this (one of them being my own) but have found no answer. My battery icon stopped working when I upgraded Ubuntu versions it now works off and on like yours appearing every 10 boots or so. If you find a fix please be sure to post it.

here are the links to the other two Threads 

[http://ubuntuforums.org/showthread.php?t=1744766](http://ubuntuforums.org/showthread.php?t=1744766)

[http://ubuntuforums.org/showthread.php?t=1741033](http://ubuntuforums.org/showthread.php?t=1741033)

---

