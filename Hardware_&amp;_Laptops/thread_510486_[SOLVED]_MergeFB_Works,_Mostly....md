---
title: "[SOLVED] MergeFB Works, Mostly..."
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by gers4302 on 2007-07-26
I'm running Feisty on a Dell Inspiron 600m.  It is on a dock and has a 17" LCD attached to it.  I got MergeFB to work, so that I can use both the laptop LCD and the 17" LCD at the same time.  I've got two little problems.

1: The dock has both a DVI and a VGA connector.  The laptop only has a VGA connector.  I could only get the external monitor to work on the VGA connector.  Is there a way to use the DVI on the dock?

2: The 17" LCD is to the left of the laptop LCD.  When using both displays, GNOME puts the panels on the left screen.  Is there a way to force GNOME to always use the LCD screen?

---

### Post by wsmoser2004 on 2007-07-28
1:  I'll be honest, I have no idea.  I really responded so I could answer your second question.  My guess is that no, the DVI connector will not work, but that's an uninformed opinion :).

2:  In my xorg.conf, I have a line that looks like this for MergedFB: 
```

Option "MonitorLayout" 		"LVDS,CRT"

```
(yours might be: )
```

Option "MonitorLayout" 		"LCD,CRT"

```
I think this really just defines which is your "primary" monitor.  LCD/LVDS specifies the "primary" monitor, and CRT specifies the "secondary" monitor.  So since your external screen is on the left, Xorg thinks it's the primary (because note that LCD/LVDS is on the left).  

So the answer is...flip them.  Make it "CRT,LCD" or "CRT,LVDS."  I think that'll do it.  If you don't have that line, add it :).

Note that LCD/LVDS/CRT don't actually refer to the type of display you have.  So even though you have an LVDS (laptop screen) and an LCD, "LCD,LVDS" would probably confuse the radeon driver a lot :).

And if you haven't seen the radeon driver wiki page yet, it describes some about MergedFB:
[https://help.ubuntu.com/community/RadeonDriver#head-793a669ccaf959871b32b81503e56817861c8c50](https://help.ubuntu.com/community/RadeonDriver#head-793a669ccaf959871b32b81503e56817861c8c50)

---

### Post by gers4302 on 2007-07-30
I tried switching the MonitorLayout option to no avail.

Digging around through that link you posted, I did find the "MergedXineramaCRT2IsScreen0" option.  The Xinerama option takes the left most screen as Screen 0, so setting that option to false did the trick.

Also, looking through the documentation, I don't think the radeon driver will support the DVI connection on the secondary display.  This looks to be an option only for the Primary display.  Weird, but Oh Well.

Thanks for your help.

---

