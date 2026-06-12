---
title: "Help with graphics problems after attaching external monitor"
date: 2011-01-26
forum: Hardware
---

### Post by Duncan J Murray on 2011-01-26
Dear All,

Can anyone help with an odd graphics problem I have which has started after I connected up a separate CRT monitor to my Thinkpad T40 laptop with Radeon mobility 7500 32mb.  I had recently installed 10.04 on the laptop, and the graphics were running beautifully, with graphics effects enabled etc...  When I connected up the external monitor, the System>Preferences>Monitors dialog box asked me permission to alter a file (I think maybe something to do with xorg), which I allowed it to, and the monitor worked without problem - both for mirroring and as extension of the desktop in various resolutions.

Now I've noticed that there's a problem when using the laptop on its own.  There is no problem with desktop effects disabled, but when they are enabled, odd things are happening such as:

.  When I minimize google chrome to see the desktop, all it shows is whatever was on google chrome's page, but shifted up by about 20 pixels.  If I pass my mouse over the desktop, the icons on the desktop 'pop up' with a patch of the wallpaper showing around it.  If I then shift to another viewport, I can see the desktop background again, and shifting back returns things to normal.

.  Switching between multiple windows throws up all sorts of artefacts, including horizontal random stripes.

Can anyone point out to me a way of fixing this?  Where can I look to work out what's going on.  My suspicion is it's something in xorg caused by using an external monitor.

Thanks in advance.

Duncan

---

### Post by Duncan J Murray on 2011-01-27
sny ideas before I go ahead and reinstall 10.04?

Duncan

---

### Post by Duncan J Murray on 2011-01-27
Yet again I am a Linux Genius!!

(tongue-in-cheek)

So I was googling stuff about 10.04/ati etc etc and came across the release notes for 10.04 which said that there were some corruption issues with old ATI cards of 32MB and smaller.  I was going to go ahead with their suggestion of adding to the xorg.conf with "RenderAccel" "off", but noticed that I had something written there already under 'display' with 2035x1035 (or something like that), and changed this to my displays native resolution of 1024x768.  Then on restarting gdm, everything works again!  Hurrah!

For those of you who come across the same problem, the steps are:

ctrl-alt-F2 to get to terminal

"sudo service gdm stop"

"sudo Xorg -configure"

"sudo nano /etc/X11/xorg.conf"

find what looks suspiciously like a wrong resolution and correct it

then save and exit from nano (sorry forgotten how to do this - I use emacs)

"sudo service gdm start"

---

