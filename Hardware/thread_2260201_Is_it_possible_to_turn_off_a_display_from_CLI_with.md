---
title: "Is it possible to turn off a display from CLI without x server installed?"
date: 2015-01-09
forum: Hardware
---

### Post by Irrationalis on 2015-01-09
I have an iMac (Ubuntu Precise Pangolin 12.04.5 LTS) I am using as a Plex Media Server. It is in the corner, but the display is annoying when the room is dark. Is it possible to be able to blank or turn off the display from the command line on a CLI only install? This would need to be added to a startup script, so it would invoke at startup.

---

### Post by TheFu on 2015-01-10
Disable:
> 
#!/bin/sh
export DISPLAY=:0
xset s off &
xset -dpms &


Enable:
> 
#!/bin/sh
sleep 7200 
export DISPLAY=:0
xset s on &
xset +dpms &

I have sleep enabled for 2 hours ... that way it is off when I fall asleep when traveling with a laptop.
Almost forgot - set DISPLAY to be :0.

At home, I just turn off the tv when listening to music. Works well enough.

---

### Post by efflandt on 2015-01-10
Following is in /etc/kbd/config to automatically blank a text console screen after a time. However, if your display is an HDTV (instead of a monitor) it might not do dpms (go to sleep), unless some period of time after it loses a signal it goes into its own screensaver mode or shuts down on its own. One early HDTV ready TV I have nevery shuts down if it loses a signal, it just eventually blue screens at full power forever. The 32" HDTV I am currently using as a monitor goes into a screensaver mode shortly after losing video signal and goes into standby (electronically off) 10 minutes after that. But while leaving the computer while leaving it on, I simply use the TV remote to turn the screen off. Note that in some cases with HDMI CEC, switching inputs on a TV used as monitor or turning off the TV with the remote might tell Linux to shut down [http://elinux.org/CEC_%28Consumer_Electronics_Control%29_over_HDMI](http://elinux.org/CEC_%28Consumer_Electronics_Control%29_over_HDMI)

```
#  **** screen saver/DPMS settings: all VCs ****
# These settings are commented by default to avoid the chance of damage to
# very old monitors that don't support DPMS signalling.

# screen blanking timeout.  monitor remains on, but the screen is cleared to
# range: 0-60 min (0==never)  kernels I've looked at default to 10 minutes.
# (see linux/drivers/char/console.c)
BLANK_TIME=30

# blanking method (VESA DPMS mode to use after BLANK_TIME, before powerdown):
# on: the default, no DPMS signalling. near instant powerup, no power saving
# vsync: DPMS Standby mode. nearly instant recovery, uses 110/120W (17" screen)
# hsync: DPMS Suspend mode. typically 3s recovery, uses 15/120W (17" screen)
# powerdown,off: DPMS Off mode, typ. 10s recovery, uses  5/120W (17" screen)

# Those values are for my 17" Mag, but some monitors do suspend the same as
# standby.  xset dpms force {off|standby|suspend|on} is useful for this, if X
# supports DPMS on your video card.  Set X's DPMS screensaver with xset dpms
# or use option power_saver in XF86Config
#
# DPMS set by default to on, because hsync can cause problems on certain
# hardware, such as Armada E500 laptops
BLANK_DPMS=off

# Powerdown time.  The console will go to DPMS Off mode POWERDOWN_TIME
# minutes _after_ blanking.  (POWERDOWN_TIME + BLANK_TIME after the last input)
POWERDOWN_TIME=30
```

Different distro, but this shows examples for X or terminal: [https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling](https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling)

For text consoles see "man setterm". I was able to get that to blank the screen. but not power it down (maybe needs sudo). But the following worked (my HDTV showed its screensaver for loss of signal) and wakes screen with any keypress (source [http://askubuntu.com/questions/62858/turn-off-monitor-using-command-line](http://askubuntu.com/questions/62858/turn-off-monitor-using-command-line) ):```
sudo sh -c 'vbetool dpms off; read ans; vbetool dpms on'
```

---

### Post by Irrationalis on 2015-01-10
Perfect!
After adding that line (minus the "keypress for on" stuff) to /etc/rc.local, the display is now blanking at boot, thanks efflandt!

---

### Post by TheFu on 2015-01-10
The x-whatever commands are almost always X/Windows and require an X/Server.  I assumed you had one, but didn't know it. I was wrong.  My Plex Server runs on the same box I run XBMC with PlexBMC on, so it has X.

Just wanted to clarify for any future lurkers.

---

