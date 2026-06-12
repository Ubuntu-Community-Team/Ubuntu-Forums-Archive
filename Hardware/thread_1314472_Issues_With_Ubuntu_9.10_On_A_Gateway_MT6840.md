---
title: "Issues With Ubuntu 9.10 On A Gateway MT6840"
date: 2009-11-04
forum: Hardware
---

### Post by SketchInYourFace on 2009-11-04
I just recently installed Ubuntu 9.10 on my GatewayMT6840 laptop and everything functions great except every 10-15 secs of no use the LCD brightness adjust menu pops up on the top left corner of the screen. I'm not sure if its a hardware issue do to the integrated Intel graphics chip or software related, any help would be much appreciated thanks

---

### Post by SeattleOtaku on 2009-11-18
On my MT6821, I was seeing the same effect (even when active) until disabling "Auto Dim" in the BIOS; though I'm currently running with it enabled again to test and not seeing it occur.  Both ways, manual controls and gnome-power-preferences still work just as well, though the OSD bars always show as "maximum" even when dimmed.

My bet's on gnome-power-preferences (perhaps "Dim display when idle" or "Reduce backlight brightness"), as that and the BIOS "Auto Dim" were the only two I had tweaked when stopping it on mine.  OSD shows up when power-prefs kicks in to change/restore things.

~ Eric

(Edit...)  My bet's shifting back to the BIOS or shoulder shrugging, as even an unmodified Live-CD test wasn't doing this anymore either.  Wouldn't be the first time that a save-and-exit refreshed things. ^_^

---

### Post by SeattleOtaku on 2009-11-19
(Would have edited again, but bumping it to ask about possible sudo need...)

Back to betting on Gnome software; today the screensaver kicked in, and coming back from that idleness, the every-few-seconds flash of the OSD restarted, even after turning 'Dim display when idle" off (OSD still flashes on when idle and moving the mouse again, the display just doesn't dim).  Of course, my BIOS still has the "Auto Dim" enabled at the moment.

Anyone reading know if the System / Preferences / Power Management needs a sudo?  Likely not (tried 'sudo gnome-power-preferences' and saw the same settings), but just a thought....

---

