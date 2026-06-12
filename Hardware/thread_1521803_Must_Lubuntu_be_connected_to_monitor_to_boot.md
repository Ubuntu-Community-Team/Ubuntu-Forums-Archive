---
title: "Must Lubuntu be connected to monitor to boot?"
date: 2010-07-01
forum: Hardware
---

### Post by theviking10 on 2010-07-01
Hello! I set up an old desktop with Lubuntu and I'm attempting to use it as a digital juke box, and am managing it via vnc.

However, whenever I attempt to boot the desktop without a monitor (that is, with only ethernet and speakers) it does not show up on my network. However, once I connect a monitor to investigate, it boots and appears. I can then access it without issue.

So my question is, is the monitor needed for lubuntu to access the internet? If so, how can I work around this?

Thank you.

---

### Post by kerry_s on 2010-07-01
have checked your bios? there usually set to not start without monitor, keyboard, mouse.

for instance mine says something like "error on all but", i have to change that to none

---

### Post by dfreer on 2010-07-01
If I recall correctly, the X server will not start up if it can't detect a monitor/keyboard/mouse. Googling shows a few fixes for getting it to ignore the absense of a mouse and/or keyboard, but I don't know about running without a monitor.

And VNC likely requires X to be running in order to run itself. You should be able to use other network services though, like SSH.

---

### Post by theviking10 on 2010-07-02
Thank you all. I will be tinkering more today, first with bios and then SSH.

---

### Post by theviking10 on 2010-07-02
Well, upon further inspection it does not seem to be a BIOS issue. I am very sure it is, in fact, the problem of X not starting.

I have attempted to integrate "startx" and "service lxdm start" into a few of the startup scripts, but to no avail. 


So far, my best bet seems to be editing /etc/xdg/lxsession/Lubuntu/autostart to start X, but I have also tried in ~/.profile. 

Any ideas? Maybe the issue is within "startx" itself. Where does X detect the presence of a monitor?

---

