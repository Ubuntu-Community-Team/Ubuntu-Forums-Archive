---
title: "LCD Burn in / Image Persistence Problem"
date: 2008-08-14
forum: Hardware
---

### Post by Kirivon on 2008-08-14
Hi all,

There was a thread here from about a year ago where someone experienced the exact problem I am currently suffering:

[http://ubuntuforums.org/showthread.php?t=514790](http://ubuntuforums.org/showthread.php?t=514790)

Unfortunately, there doesn't seem to be any solution to the problem.

I am running Ubuntu Hardy 8.04.1 and using Gnome's Misty theme. On the hardware side, I have an evga 8800GTS(with the nvidia-glx-new drivers installed) pushing a Dell 2007WFP.

I've been running Ubuntu on a whim for about a week, and I've been amazed by how much more user friendly it is than the slackware/gentoo installs I putzed around with four years ago. But, upon restarting several times today I noticed that the top menu bar's shadow and text content persisted on my display.

I'm not sure if it's the high contrast of the white bar to black text that caused the rapid burn in, but I'm at a loss how this could have happened so quickly. I had left Ubuntu's power settings on, turning the monitor off automatically after 45 minutes, and I shut the panel off when I'm away for extended periods of time.

I've been using the same wallpaper, the same start bar orientation, and same quick launch icons for a year on my Windows XP install. Under Windows, I have the display to never shut off, and I don't run a screen saver. I've left my panel on for days at a time, and this is the first time I've ever had any kind of problem with persistence.

If anyone has any ideas on what is causing the problem, or how to fix it I would be greatly thankful. Over the course of the week I've worked out about 80% of the quirks that were bothering me when transitioning to linux as my primary OS, but this problem is an instant deal-killer.

---

### Post by abgemacht on 2008-08-14
Luckily, unlike CRT burn-in, LCD burn-in can be corrected.

Turning off the screen for a few hours should restore the crystals to their normal state.  I've also heard that setting your screen saver to white and leaving that running for a while works, but I've never tried it.

In the future, I'd suggest using a screensaver or setting your monitor to a power saving mode.  This would have the added benefit of saving your backlight. 

As to why this happens for you in Ubuntu more than in XP, I have no idea.


Hope that helps.

---

### Post by Kirivon on 2008-08-15
Alright, I seem to have worked it out.

I let DeadPixelBuddy run for about eight hours, cycling through black, white, red, green, blue, and yellow. That got rid of all the visible text, with only a little of the menu bar's shadow remaining in the top left corner.

It seems that high-contrast transitions, black to white especially (aka the majority of gnome's menu bar), are the worst in causing image persistence due to the high disparity of LCD charge in those areas. Also, Dell panels seem particularly susceptible to ghosting.

As an experiment, I left firefox maximized under windows for about five hours. When I came back, I noticed the persistence of firefox's menus in the top left corner, which coincided with the area where I saw the worst ghosting in ubuntu. The ghosting, however, was far less noticeable than the image left behind by gnome's menu. I closed firefox and left the computer at the desktop for three more hours, after which all of the ghosting had cleared up.

I suspect that the high contrast of gnome's menu bar is to blame for the sudden and severe persistence on my panel. Also, it seems that my monitor only ghosts on the top 1cm of the display, a problem never encountered in windows due to a lack of a static menu bar at the top of the screen.

I guess the solution for now is to consolidate to one menu at the bottom of the screen. Screen savers and power saving modes are of limited value due to the fact that when my monitor is on, I rarely wander off for long enough for a screen saver to kick in. I simply shut off the panel when I am going to be away for any prolonged period of time.

---

