---
title: "Getting 1920x1200 res for T240"
date: 2009-06-17
forum: Hardware
---

### Post by ghmerrill on 2009-06-17
I know there have been threads in various forums about this in the past, but I haven't seen any general successful solution.  I'm thinking it can't be that difficult.  So I have hopes someone on this forum will provide the needed details.
 
I just got a Lenovo Y 550 and put ubunto on it.  I really didn't even try it out much with Vista before doing that.  It works very nicely, except ...
 
I have a nice Samsung T240 (actually one in my office and one at home) that I use every day.  My work computer is a Dell laptop running XP.  With that system, it was just plug and play.  Got the maximum 1920x1200 resolution as soon as the monitor was plugged in.
 
On the Ubunto system, I can't get it.  It doesn't even show up in the Resolution list in the System->Preferences->Display dialog for the Samsung monitor.  The best it will do is 1280.
 
What will it take to make this work?  If I need to add something to xorg.conf (or somewhere else), please just let me know what that would be.
 
Thanks for any insight on this.

---

### Post by whitfield.fowler on 2009-10-05
I had the same problem trying to drive a Samsung t240hd. I tried a simple change to the xorg.conf file, and it seems to have done the trick for me.

first I backed up the file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```opened the file
```
sudo gedit /etc/X11/xorg.conf
```changed two numbers from their original setting to numbers large enough to accommodate the big screen
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    [COLOR=Red]1920 1776[/COLOR]
    EndSubSection
EndSection
```I actually changed the numbers to 1920 1200, but then was prompted to let the system change the file, to which I responded "ok." The system apparently changed the numbers to 1200 to 1776 so that I could stack the two monitors on top of each other (1200 + the 576 of my netbook's display).

I'm running an hp mini 110 netbook with ubuntu netbook remix.

---

