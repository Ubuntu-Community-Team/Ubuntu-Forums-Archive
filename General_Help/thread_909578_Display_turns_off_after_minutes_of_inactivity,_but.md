---
title: "Display turns off after minutes of inactivity, but it shouldnt be!"
date: 2008-09-03
forum: General Help
---

### Post by seidleroni on 2008-09-03
I currently use Xubuntu (Hardy Heron) and I'm configuring it for a kiosk application.  The problem is that the display is turning off after a few minutes of inactivity, but I checked the settings for the power management, but for the setting "Put computer to sleep when inactive for..." I have "Never", and for the setting "Put display to sleep when inactive for" and I have "Never" for that as well.  

On the screensaver I have "Activate screensaver when the computer is idle", I have it UNchecked.

I dont understand why the display turns off.  This is a single board computer with touchscreen and when I the display is off, when I touch a key or touch the touchscreen, the display turns off.  How can I keep the display on all the time?

---

### Post by cyberdork33 on 2008-09-03
Are you on a Mac? If so, what type? Otherwise, you are in the wrong forum.

---

### Post by seidleroni on 2008-09-04
No I'm not on a mac at all.  I'm using a Panel PC.

---

### Post by Bronto on 2008-09-04
I've had the same problem with my Ubuntu box.
It went away after moving the "Put computer to sleep when inactive for" and "Put display to sleep when inactive for" sliders from "Never" to a random value then back to "Never".

---

### Post by Joeb454 on 2008-09-04
> **seidleroni said:**
> No I'm not on a mac at all.  I'm using a Panel PC.

And so moved to General Help

---

### Post by seidleroni on 2008-09-04
Changing the times and then putting them back to "Never" didnt help.  Any other suggestions?

---

### Post by tetsuo29 on 2008-09-06
I'm having the same problem. I'm hoping that someone will post a fix soon.

---

### Post by tetsuo29 on 2008-09-06
I think that the following how-to (from [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)) fixes this problem:

> HOW: Applications>settings manager> click on Autostarted apps button.
click add. give it a name, a description and for command type
"gnome-screensaver". click ok and then CTRL-ALT-BACKSPACE. log back in and your power settings will actually work, including suspend password, screensaver and whatever screen settings you have selected.

It's only been about 30 min. since I followed those directions, but my screen has yet to blank.

---

### Post by user11 on 2008-09-07
I was trying to use the cool screen savers, but my screen would go black after a few mins, regardless of how I adjusted ANY of my settings. I then realized that I didn't activate my Nvidia driver, so I figured that may have been it. After I activated it, my screen stopped going black, but now I have no screen saver at all! This is a real pain in the a**.

---

### Post by jimmy the saint on 2008-09-16
tetsuo is correct.  The issue is that gnome-power-settings relies on gnome-screensaver in order to manage the screen.  This is not just true for screensavers, but for ALL functions having to do with the screen.  That means that if gnome-screensaver is not run at startup, nothing you do in the power setting (ie settings to control when the screen blanks) will matter.  Try running gnome-screensaver from a terminal and then set the settings you want and see if it works.  If it does, add it to the session manager and your problem will be solved.

---

### Post by ricardisimo on 2009-01-20
Well, the real issue is that so many things in Gnome are not as well thought-out as one would hope. Using VLC (rather than totem or any other Gnome app) to watch DVDs and video solves the problem. I have screensaver set to kick in after 3 minutes of inactivity, and to lock the screen (otherwise my four-year-old becomes a major threat to my comp) but it never turns on while I'm watching a movie. 

I'm assuming that VLC sends a signal regularly to gnome-screensaver not to kick in while it is playing. Unfortunately, i haven't found an embedded player for Firefox that will do the same, so watching newsfeeds, etc. is a bit challenging. [sigh] Gnome is very frustrating, to say the least. Based on the original poster, so can XFCE be.

---

### Post by dcstar on 2009-01-20
> **tetsuo29 said:**
> I think that the following how-to (from [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)) fixes this problem:

It's only been about 30 min. since I followed those directions, but my screen has yet to blank.

I'm glad this post was revived, I just installed 8.04 on a eee-PC to be used as a shop display system and could not stop the screen blanking - hopefully this will provide the solution.

---

### Post by ricardisimo on 2009-01-28
Curiouser and curiouser... I just noticed a bizarre little quirk in Firefox that pertains to this topic. If you click on the BBC RSS newsfeed button (the one that always comes on the Bookmarks Toolbar of virgin installs of Firefox on Ubuntu) and mouseover the news items without actually selecting any of them [see attached screenshot,] the screensaver never kicks in. Well, I don't know about never, it didn't come on after more than an hour of sitting idle.

Two things: [LIST=1]
[*]This smells like a bug to me;
[*]If FF can indeed prevent my screensaver from activating, why can't it do so while an embedded video is playing?
[/LIST]

---

