---
title: "ATI Radeon HD 3400 flicker"
date: 2008-11-08
forum: General Help
---

### Post by kgish on 2008-11-08
I upgraded to Ubuntu 8.10 and since then have an annoying slight flicker of horizontal lines appearing on the monitor. Nothing really major, I mean I can still read the screen, but the subtle effect is pretty aggravating and makes reading tiring after awhile.

Is there anyway to fine tune some setting somewhere to get rid of this, perhaps something having to do with the frequency? Is there a version of Catalyst I can install?

---

### Post by SleepingProphet on 2008-11-08
I've been wrestling with an HD 3450 for a couple weeks now, so I hope I can help. I had more demanding needs than normal folks cuz I wanted to run 1080P video with no horizontal tearing. Anyways, the good news is that the proprietary ATI drivers do a decent job of getting your hardware acceleration working (hello Compiz!), and should also get you the nice ATI control panel app, where you can set all sorts of stuff easily. The bad news is that you're gonna need to do some terminal jockeying to get the driver installed. After trying many methods with varying levels of success, this is the one that has worked best for me:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)
I used the 3rd option, "manual install", as the various other methods didn't always result in me getting the ATI control panel. I am a Windows guy by trade, but ever since I learned to copy / paste between terminal and other windows, stuff like this has been a breeze. If you don't know, you gotta use Ctrl+Shift+C for copy and Ctrl+Shift+V for paste inside of terminal. One gotcha I ran into is that the various flavors of Ubuntu 8.10 MUST use the 8.10 version of the ATI drivers and CANNOT use the older 8.9 drivers. Following the guide will get you the right ones :)

Aside from getting the "real" ATI drivers installed, you could also check your monitor's refresh rate in the Screen Resolution control panel. Usually rates at or above 60 Hz look OK. It depends on the display type. Most "computer monitor" LCDs will go up to like 75 Hz, which should look fine. Most HDTV LCDs will only do 60, unless you have a new one which will do 120. CRTs can usually very comfortably do 75 Hz. Generally you'll wanna get the refresh rate as high as your monitor can go to avoid eye strain.

---

