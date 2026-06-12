---
title: "Defective display: some questions about the resulting errors"
date: 2024-11-27
forum: Hardware
---

### Post by freedom1984 on 2024-11-27
Good morning! As you already know, I have problems with my Thinkpad, which I'll put aside here. Due to other bugs on my HP Bang Olufsen Elitebook (time & date was often set to April 16 at 16:20, I couldn't get on the internet), I smashed it completely. Well, at least the screen. I thought the PC was broken, but got the idea to plug in an external screen today. Sure enough, it connected automatically. Unfortunately, it didn't mirror it, but expanded it, which is why it now “jumps”. I can't manage to set the settings to “mirror” in the settings in time. It jumps back every time and then I have to start all over again and can't do it. I tried it via the terminal: 

```
xrandr --output eDP-1 --same-as HDMI-1
``` Even with the resolution 1920x1080 in the center.It did not work.Without resolution I had problems with the parameters.With resolution it did not find eDP-1, although xrandr clearly spits out eDP-1 as the name (next to HDMI-1).I could now imagine that it does not find it, as it actually no longer exists (it is broken).Can I switch it off with the terminal without hesitation?But it can no longer find it.So I tried to set the external one as primary:

```
xrandr --output HDMI-1 --primary
```Unfortunately, the screen still “jumps”.So I tried switching off the internal screen:

```
xrandr --output eDP-1 --off
```The following error appears:

```
X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 140 (RANDR)
Minor opcode of failed request: 7 (RRSetScreenSize)
Serial numer of failed request: 28
Current serial number in output stream: 29
```I tried that too:
```

sudo nano /etc/X11/xorg.conf
```
 And then:

```
Section "Device"
    Identifier  "Configured Video Device"
    Option      "IgnoreDisplayDevices" "eDP-1"
EndSection

```

But I must have made some kind of mistake (red arrow with 1x appeared in the terminal)

At this point I would be open to suggestions, hahaha!

---

### Post by Yellow Pasque on 2024-11-27
What model Elitebook? You don't have hotkeys or function keys to control the display?

---

