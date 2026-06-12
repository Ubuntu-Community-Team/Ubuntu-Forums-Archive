---
title: "can't set wxga 1280x800 resolution"
date: 2012-08-17
forum: Hardware
---

### Post by pirkadatka on 2012-08-17
I used to have PC Linux OS and Ubuntu 6, just switched to Ubuntu 12.04 and have problems with resolution.

In System Settings/Displays, all I could find is a 800x600 and a 1024x786 resolution, although my laptop's screen is 16:10 and a 1280x800 res worked fine with Windows, PC Linux OS and Ubuntu 6 as well.

I tried various tricks found here in the forum, but none worked.

What people having the same problem are asked:

```
hajni@hajni-ESPRIMO-Mobile-V5535:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

Then, tried to use XrandR, added a new mode (1280x800_60.00), still, when I try to use it, I get:

```
hajni@hajni-ESPRIMO-Mobile-V5535:~$ xrandr --addmode default 1280x800_60.00
xrandr: Failed to get size of gamma for output default
```

I would like to emphasize, that I USED this resolution for years. Is it possible Ubuntu 12 simply can't recognize it??

Then, tried to find xorg.conf and mess around with it, but couldn't, there was no such file. Then, I read that Ubuntu 12 doesn't need one but I can generate one, but this is what I got...

```
hajni@hajni-ESPRIMO-Mobile-V5535:~$ sudo Xorg -configure
[sudo] password for hajni: 

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```

Tried going back to System Settings/Displays, and altough now I DO have an option "1280x800 (16:10)", if I try to apply it, I get an error message saying:

"The selected configuration for displays could not be applied

required virtual size does not fit available size: requested=(1280, 800), minimum=(640, 480), maximum=(1024, 768 )"

Does someone know the solution? What else could I try?
Everything's messed up and I don't want to switch back to PC Linux OS, I had a lot of bugs...

Thank you for your time and help in advance!

---

