---
title: "Success with WXGA 1280x800 on HP Laptop"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by A. J. Rimmer on 2006-09-18
I've reviewed several posts lately regarding getting WXGA to work.  Rather than trying to track them all down and reply, I thought I would start a new thread since my experience doesn't quite match anything else I have read, anyway.  I hope this is of some help to others with this issue.

The laptop is a new HP Pavilion dv5000 series (actually, a dv5220us).  Since installing Dapper a few days ago my screen was at 1024x768, with no other options offered in the System > Preferences > Screen Resolution box.  I checked /etc/X11/xorg.conf and found that the only resolution listed there was 1280x800 (several entries for different color depths).

I ran sudo dpkg-reconfigure xserver-xorg, and two things happened.  Horizontal and Vertical scan rate ranges were added to xorg.conf, and 800x600 and 640x480 were added to my Screen Resolution choices under System > Preferences.  However, xorg.conf continued to list only 1280x800.  This was getting weird!

Next, I used Synaptic to install 915resolution.  I did this while on the WiFi network at the library, then spent an hour or so reading through the fourum regarding other issues.  When I got home, I restarted the computer and ran 915resolution -l, but got an error message.  (Don't recall exactly what it was, but it was short and essentially said "can't do this."  I don't want to run it again to find out in case it might jinx my success here!)

So, I decided to defer working on the screen issue and started reviewing some other things that I had downloaded and saved while at the library.  I have my desktop wallpaper set to Simple Ubuntu, and after a while I happened to notice that the "Circle of Humanity" symbol was round, not oval as it has been since the initial installation.  I checked my Screen Resolution, and it was set to 1280x800, with 1024x768, 800x600, and 640x480 as options.  However, xorg.conf still only lists 1280x800.

I know this doesn't match the way 915 resolution is supposed to be implemented, but I'm not going to argue with success or tempt fate.  I'm just happy to have the correct WXGA screen resolution and have my pictures display with the proper aspect ratio.  Fonts look great now, too, no more fuzzy look to them.

I've been using Breezy and now Dapper for about five months now.  Fixing all these little issues with the help of the fourm has taught me a lot!

---

