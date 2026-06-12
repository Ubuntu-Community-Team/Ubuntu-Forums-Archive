---
title: "Dual Monitors"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by American_Outcast on 2007-09-12
There is to much information out there on this. I don't know where to start, lol.

I have 1 Nvidia 6200 AGP
1 LG Flatron 19" 196wtq 1440x900 Wide Screen (I want this for digital but it can be used with analogue.)
1 19" Gateway EV910 1280x1024 or 1024x 768, prefer the first one. 

I have the LG connected to the DVI and the Gateway to the analogue.

I want then option to stretch the desktop over both monitor or just use them both at the same time with the same desktop  or just one of them.

I know the info on how to set this up is out there somewhere, but like I said there is a lot of info to sort through. So if someone can point me there, to the thread, instructions, etc, or tell me here how to do it I would greatly appreciate it. I know it can't be that hard to do, lol.

I am using Ubuntu 7.04 .

Thanks

---

### Post by John Terzakis on 2007-09-12
Use the desktop manager that came with your video card and "stretch" them in the properties/setup.

Piece of cake :)

---

### Post by American_Outcast on 2007-09-12
Thanks. I have been playing around with this in XP..... I hate XP, lol. What I want to do once I reboot Ubuntu, my main OS, is to get dual view. It wasn't saving the information before but I think I know why, I hope. I love nvidia, only card I will buy, they make things easier in linux then other graphic cards.

---

### Post by American_Outcast on 2007-09-12
FOr some reasons it is not working. So I tried to edit the xorg.conf file and all I have to say on that is oooopssss. GOod thing I backed up the file so I was able to replace the one I screwed up.

I think this is what I want for now. When I played around with this in XP I was able to get dual view. My main desktop was on my LG monitor and the second monitor was there working. I don't like the stretched desktop on two completely different monitors and I don't need to have the same thing on both monitors either. So now I have to set this up for dual monitor. Problem is nvidia is not saving anything it says it is going to save. When I save it it tells me that not all information can be saved, etc.

So I am back to my LG until I can figure this out. I am completely new to dual monitors in any os, as if no one was able to tell, lol.

---

### Post by American_Outcast on 2007-09-12
Have an idea, think I left something out when I tried this before, figures :mad:

---

### Post by PurposeOfReason on 2007-09-12
Open a terminal, type 'gksudo nvidia-settings'. Under the X Server Display Configuration, there should be a twinview option. Play with those settings.

---

### Post by American_Outcast on 2007-09-12
Got it. Thanks everyone. I have it set up so my main desktop is on my LG and the other monitor is can be used to drag windows to, etc.

---

### Post by American_Outcast on 2007-09-12
Ok I have one problem. Ubuntu has my crt monitor is the default one. How do I change it so the LG monitor is the default? I know it has to be simple. I am asking because I went to start WoW and the LG turned off and the old gateway stayed one for the game.


EDIT:

This might help huh,

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway EV910"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +1440+0, DFP: 1440x900 +0+0; CRT: 1280x960 +1440+0, DFP: nvidia-auto-select +0+0; CRT: 1152x864 +0+0, DFP: NULL; CRT: 1024x768 +0+0, DFP: NULL; CRT: 832x624 +0+0, DFP: NULL; CRT: 800x600 +0+0, DFP: NULL; CRT: 720x400 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by American_Outcast on 2007-09-12
Well I tried a few things that didn't work. I can now officially tell people what NOT to do, lol.

---

### Post by PurposeOfReason on 2007-09-12
I'm not sure if it'd work, but switch the inputs and see what happens.

---

### Post by dmm1983 on 2007-09-12
try this site out
i found out more about envy
[http://www.stchman.com/tools_page.html]("http://www.stchman.com/tools_page.html")

---

### Post by American_Outcast on 2007-09-13
Thank you both. 

I am going to give envy a try tomorrow after some sleep, lol. It looks like a great program. :guitar:

---

### Post by American_Outcast on 2007-09-13
Just wanted to update this.

I ran sudo nvidia-settings from the command line after I made a copy of the xorg.conf file and backed it up in two places (Yeah, I a strongly believe in backing things up twice, lol.) I changed, under configuration, to twinview. Positioned my LG monitor left of the Gateway, changed both resolutions to 1440x900 and 1024x768. Rebooted. That works fine.

Now when I run World of Warcraft I get into the terminal and run sudo nvidia-settings to turn off the Gateway monitor and when I am done with the game I turn it back on and change the resolution and it works fine. No need for reboot.

Two problems. One, Gdesklets doesn't like when I do that or change the wallpaper on Twinview. It shuts down and I have to restart it. No big deal but it is annoying. Two, I can't keep any folders, bars, etc on the Gateway. If I do when I turn it off so I can play WoW it moves all of them to the LG monitor. It also leaves them there when I turn the Gateway back on.

So over all I have it working the way I want with only two small issues.

---

### Post by PurposeOfReason on 2007-09-13
Basically, you need to edit your xorg.conf file so it turns a monitor off for wow. Something like this in your screen section.

```
   Option         "MetaModes" "1440x900,1440x900; NULL,1024x768"
```

That that says is that when a program with 1024x768 comes up, turn off the left monitor. Put NULL on the best fitting side and change the 1440x900 to your two different resolutions.

---

### Post by American_Outcast on 2007-09-14
Cool, thanks.

---

### Post by American_Outcast on 2007-09-14
For some reason I couldn't get it to work for me. I will play around with it later. Because of space restrictions I have to have the crt monitor on the right of the flatscreen wide. 

So instead of changing the nvidia settings like I said above I decided to try the game in window mode. Worked great. I have my desktop icons, task bar, etc, on the crt monitor to the right and even in window mode the game fills most of the screen.

There is no way I would try and do this in XP. It couldn't handle the game that well but to have music and firefox on the right, etc, and the game on the left, XP would keep freezing on me, lol.

Now if I could just afford a better nvidia card and a mother board with 4gb of memory and a dual core 64 bit cpu, I would be all set, :guitar::guitar::guitar:

---

