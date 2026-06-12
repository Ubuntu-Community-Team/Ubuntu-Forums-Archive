---
title: "How to launch app upon Palm Hotsync (SERIAL)"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by ChrisC on 2007-08-07
In Ubuntu, under System -> Preferences -> Removable Drives and Media, on the "PDAs" tab, there is a setting for what app to launch if a Palm HotSync is detected.

By default Ubuntu points you to using Evolution, but I prefer a more stripped down app -- Palm Desktop itself is a work of art but sadly not available on Linux or even in Crossover/Wine.  So I've just started using JPilot.  Supposedly the command line entry for syncing JPilot is "jpilot -s" (but that's not documented anywhere) so that is what I entered in the preference mentioned above.

If I hit the hotsync button on my Palm AND hit the HotSync button within JPilot then the sync transpires fine.  However if I JUST hit the hotsync button on my Palm, nothing happens.  

I am interfacing via serial ( /dev/ttyS0 ) because USB syncs were crashing and wiping out my PDA :(

Is there something I need to do to get the system to recognize the HotSync event on the serial interface?

Please note that I'm running JPilot and interfacing serially, so pilot-link / gpilot / USB solutions don't apply ...

Finally, note my sig!

---

### Post by ChrisC on 2007-08-08
anyone?

---

### Post by ChrisC on 2007-08-10
ping?

---

### Post by ChrisC on 2007-08-10
Ooookay, I give up.  For the fiftieth time, I wish Ubuntu had a paid support option that was less than $250, just so I can get answers to my 5 questions a year without having to beg for them!

---

