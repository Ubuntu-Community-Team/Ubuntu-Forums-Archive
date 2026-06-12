---
title: "Monitor turning off - anyone else getting this?"
date: 2008-10-21
forum: General Help
---

### Post by Gallardo Spyder on 2008-10-21
I am getting a situation where my monitor will just go blank at random times.  I press any of the monitor buttons and it will come back (any adjustment keys or menu key).  It is not powered off - more in standby.


Specs:

I am running a Quad core desktop with 8.04.  It did this once before - early on in 8.04 (just a few times) but resolved itself somehow.

I have put in all the various no sleep, etc in the Xorg.conf, the power options are all set to turn off never (in power settings and config).  I made sure that laptop mode is off.

It is really not a timed thing - which would be easier to solve.  It could be 5 minutes or 4 hours.  It just goes blank/turns to standby), no out of range or anything from that standpoint.  It has happened with no activity and also when I am doing web browsing or open office...

I do the normal updates - not sure if an update is causing it or if it may be a bad monitor (3 months old Dell 22" hooked up with DVI).

Anyone have any thoughts on what it could be?

Thanks,
GSpyder

---

### Post by phidia on 2008-10-21
When it happens next open a terminal and enter > dmesg there might be helpful troubleshooting output there and/or check /var/log/xorg.log.

Actual you can check you log files either from System > Admin or by looking in /var/log because if this has been happening for a while chances are that it could be reported in the log files.

If it is the monitor going bad that probably won't show anything so if there is no logfile on the blackouts that suggests what you already suspect may be true.

---

### Post by Gallardo Spyder on 2008-10-22
> **phidia said:**
> When it happens next open a terminal and enter  there might be helpful troubleshooting output there and/or check /var/log/xorg.log.

Actual you can check you log files either from System > Admin or by looking in /var/log because if this has been happening for a while chances are that it could be reported in the log files.

If it is the monitor going bad that probably won't show anything so if there is no logfile on the blackouts that suggests what you already suspect may be true.

It has done it once since I posted this...  Checked the logs nothing revealing...

I have two systems with two monitors (side by side).  I just switched the monitors (not happening on my other Ubuntu system).  It happened with this other monitor as well.  So I am ruling out a monitor problem.

I am thinking it is something with Ubuntu on this box loosing connection with the monitor which is in autodetect mode (default with DVI hooked up).

The other monitor has two systems hooked to it - VGA and DVI and I can have it select which input it uses specifically rather than auto dectect.  I can't change the primary monitor just to use digital - due to only one system hooked to it.

So I wonder if it is loosing connectivity to the DVI.

Any other thoughts?

---

### Post by scouser73 on 2008-10-22
It sounds exactly like what happened to me when I had 7.10 installed, the monitor would switch to standby, I was told that all I needed to have done was move the mouse, and I had done that several times without the screen resuming. I'm unsure of a fix for this, but I just wanted to say that you're not the first to encounter it.  Thankfully in 8.04 and certainly in 8.10 things has drastically improved.

I also got told that it could have been my graphics card, that is was't fully inserted (it was)., perhaps you could check yours just to be on the safe side.

---

### Post by echo314 on 2008-11-03
I'm having similar problem. When booting up, right after progress bar finishes and it should go to login screen, monitor goes to standby and mouse / keyboard do not wake it up.

---

