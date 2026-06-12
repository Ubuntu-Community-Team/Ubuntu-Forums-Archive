---
title: "[SOLVED] SVideo output for ATI on 8.10"
date: 2008-12-17
forum: Hardware
---

### Post by FoxSpy on 2008-12-17
All,

I recently installed Ubuntu on my old IBM Thinkpad R40, Model 2723-3XU. This uses an ATI Radeon Mobility 7500 card, which has the s-video output on it. However, I can't get Ubuntu v8.10 to recognize the s-video out. I tried modifying my xorg.conf based off this, but that didn't seem to help or I did it wrong. I left the driver and BusID off as my original xorg.conf file did not have those anyway. However, this didn't work and I had to restore the backup while in low graphics mode.

If anyone has any idea what I need to do, I'd appreciate it. I've been googling and trying things to no avail. Below is my xorg.conf file as it appears minus all the comments at the beginning. Thanks for any help anyone can give me.

In addition, I've also been on the following pages.
[http://ubuntuforums.org/archive/index.php/t-198733.html](http://ubuntuforums.org/archive/index.php/t-198733.html)  No real luck here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  This is outdated, does not include Ubuntu 8.10.  


Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection


Edit:
This may actually belong under Multimedia & Video.  I was going with the "Well, it is my laptop" line of thinking.  Mods feel free to move this if it does belong elsewhere.

---

### Post by FoxSpy on 2008-12-17
I got it working using xrandr but now the picture is too red.  Any ideas on how to fix this?

---

### Post by FoxSpy on 2008-12-18
Fixed color problem by using S-video cable instead of the svideo-composite adapter I've been using.

---

### Post by Gizmot on 2008-12-29
> **FoxSpy said:**
> I got it working using xrandr but now the picture is too red.  Any ideas on how to fix this?


I'm also trying to get it working on an IBM R40. Could you please share some tricks and hints?

thanks

---

### Post by krak on 2009-01-07
Thank You FoxSpy for giving me idea how to enable s-video on my IBM R40 :popcorn: 

@ Gizmot i use those commands

```
xrandr --addmode S-video 800x600
```
```
xrandr --output S-video --mode 800x600
```

and everything works well.

unfortunately i can't enable resolution 1024x768 is 800x600 max ?

If you want to watch movie on a TV using VLC player go to Video settings and for output choose "OpenGL video output"

---

### Post by AdamSorensen on 2009-01-16
Nice tread, thanks a lot. 

I now got the s-video on my ati 9700 working.

My problem is that I would like to enable the s-video on boot, because the intention is to only connect to a old tv and not a monitor. 

Is there any way to make s-video a default setting, or adding a start-up script?

/Adam

---

### Post by hrvoje-sl on 2009-01-19
Hello to all from Croatia. I'm a new user of the ubuntu 8.10. I have ATI RADEON 9200SE and so far have not been able to turn on the tv-out. After xrandr it says s-video disconected. Also tryed adding the resoluton, mode, and the things that you mentioned. If there is any advice left please let me know. It would probably be usefull if someone has the same card and is using tv-out.

---

### Post by Kumagoro on 2009-01-22
> **krak said:**
> Thank You FoxSpy for giving me idea how to enable s-video on my IBM R40 :popcorn: 

@ Gizmot i use those commands

```
xrandr --addmode S-video 800x600
```
```
xrandr --output S-video --mode 800x600
```

and everything works well.

unfortunately i can't enable resolution 1024x768 is 800x600 max ?

If you want to watch movie on a TV using VLC player go to Video settings and for output choose "OpenGL video output"

I used this on my compaq nx9110 with a ATI 9000 IGP, and even though it worked, how can I disable (revert to original res) after using it? I get a screwed up desktop after I switch back to normal res.
Theoretically it's 1024x768, and it looks like that, but the other part of the desktop (the one that exceeds 800x600) is unusable
 Also the screen flickers a bit, as if it sent a bad signal (europe PAL here).


Byt nevertheless, this post helped me. It should be stickied :)

---

### Post by Lauren_W on 2009-02-25
I'm having the same problem, not solved for me! 

I have a Dell Inspiron Laptop with ATI Radeon Mobility X1400 video card, and run Ubuntu 8.10. In Windows I could easily plug in the S-video cable from the TV and with a couple clicks had the TV as a second monitor enabled. 
I am new to Ubuntu and love it so far, but am frustrated with the difficulty of getting the TV screen up as my second monitor. I followed the instructions outlined above, and no go. Went to the links posted by FoxSpy, but they didn't work either. Are there additional tweaks I need to make that I may have missed? I have not edited my xorg file at all, do I need to do this first? 
thanks!

---

### Post by logicalinsanity on 2009-03-11
RE: Lauren - I was somewhat in the same boat.  I couldn't figure out how to get s-video working on my Radeon Mobility 9600 with the default, open source drivers and there was nothing being listed in the restricted driver downloads for my card in Ubuntu.

However, I eventually got s-video working by using the proprietary driver directly from ATI's website.  Use their driver search tool and, once you're on the download page, you'll see an instruction PDF link that will walk you through the installation steps (if you're not sure how).

After installing and initializing the ATI driver per their instructions, reboot and your secondary display over s-video should be working.  If the s-video display is in black and white (like mine was), you can open Catalyst Control Center and expand the display options for the 2nd TV display.  Find the option that allows you to set it to 'NTSC' instead of using the location (United States) setting (Assuming, of course, that is your location).

UPDATE:
Actually - I was wrong.  Using the auto-installer from ATI's binary would result in my display going black after the initial login (this was on a clean install of Ubuntu with the open source drivers being used).  Instead, I manually installed them [using this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").

---

### Post by janwari on 2009-04-03
I was faced with a similar problem. 
One workaround I found was to create two seperate shell scripts that turns s-video on and off. 

So before we run VLC I run the following script to change my screen resolution to 800x600.

```

#!/bin/sh -e

xrandr -s 800x600
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

```

And after we are done watching the movie/video we run the following script to change the resolution back to normal.

```

#!/bin/sh -e

xrandr --output S-video --off
xrandr -s 1024x768

```

I found that OpenGL output in VLC used to cause the video to flicker intermittently. Changing the video to "X11 video output" resolved the issue. 
To change the video output in VLC go to Tools->Preferences->Video and change "Output"

@krak thank you for your initial solution of using xrandr to turn on s-video

---

### Post by barabaskid on 2009-05-31
I am having a similar problem, and was wondering if anyo0ne had any ideas.

I have a radeon 9800 card, and I installed the driver and the Catalyst Control Center. My tv and monitor both display the boot and bios screen on start up. Once the ubuntu flash screen comes, my tv ceases to display anything. After the load screen, my monitor goes black as well, and I am unable to see anything.

Any help would be appreciated. I tried the commands in the post in terminal, but I get:

xrandr: cannot find output "S-video"

I may have done something to screw up the settings, but if so I have no idea how to undo it. Any thoughts much appreciated.

Samuel

---

