---
title: "eDP detected as Primary Display even though only HDMI is connected."
date: 2020-06-03
forum: Hardware
---

### Post by cpaljchc on 2020-06-03
MotherBoard: ASRock NUC-8265U
OS: Ubuntu 19.04
Monitor: ASUS VP247H
Problem:
Every time when I boot up Ubuntu 19.04, an eDP-1 is detected as Primary monitor even though there is only one monitor connected to the system through DP-1.
However, it is stated that there is no eDP port in the manual as shown in the below screenshot.
[ATTACH=CONFIG]286081[/ATTACH]
I have to keep adjust to the secondary display in order to show icons, taskbar, and desktop properly every time when the system is reboot.See following screenshot:
[ATTACH=CONFIG]286079[/ATTACH]

Left is Secondary display which is the monitor connected to the system; Right is Primary display - eDP detected.


I have tested with Ubuntu 18.04, 19.04 and 20.04 and this symptom will occur. However, it works fine when I tried testing with earlier version of Ubuntu 16.04 and Windows 10 Pro. I have tried some of the xrandr commands found on this forum, but there is no quick fix to it.
The following screenshot is the xrandr result, it states that eDP-1 is connected as Primary Disply while HDMI and DP are disconnected. In this screenshot, the monitor is connected to the HDMI port.
[ATTACH=CONFIG]286080[/ATTACH]
I am wondering why DP signal is being detected by the later versions of Ubuntu and if there is any fix to this problem?
Thanks in advance.

---

### Post by cpaljchc on 2020-06-23
Hi,

Does anyone has any idea to solve this problem?Please.
Thanks you.

---

### Post by CelticWarrior on 2020-06-23
The problem is likely related to UEFI settings. Some firmwares enabled a sort of virtual display.

That said and knowing the problem likely will persist with a newer release, even so you mustn't keep using 19.04 because it's out of support. Please install a supported release, current is 20.04 LTS, and come back here if the problem persists.

---

### Post by siepo on 2020-06-23
You can define the arrangement of your monitors for the login screen in stanzas in /etc/X11/xorg.conf, or in e.g. a file /etc/X11/xorg.conf.d/10-monitor.conf:
```

Section "Monitor"
  Identifier  "DP-1"
  Option      "Position" "0 0"
EndSection

Section "Monitor"
  Identifier  "DP-2"
  Option      "Position" "0 0"
EndSection

```
In your case, you could create sections for eDP-1 and HDMI-1. These sections tell X11 to display the same content on each display.

---

### Post by TheFu on 2020-06-23
19.04 support ended in January.  Well passed time to move. 

At this point, **20.04 is the answer.** 19.10 has only 1 month of support remaining, so it isn't worth installing.

As for the monitors, I've never used anything except a full xorg.conf file, so can't say whether just adding a monitors stanza is sufficient or not. These things are very unique to a system and my highly customized settings could break other people X11 completely.

The correct directory is: /etc/X11/xorg.conf.d/  Inside there, begin the filename with a number - and end the filename with .conf and those settings should be picked up my the xorg processing. As siepo wrote above, /etc/X11/xorg.conf.d/10-monitor.conf would be find.

Whenever posting data here, please use plain text, not images, unless the image is germane to the issue. 800 bytes easily replaces 12KB images.

---

### Post by cpaljchc on 2020-07-02
Thank you for your answers,

I will try and see if it works.
I will be aware to not posting images if not necessary next time.

---

