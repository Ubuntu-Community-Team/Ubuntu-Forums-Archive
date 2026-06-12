---
title: "Setting primary monitor on dual display"
date: 2011-07-10
forum: Hardware
---

### Post by gnomeout on 2011-07-10
Hi Folks,

I'll try to keep this simple. I have my desktop with a 22" monitor which is what I do my computing on. I also have a TV (40") to the left of my desktop. The only thing I ever want to do with the TV is play videos on it. It is not in a convenient place to look at when I am sitting at my desktop.

PROBLEM: I cannot seem to make my normal 22" right-hand monitor be recognized as the default one. The system seems to have a natural inbuilt preference for putting default behaviour/windows/panels in the left hand monitor(TV).

WHAT I TRIED: The System Settings->Monitors config window is pretty much useless for me. For a while I could not even get dual displays, it would only clone. Some online reading led me to use the Catalyst Control Center(CCC) (since I am using ATI HD4850). The CCC actually worked and I was able to reconfigure my monitors to have 2 separate displays. Originally it was reading my TV as monitor 1 and my actual monitor as monitor 2. It seems like the Unity launcher/panel is always in monitor 1, so to get around this, I switched where the monitors were plugged in, then swapped their orientation in the CCC. 

This gets me as close as possible, but there are still a few main issues that I just completely dont understand why they are happening. 

FIRST: the login screen is always on the left monitor no matter what, even after switching where they are plugged in and their orientation.

SECOND: for some reason my calendar/me-menu/logout button are all shifted offscreen on my primary right hand monitor. But all appear in full duplicated on the left hand monitor. (see attached pics, note that the right hand picture is not cropped, that is what actually appears on my screen)

THIRD: it also is making the left monitor my default desktop so new files saved appear there. and new windows and pretty much everything that ever appears, appears there. despite unity clearly being in my RIGHT hand monitor.

These last 2 issues are super annoying because my TV is off most of the time and they cause a major inconvenience when I am just computing.

Can someone tell me how to force ubuntu to use a particular monitor as the default for everything???

---

### Post by stony999 on 2011-07-13
I am using a script with xrandr for that, which I manually start from the menu. Take care of your resolutions!
```

#!/bin/sh
if [ "$1" != "off" ]; then
  # External Screen as HDMI, Laptop below
  echo "Dual Screen on"
  xrandr --output VGA1 --off  
  xrandr --output HDMI1 --primary --mode 1920x1200
  xrandr --output LVDS1 --off
  xrandr --output LVDS1 --mode 1680x945 --below HDMI1
else
  # External Screen off, Laptop primary
  echo "Dual Screen off"
  xrandr --output HDMI1 --off
  xrandr --output LVDS1 --primary --mode 1680x945
fi


```

---

### Post by dewdrop_world on 2011-07-16
Nice script, many thanks! I've just successfully moved my panels to the external monitor using it (and adjusting screen resolution etc.).

Beautiful!
James

---

### Post by w1n5t0n on 2011-07-25
Hi,

worked nice for me. I just wanted to ask, if you could give a short explanation about what the script does? I guess the key is the line in which the keyword --primary appears. This sets (e.g.) the HDMI channel as the primary monitor - right?

So if I have a monitor on the VGA port and one on the HDMI port i need to change it accordingly, such as:

```
xrandr --output HDMI1 --primary --mode 1680x1050
xrandr --output VGA1 --mode 1280x1024 --below HDMI1
```Is there any other way to change this, or maybe it would be a good idea to integrate this "Primary Monitor" into the Screen-Dialog that comes along with Ubuntu.

KR
Alex

---

### Post by pbpcservices on 2011-09-15
Guys,

Maybe you can help me with my frustration with my dual monitor issue. I am using Ubuntu 11.04 on my HP Compaq dc5750, with video card **[COLOR=Black]"[COLOR=Red]Integrated ATI Radeon X300 graphics with VGA and DVI-D[/COLOR][/COLOR]**[COLOR=Red]"[/COLOR]. The monitors show the same thing even though I unchecked "same image on all monitors". 

Please help.
Thanks,
pbpcservices

---

### Post by patrick12 on 2011-09-25
Perfect script!

I had to edit it a little bit to make it work but now it runs like a charm :)

```
#!/bin/sh
if [ "$1" != "off" ]; then
  # External Screen as HDMI, Laptop left
  echo "Dual Screen on"
  xrandr --output VGA1 --off  
  xrandr --output DFP1 --primary --mode 1920x1080
  xrandr --output LVDS --off
  xrandr --output LVDS --mode 1366x768 --left-of DFP1
else
  # External Screen off, Laptop primary
  echo "Dual Screen off"
  xrandr --output DFP1 --off
  xrandr --output LVDS --primary --mode 1366x768
fi
```

---

