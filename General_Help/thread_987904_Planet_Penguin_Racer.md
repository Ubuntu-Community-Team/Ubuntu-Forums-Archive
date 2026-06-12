---
title: "Planet Penguin Racer"
date: 2008-11-20
forum: General Help
---

### Post by RampageAI on 2008-11-20
This may not be one of those "high priority" problems but after upgrading from Ubuntu 8.04 to Ubuntu 8.10 Planet Penguin Racer stopped working.  It functioned normally before now it opens full screen with a black window and plays the opening music.  You can exit by pressing Escape twice and it doesn't indicate any error messages if it is executed from the terminal.  When it was run in 8.04 it ran perfectly fine with compiz turned on and it still doesn't work with compiz turned off in 8.10.  Any suggestions or thoughts for troubleshooting this problem?

---

### Post by RampageAI on 2008-12-04
I finally did get this working (or at least got a workaround) and here's what I found out...

Penguin Racer does not seem to work on fullscreen.  However it works fine in windowed mode.  All of these settings can be changed in the file ~/.ppracer/options.

Notes:

This problem occurred on a laptop with a widescreen resolution of 1280x960 so I think it's possible that something occurred between Ubuntu 8.04 and Ubuntu 8.10 that would not allow it to handle fullscreen mode or at least switch into fullscreen mode properly under those settings.  However, I have not yet tested it by...

1) Changing the resolutions in the ppracer options file
2) Changing the screen resolution of the laptop

However, it's possible this could be leading to a bug in 8.10

---

### Post by Anfanglir on 2008-12-11
Recently I have problems with Penguin Planet Racer in 8.04 as well on the kids computer. It used to work in fullscreen mode. Tried Intrepid for a while, but switched back to Hardy due to lacking graphic driver support in Intrepid for the old Radeon 9700. Back in Hardy the Radeon drivers install fine, everything seem to work, but when I try PPR in fullscreen the screen goes white and I have to reebot to break the spell. Changing to "fullscreen false" in the option file I can play again, but it's annoying not to have fullscreen.

I'm guessing that PPR has been revised the last 6 months with unintended side effects for old hardware? or am I missing something obvious here?

/ Anfanglir

---

