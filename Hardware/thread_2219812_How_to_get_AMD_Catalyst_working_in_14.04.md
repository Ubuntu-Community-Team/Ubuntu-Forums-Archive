---
title: "How to get AMD Catalyst working in 14.04"
date: 2014-04-25
forum: Hardware
---

### Post by Marian_Domanik on 2014-04-25
Hi. I was trying AMD forums, Phoronix forum, Ubuntu launchpad without 1 single response, so I guess I will try here too...

So, I'm using ATI 7850, installed  Ubuntu Gnome 14.04. At first I tried fglrx from "Additional drivers",  which didn't work (same as the new one, read on). So I reverted back to  Xorg drivers, which are awesome. Now that the new version of Catalyst  is available, the 14.4 RC1, I convinced myself to give it a try again.  So I downloaded the driver from the AMD website, installed, rebooted,  and it didn't work again, just like the former fglrx.


 So my issues are:


[LIST]
[*]The top 1/3 of the screen was tearing when moving windows, scrolling,  etc. Tried all the settings possible with Tear Free and VSYNC.  Currently I have two options: Either I use Tear-free, which removes my  top screen tearing BUT the whole desktop is totally laggy and slow. Like  moving windows around, resizing, showing Gnome Activities, etc...Or  when I disable Tear Free, everything is fast and snappy, just like with  the Xorg drivers, but the top of the screen is tearing like hell. This  is my personal biggest issue, because the desktop experience is  absolutely terrible with fglrx. With open source radeon drivers the  desktop is extremely fast and snappy...with fglrx just terrible.
[/LIST]


[LIST]
[*]Docky has a weird glitch when set to 3D mode, like it extends the  dock panel more as it should, without textures applied. I can't provide  screenshots since I'm back to open source drivers and I'm tired of  constantly reinstalling them.
[/LIST]

So there are my problems. I really would like to use Catalyst  drivers, as I play some games and I noticed the performance is much  better with Catalyst (tried Portal2, Dota2) and also with Catalyst, my  GPU fan speed adjusts dynamically with load. With RadeonSI drivers, the  GPU reclocks itself, but fan speeds are constant, which is really  annoying when the card is idle.
 Any help appreciated!

---

### Post by QIII on 2014-04-25
Could you tell us, step by step and in detail, how you have installed it?

From what I have seen, the 7850 has been a particular source of frustration for a lot of users.

---

### Post by Marian_Domanik on 2014-04-25
After installing OS, I went to "Software & Updates", chose "Additional Drivers" and picked the option "Using Video driver for the AMD graphics accelerators from fglrx (proprietary)".
Rebooted and was welcomed with terrible desktop experience...so I reverted back to Xorg drivers, which are working very well in desktop, but in-game are very poor.

Then for the Catalyst 14.4 RC drivers, I downloaded the official package from AMD support website. Unziped, and from the terminal as root ran the installation script ./amd-driver-installer-14.10-x86.x86_64.run. The GUI installer showed up and I installed the drivers. Asks me to reboot, so I did. Again, the desktop experience is really painful, slow, tearing, bad. However no tearing in games, in video...

---

