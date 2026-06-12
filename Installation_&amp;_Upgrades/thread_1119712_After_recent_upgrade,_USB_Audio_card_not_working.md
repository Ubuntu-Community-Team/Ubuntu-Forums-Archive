---
title: "After recent upgrade, USB Audio card not working"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Rossi9x87 on 2009-04-08
So I ran the recent upgrade (the one from about 36 hours ago) and rebooted. now my external usb sound card is listed as "not connected."  its not detected by the OS, as my internal card is the only one being listed as detected.  However, the mute button on the side of the card still mutes the onboard audio, just like if it was connected,

any recos? Ive reinstalled alsa and anything else related that i could think of that might cause this issue.

If there was a kernel update in the last series of updates, can I revert to the old kernel?

-----------------------
EDIT
-----------------------
Reason:  SOLVED
-----------------------

used the automatic ALSA updater script available on the forums instead of the apt-get terminal code.
All audio back to normal.

Sorry for wasting the space on the forums!

---

### Post by prunch1910 on 2009-04-29
I had the same problem, but it just took a little longer to fix, I had to uninstall alsa, reinstall it and then run the update script. My sound worked fine after that.

---

