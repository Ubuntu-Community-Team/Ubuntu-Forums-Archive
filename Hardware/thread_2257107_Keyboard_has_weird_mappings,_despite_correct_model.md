---
title: "Keyboard has weird mappings, despite correct model &amp; country selected"
date: 2014-12-16
forum: Hardware
---

### Post by Evan_Charlton on 2014-12-16
Hi all!

**The problem:**
My keyboard (wired microsoft natural ergonomic keyboard 4000) has weird mappings now, and I have no idea why. For example:
[LIST]
[*]right-alt = z
[LIST]
[*]z continues to work, though z-space results in the context menu appearing
[/LIST]

[*]p = ~p
[LIST]
[*]But only in gnome-terminal (!)
[/LIST]

[*]numpad-7 gives me the context menu
[LIST]
[*]All other numpad buttons work fine
[/LIST]
[/LIST]
And so on like that; just bizarre behavior

**What I did:**
As far as I can tell, all I did to cause this was boot my machine. It seemingly came out of nowhere. I've used this same setup for years, on multiple machines, and never had a problem.

**What I've done:**
Searched around, not finding much. I did see this message in my /var/log/syslog:
[FONT=courier new]syslog.1:Dec 11 18:44:41 evan-desktop kernel: [    2.916005] systemd-udevd[464]: Error calling EVIOCSKEYCODE: Invalid argument[/FONT]
which lead me to here:
[http://ubuntuforums.org/showthread.php?t=2250210](http://ubuntuforums.org/showthread.php?t=2250210)
which wasn't much help :-(

**Logs:**
In the log below, I run `sudo evtest`, point it to my keyboard (there are two entries?), press <return>, <p>, <right-alt>, <numpad-7>, and then terminate with <ctrl-c>.
```

Testing ... (interrupt to exit)
Event: time 1418791099.666304, type 17 (EV_LED), code 0 (LED_NUML), value 0
Event: time 1418791099.666304, -------------- SYN_REPORT ------------
Event: time 1418791099.771160, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70028
Event: time 1418791099.771160, type 1 (EV_KEY), code 28 (KEY_ENTER), value 0
Event: time 1418791099.771160, -------------- SYN_REPORT ------------
Event: time 1418791107.323198, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70040
Event: time 1418791107.323198, type 1 (EV_KEY), code 65 (KEY_F7), value 1
Event: time 1418791107.323198, -------------- SYN_REPORT ------------
^[[18~Event: time 1418791107.331171, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70013
Event: time 1418791107.331171, type 1 (EV_KEY), code 25 (KEY_P), value 1
Event: time 1418791107.331171, -------------- SYN_REPORT ------------
pEvent: time 1418791107.435222, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70040
Event: time 1418791107.435222, type 1 (EV_KEY), code 65 (KEY_F7), value 0
Event: time 1418791107.435222, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70013
Event: time 1418791107.435222, type 1 (EV_KEY), code 25 (KEY_P), value 0
Event: time 1418791107.435222, -------------- SYN_REPORT ------------
Event: time 1418791111.283220, type 4 (EV_MSC), code 4 (MSC_SCAN), value 7001d
Event: time 1418791111.283220, type 1 (EV_KEY), code 44 (KEY_Z), value 1
Event: time 1418791111.283220, -------------- SYN_REPORT ------------
zEvent: time 1418791111.291215, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1418791111.291215, type 1 (EV_KEY), code 100 (KEY_RIGHTALT), value 1
Event: time 1418791111.291215, -------------- SYN_REPORT ------------
Event: time 1418791111.411174, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1418791111.411174, type 1 (EV_KEY), code 100 (KEY_RIGHTALT), value 0
Event: time 1418791111.411174, type 4 (EV_MSC), code 4 (MSC_SCAN), value 7001d
Event: time 1418791111.411174, type 1 (EV_KEY), code 44 (KEY_Z), value 0
Event: time 1418791111.411174, -------------- SYN_REPORT ------------
Event: time 1418791113.779165, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70065
Event: time 1418791113.779165, type 1 (EV_KEY), code 127 (KEY_COMPOSE), value 1
Event: time 1418791113.779165, -------------- SYN_REPORT ------------
Event: time 1418791113.787169, type 4 (EV_MSC), code 4 (MSC_SCAN), value 7005f
Event: time 1418791113.787169, type 1 (EV_KEY), code 71 (KEY_KP7), value 1
Event: time 1418791113.787169, -------------- SYN_REPORT ------------
Event: time 1418791113.915165, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70065
Event: time 1418791113.915165, type 1 (EV_KEY), code 127 (KEY_COMPOSE), value 0
Event: time 1418791113.915165, type 4 (EV_MSC), code 4 (MSC_SCAN), value 7005f
Event: time 1418791113.915165, type 1 (EV_KEY), code 71 (KEY_KP7), value 0
Event: time 1418791113.915165, -------------- SYN_REPORT ------------
Event: time 1418791117.779216, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e0
Event: time 1418791117.779216, type 1 (EV_KEY), code 29 (KEY_LEFTCTRL), value 1
Event: time 1418791117.779216, -------------- SYN_REPORT ------------
Event: time 1418791117.851173, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70006
Event: time 1418791117.851173, type 1 (EV_KEY), code 46 (KEY_C), value 1
Event: time 1418791117.851173, -------------- SYN_REPORT ------------




```

**More info:**
I have a laptop also running 14.04.1 LTS, and this *does not* reproduce on that machine, so I'm 99% sure it's not defective hardware.

I'm happy to provide any logs you need.

---

