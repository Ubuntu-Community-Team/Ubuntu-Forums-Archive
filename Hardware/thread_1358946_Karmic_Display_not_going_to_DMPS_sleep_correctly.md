---
title: "Karmic: Display not going to DMPS sleep correctly"
date: 2009-12-19
forum: Hardware
---

### Post by hesapotman on 2009-12-19
My problem: The LCD display on my laptop wouldn't always go to DPMS sleep. Sometimes it did, sometimes it didn't.
I tried: All sorts of fixes including updates to xserver and gnome-power-manager ... but no luck.
What I did that worked: Decided to try replacing "gnome-screensaver" with "xscreensaver", disabling DPMS sleep in "gnome-power-manager", and enabling DPMS sleep in "xscreensaver" ... and it WORKED!

Step 1:
*Open "Administration->Synaptic Package Manager"
*REMOVE package "Gnome-Screensaver"
*INSTALL package "xscreensaver"
*INSTALL package "rss-glx"
*INSTALL package "xscreensaver-gl"
*INSTALL package "xscreensaver-data"
*INSTALL package "xscreensaver-gl-extra"
*INSTALL package "xscreensaver-data-extra"
*Close Synaptic Package Manager

Step 2:
*Open "Administration->System Monitor"
*Find the process "gnome-screensaver" and KILL it
*Close System Monitor

Step 3:
*Open "Preferences->Startup Applications"
*Find the startup application "Screensaver" and select it
*Click the "Edit" button to the right
*Replace the text "gnome-screensaver" with "xscreensaver -no-splash" and click the "Save" button
*Close Startup Applications

Step 4:
*Open "Preferences->Power Management"
*Under "AC" and "Battery" tabs, set "Put display to sleep when inactive for" to "Never"
*Close Power Management

Step 5:
*Open "Preferences->Screensaver"
*When prompted to start xscreensaver daemon, allow it
*Under the "Display Modes" tab, select SOME screensaver or select "Blank Screen"
*Below that, set the "Blank After" time to some desired time (this is how long until the screensaver activates)
*Under the "Advanced" tab, check the box for "Power Management Enabled"
*Below that, set the "Standby", "Suspend", and "Off" times to some desired time (this is how long until the monitor shuts off. In my case, I just set all the fields to the same time ... 5 minutes)

That SHOULD be it! It fixed all the problems with my display not doing DPMS sleep, AND it gave me a lot of nice screensavers to choose from. Hope this works for you! =)

---

### Post by rCXer on 2009-12-19
Thanks for sharing.  I had problems with gnome-screensaver as well. It has [a bug](https://bugs.launchpad.net/gnome-screensaver/+bug/32457) in which it activates during many fullscreen games, even if the keyboard and mouse are being used.

Btw, my favourite screensaver "MoebiusGears"

---

### Post by hesapotman on 2009-12-22
> **rCXer said:**
> Thanks for sharing.  I had problems with gnome-screensaver as well. It has [a bug](https://bugs.launchpad.net/gnome-screensaver/+bug/32457) in which it activates during many fullscreen games, even if the keyboard and mouse are being used.

Btw, my favourite screensaver "MoebiusGears"
Thanks for the added info about the bug.

Just yesterday I found another bug that prevented my WLAN from connecting to networks using WPA encryption. I'm not sure if the bug is in the "iwl3945" module that drives my wireless card or if it's in the "network-manager" application, but I found another fix that involves replacing gnome-specific stuff with something else. In this case, replacing "network-manager" with "Wicd" was the solution that worked.

It's sort of a shame that so much gnome stuff doesn't work out of the box - yet Ubuntu keeps shipping it - when other apps work better (like xscreensaver and wicd).

I'll probably take the time to post my how-to on that "Wicd" soon.

Cheers!

---

### Post by konradsa on 2010-02-27
Thank you!

This problem has been bugging me in every version of Ubuntu (and other dists) since I can remember.

That's what I love and hate about Linux. Hate: Still can't get some of the basics right. Love: For any problem, you can find some support online to help you fix it. Nicely explained solution, thank you so much!

---

### Post by RT236 on 2010-03-10
Thanks!  This has been very helpful!  I had been trying to fix this for sometime on my Toshiba laptop.  I tried your ideas and it helped a lot.  I did all you posted, but I had to make some changes.  My laptop wouldn't accept any sequence that causes the backlight to go off.  What happens is I get a very muddy blue-white screen with a thin dark black line across the center.

Also, it interpreted any screensaver activity as an active laptop.  However, the "Blank Screen Only" setting in xscreensaver works fine, and I have Display Power Management NOT enabled in xscreensaver Advanced panel.

In Power Management Preferences, I have "Display" as Never, but have "Actions" in Power Management Preferences set to put computer to sleep when inactive for 10 minutes (or what one wants).

This allows my screensaver to blank the screen.  The backlight remains on, but then then later power management puts my laptop to sleep.  For my case this works fine and my backlight is, of course, now off.  It seems the Toshiba laptop hardware does not work extremely well with the screensaver and power management sw, but at least I have a stable workaround.

Thanks again for posting your information.  You really helped me to get on the right track!

Thanks!!!

---

### Post by Schuby007 on 2011-03-10
Wow... I'm reading this and shaking my head. Why in God's name would the screensaver affect the wireless network card!?!?! There is no way that I wanna go through this kind of pain just to get my screensaver working...

I appreciate the fact that you've gone through the trouble of finding a "solution" but this is ridiculous. I don't know the Ubuntu development process, but I just wish they would focus on these extremely frustrating problems instead of pushing forward and building on top of broken code.

---

### Post by Jim_in_Omaha on 2011-04-24
One thousand thank you's.

This fixed mine. Yea I am not sure why it all started a few weeks ago. The standard Gnome Screen saver was not turning off my Asus 26" display and I would see it in the morning with the back light still on. Not good, me not happy.

X screensaver has some cool screens too....

Jim

---

### Post by Unknown Frequency on 2011-08-24
Yeah thanks man. That was the end of many hours of searching for solutions!

---

