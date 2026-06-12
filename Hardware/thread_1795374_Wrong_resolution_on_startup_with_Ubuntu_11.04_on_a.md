---
title: "Wrong resolution on startup with Ubuntu 11.04 on a Toshiba Satellite Pro L500"
date: 2011-07-02
forum: Hardware
---

### Post by ubut on 2011-07-02
I recently installed Ubuntu 11.04 on my (brother's) laptop (Toshiba Satellite Pro L500. I have listed a few monitor specs at the bottom, but wasn't sure what to look for.) 
and when I turn it on, I always get the wrong resolution. It starts up as 1024x768 (4:3) with black bars instead of 1366x768 (16:9). When I start programs they often appear in the black sides (and are "unreachable") as though it realised that the screen is actually 16:10. Then after a few minutes it does adjusts to the correct resolution, but it's terribly annoying.

I thought that making a 10-monitor.conf file (I just found out that xorg.conf is no longer used in 11.04. [http://ubuntuforums.org/showthread.php?t=1730188](http://ubuntuforums.org/showthread.php?t=1730188) ) with the correct resolution (and no other options maybe?) would force it to start properly. I have never done this before, and was hoping there would be an "automatic" way of making the file, like
```
~$ sudo Xorg -configure
```which I don't know how to use anyways, and so get the error message:
> 
Fatal server error:
Server is already active for display 0
...
[COLOR=Red]thanks[/COLOR] in advance, ubut

```
~$ xrandr

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
``````
~$ lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

---

### Post by shanjay86 on 2011-07-04
hi, 
i am using toshiba L500 too this happend to mee too but after running full updates n restarted system its fine now...
 using same OS 11/04

---

### Post by ubut on 2011-07-04
hey shanjay86,
thanks for your reply. 

do you remember which updates fixed it? did you do some unscheduled updates yourself?
I installed it in May and have done all the automatic updates since then, but nothing changed.[COLOR=Black][U][URL="http://ubuntuforums.org/member.php?u=1327926"]
[/URL][/U][/COLOR]

---

### Post by ubut on 2011-07-09
_does anybody have any ideas? please!_

I don't really know whats happening, but _I don't see why it should be fixed by updates (which I have done anyways_), it seems more like a settings problem. or?

---

### Post by davidoloan on 2011-07-09
Me too...........

on a Toshiba Satellite Pro A300.

I have set up 11.04 on 4 other computers without problems.

Getting same issues except when I decided to alter the resolution to the correct setting the screen went black. Restarting, after entering the password it started with a black screen. I had to power off and start in Ubuntu Classic No Effects. Then it allowed me to restart in Ubuntu in the WRONG resolution again.

Also on startup my password box is now often not in the centre and can be off screen so I cannot click it. Have to restart.

On occasion it thinks there is a 1024 x 768 screen and a 2nd smaller screen attached.

I am using some Apple stuff now including an ipad and it doesn't do this kind of thing. I like Ubuntu and putting effort into working out how to do things I want, but this is a waste of time just like I used to have on Windows XP and from past experience the chances of things like this being fixed before the new version are slim. Each new version there is a problem specific to one of the computers.

Screen resolutions were no problem on same computer on 10.10 and 10.04.

---

### Post by davidoloan on 2011-07-09
The Phantom 2nd Monitor is called "unknown". It is marked "off" and at this point of checking it has no details though I am sure that it had small resolution figures stated at another time.

---

### Post by Blasphemist on 2011-07-09
Ubut- With 11.04 there are changes in the handling of video modes through the boot process. Please see this thread's first 3 posts for trying video mode settings in grub to see which solves your issue. The way you were trying to change this kind of settings in grub wasn't correct.

I have the same gpu you do, run two monitors and don't have this problem. The only setting I use is acpi_os=\"Linux\". That is just what it took to give ubuntu proper control of the fan. My guess is that the issue is actually in getting available modes from the screen. That is also discussed in this sticky thread and others. There is a tool to read the EDID but I don't remember what it is.

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Blasphemist on 2011-07-09
davidoloan- I'm not wild about your attitude but that can likely be said about me at times, maybe even now. What you described as happening when you changed resolution shouldn't happen. No news to you I'm sure. How did you change it? I wonder if it could have been how you did it that allowed this to happen. Just saying, it might not be a bug after all. When I change resolution in monitor preferences, it should only display valid settings as choices and when you do apply changes, you are prompted to keep the new settings or revert to the previous settings. If you press enter the previous settings are used. You can also use the same instructions I gave ubut on how to pass video settings on from grub2.

---

### Post by davidoloan on 2011-07-09
Sorry about the attitude. I'm usually positive about Ubuntu and its great overall. Some of these bugs are frustrating and for some reason Resolutions and External monitors seem to be an issue on different hardware setups on each new Ubuntu version. I don't mind putting the time and effort into figuring out how to use the system to full advantage. I enjoy that. And people are very helpful here.

Thinking about it; I think it annoyed me because Ubuntu is overall so good now that I don't like to see this kind of basic problem.

---

### Post by davidoloan on 2011-07-09
> **Blasphemist said:**
> How did you change it? I wonder if it could have been how you did it that allowed this to happen. Just saying, it might not be a bug after all. When I change resolution in monitor preferences, it should only display valid settings as choices and when you do apply changes, you are prompted to keep the new settings or revert to the previous settings. If you press enter the previous settings are used.

Went to Monitor Preferences. Resolution was 1024x768. Clicked the arrows for the options and selected the (correct) 1280x800 and clicked Apply. It immediately went Black. I restart the computer (as I could not see anything) and after several attempts and restarting it will correctly set the resolution. But then it eventually restarts at 1024x768.

The funny thing is earlier it was showing 2 screens attached and now without being restarted or used at all it is showing one with the correct resolution. Weird.

---

### Post by Blasphemist on 2011-07-09
davidoloan- Is it working right for the moment then? If so, I recommend no further changes to this. And seeing if it still is after a reboot. Did it suspend or at least turn off the monitor before it came back right?

If it does mess up again, when you change to the right settings and it goes black, did you try pressing enter and seeing if brings back the display even if it is with the wrong settings? What gpu and pc do you have? Have you checked your Xorg.0.log file for any concerns?

I don't have a solution for this puzzler but these are the questions that come to mind.

---

### Post by ubut on 2011-07-19
just wanted to thank you (Blasphemist) for the advice. I wasn't able to try because my brother went off on holiday with his laptop, and it did also look a bit much for a novice like me.
However, the last update (about a week ago) seemed to fix things (can't remember what was updated, so i really don't know why\how).
so I think i'll close the thread (report as solved).

---

