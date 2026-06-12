---
title: "ThinkPad W541 refuses to use nVidia drivers..."
date: 2015-08-05
forum: Hardware
---

### Post by Plankmeister on 2015-08-05
Hi all,

I've used around 15 hours on this problem, and it's driving me insane. I have a ThinkPad W541 running 14.04.2, and for the past 2 months (since I got it) everything has been hunky dory. I just came back from holiday, and it seems that an update to Google Chrome causes it to crash when using the Ubuntu generic "Nouveau" nVidia driver. The solution is to use Chrome with the "--disable-gpu" option, or use a proper nVidia driver.

I've tried a whole bunch of things to get a proper nVidia driver installed and working:


[LIST]
[*]Tried all available drivers in Software & Updates -> Additional Drivers
[*]Tried manually downloading and installing a whole BUNCH of available nVidia drivers, from their downloads page
[*]Have followed so many threads online with instructions on how to get it to work, that they are simply too numerous to list
[*]Manually constructed an xorg.conf file
[*]Sacrificed my first-born
[/LIST]

It all results in one of two outcomes:


[LIST=1]
[*]Boots into black screen. I can switch to a tty, so it appears to definitely be driver related.
[*]Boots into a very low resolution login screen. When I attempt to login, I am returned to the login screen after a teasing glimpse of the desktop is displayed... literally for a few milliseconds or so...
[/LIST]

So I'm stuck using the Nouveau driver, and running Chrome with --disable-gpu, which... OMFG, it's so slow it's ridiculous. Try it yourself and be amazed at its sluggishness. I really need to get these nVidia drivers working...

So any help would be appreciated.

Kind regards,

Andrew Plank

---

### Post by dino99 on 2015-08-05
why not using chromium-browser instead of chrome ? chromium is ubuntu compatible and works well with my nvidia driver.

---

### Post by Artemio_T on 2015-08-05
Have similar problem after update, works loading previous kernel (from grub menu, select second option and the the previous kernel)

---

