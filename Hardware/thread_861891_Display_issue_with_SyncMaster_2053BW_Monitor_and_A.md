---
title: "Display issue with SyncMaster 2053BW Monitor and ATI graphics card on ubuntu 8.04"
date: 2008-07-17
forum: Hardware
---

### Post by urban_ryoga on 2008-07-17
Hi a newbie here. I am running into issues displaying the picture from my laptop to another monitor. I am using a  Fujitsu Lifebook A3210 laptop. The thing about it that may be giving me an issue is the ATI graphics card that is built inside. I installed the driver on my laptop and I am able to view on the maximum resolution on my laptop screen, however when I attempt to display on my external monitor I run into many issues.

First and foremost I tried to follow the steps located at: [http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

However I sadly get stuck at step 2 as it complains about some issue with my xorg.conf file:
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Uninitialised file found, configuring.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault

I figured that I have to reconfigure my xorg conf file (odd to me because I just installed ubuntu yesterday). I looked up the command and used:
sudo dpkg-reconfigure xserver-xorg

I assumed that this was the right command, but the UI for this closed after I entered some information about my keyboard. I never seen steps regarding the checking of my monitors and whatnot (assuming that is what xorg is for). Because of this I am currently stuck in using that path to fix my issue.

I also tried using the other current applications installed by default on Ubuntu. I went to System -> Preferences to find "Monitor Resolution Settings". There I found that Ubuntu was actually able to detect my monitor and its maximum settings fine and that for my laptop monitor just fine. However from this application I can't seem to separate them as multiple screens. Even by moving them apart they both share the same view so there is needless overlap. When I try disabling my  laptop monitor (I don't want to see it is on if there is no point in using it), but for some reason my external monitor complains that my laptop is no longer sending the correct signal.... There also appears to be a refresh rate issue with the monitor as I can notice part of the display looking wavy.

The second app I attempted to use was called Screens and Graphics. In this application I appear to be unable to auto detect my monitor and no matter what setting I set to my external monitor it fails.

I am completely at a loss as I have tried to fix this for over a day and a half now. I tried it on a windows machine first with a similar graphics card before attempting on this laptop with no issue. Do you guys have any ideas that can help me out?

---

### Post by urban_ryoga on 2008-07-17
Actually I think I will be returning this monitor. I tried again on windows and noticed the refresh rate still isn't that great even with the drivers installed....

---

