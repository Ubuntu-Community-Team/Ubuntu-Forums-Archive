---
title: "Nvidia Separate X screens  11.10"
date: 2011-11-15
forum: Hardware
---

### Post by Betanu701 on 2011-11-15
Has anyone been able to get separate x screens to works in Ubuntu 11.10?

I know there is a bug that forces the system to freeze shortly after login. 

If anyone has gotten it to work, can you please instruct me and others on the correct setup for the X Server?

Thanks

Beta

P.S. I will continue to work on it and see if I can make it work. If I do I will post how to do it on here.

---

### Post by bshosey on 2011-11-21
I would like this too. I can get xirama to work but I want separate x screens

---

### Post by MugOTea on 2011-11-29
How far have you got?

I'm trying to set this up (blindly) and so far I have 1/3 of the results I was hoping for.

I have a 20" primary display, and a 14" touch screen secondary display. The touch /  2nd monitor is plugged into the nVidia VGA port, and the primary is using the DVI port.

To configure the two monitors (ubuntu settings Displays ONLY shows the primary) I opened a terminal and and backed up my nearly unused xorg.conf file then used the nVidia settings tool to enable a secondary screen with it's own X. Saved the settings to a new xorg.conf and logged out/in.

What I see is; Primary screen loads as normal, 2nd screen receives input (wakes up) and displays a WHITE desktop. Left alone, it appears to stay like this indefinitely. The mouse cursor will track to the 2nd screen (as I hoped) and while the WHITE desktop is there, I can right-click for a context menu shortly before the WHITE background vanishes and my configured desktop background appears. The cursor on the 2nd monitor is then a cross and the mouse / keyboard has no effect.

The touch screen works like a large touch pad, not what I wanted, I am hoping to configure a standard unity desktop alongside a touch terminal containing shortcuts / custom menu system on the 2nd screen.

I'm unable to execute any applications on the 2nd screen currently, nor interact with anything on it except moving the mouse cursor.

Have either of you got further than me, or would the following guide on my actions help you at all?

So, presuming you already have all the nVidia drivers installed and activated, this is what I did / done:

1/ Check for an existing "xorg.conf" and back up / remove.
    "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup"
2/ Launch nVidia settings manager
    "sudo nvidia-settings"
3/ Enable secondary screen from "X Server Display Configuration"
    Choose "Configuration: Separate X screen"
4/ Click on "Save to X Configuration File"
    When asked enter "/etc/X11/xorg.conf" for the config file.
5/ Quit nVidia Server Settings, then log out and log back in again.

I post this hoping someone will reply and say something like, "Nearly there, you just have to ..." ;)


p.s. My two monitors were back to front at first too, primary was on the little screen and large screen left empty. To fix this I simply enabled BOTH monitors in the nvidia-settings application, logged out, logged back in, then disabled the screen that was currently primary but I wanted to be secondary. logged out, logged back in again then re enabled the monitor I wanted secondary. Obviously backing up and saving the xorg,conf each time. There's probably a much easier way but this worked for me.

---

### Post by bshosey on 2011-11-29
it seems we are at the same point. I get wallpaper on all three monitors. I can move the curser over to the montitors. But only one I am able to launch things in.

---

### Post by bshosey on 2011-12-04
This command will set it up 3 monitors with sexperat x screens
sudo nvidia-xconfig --no-sli --no-twinview --separate-x-screens --xinerama

The problem I am having now is when I mouse over the sound menu the top bar crashes and reloads. Also it will act like the mouse button is stuck on click and the menus will drop just by mousing over them. I actually prefer the separate x screens I just need to get this fixed. Does any one have a idea how I can fix this.

---

### Post by ostraaten on 2011-12-11
Assumption is the mother of ...

Bought a second hand monitor today assuming I would be able to use it with Ubuntu 11.10. I´m so used to separate screens at work (on Windows 7) and I have used separate screens on an earlier version of Ubuntu, it was a bit buggy but more or less working.

It seems this is not going to fly with Ubuntu 11.10. Shame on Ubuntu! Monitor was cheap enough so I&#314;l just toss it away.

---

### Post by bshosey on 2011-12-11
This is the reason why I run Debian Squeeze on this system now. I am able to run just fine with 3 separate xscreens. I really wish I could get it to work the way I want in ubuntu.

---

