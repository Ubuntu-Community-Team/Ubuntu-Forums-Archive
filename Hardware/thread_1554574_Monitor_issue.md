---
title: "Monitor issue"
date: 2010-08-16
forum: Hardware
---

### Post by Beta.v.2 on 2010-08-16
I'm on a laptop and the bezel for the monitor started to fall apart. I figured since it was going to fall apart by itself anyway, why don't I remove the bezel+monitor? So I did that and here's the problem. Before all the problems with my monitor occurred I could plug-in my external monitor and when I turned on Ubuntu it would say "Unsupported Mode" (on the external monitor) and the regular monitor would display fine. After I log in the external monitor starts working, other than the fact that it's a little fuzzy. But, I can fix that problem by turning the screen off and back on (via System>Preferences>Monitor). After all the problems with my laptop monitor, and after I removed the monitor this is what happened. I started my laptop up like normal and it gave me the "Unsupported Mode" error. That doesn't bug me b/c I can log into my screen without seeing anything. After I log in the screen is supposed to display right, just the normal fuzziness, but this time it kept the "Unsupported Mode" error. I tried doing the following:
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
Didn't work.

I also tried doing stuff w/ xrandr, but anything I do with that tells me "Cannot Open Display".

I also tried going into low graphics mode. This worked until I went into System>Preference>Monitors and saw that it said that the monitor that was plugged in was "Unkown". Usually it says "TVW 19""

Here's the twist, I can turn on Ubuntu, plug my laptop monitor in, and everything works. Then I can unplug it with the system still turned on and it still works. I don't understand what the problem is.

---

### Post by Fafler on 2010-08-17
Try making a Xorg.conf that only uses the secondary display. I've done that in the past with great success.

---

### Post by Beta.v.2 on 2010-08-17
> **Fafler said:**
> Try making a Xorg.conf that only uses the secondary display. I've done that in the past with great success.
How would I go about doing that?

---

