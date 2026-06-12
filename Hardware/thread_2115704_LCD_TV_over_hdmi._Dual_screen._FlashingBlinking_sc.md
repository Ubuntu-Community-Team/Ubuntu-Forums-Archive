---
title: "LCD TV over hdmi. Dual screen. Flashing/Blinking screen when hdmi audio is on."
date: 2013-02-13
forum: Hardware
---

### Post by oblador on 2013-02-13
Hi,

When I connect hdmi cable from laptop to my LCD TV, the screen eventually blinks/flashes. It becomes intermitently on/off.

It only happens when I enable hdmi audio.

How could it be fixed?

PS: 
ubuntu 12.04
dell inspiron, 1525
intel 965

---

### Post by oblador on 2013-02-17
I tried the xorg edgers ppa, but the problem remains.

The screen is blinking when I plug the HDMI cable from laptop to TV and set the audio to HDMI audio.

Thanks.

I still wait for help.

---

### Post by Willyweasel on 2014-01-08
Your problem has already been solved here  [http://ubuntuforums.org/showthread.php?t=2045313](http://ubuntuforums.org/showthread.php?t=2045313)

All you have to do is

1. open a terminal
2. ```
sudo gedit /etc/pulse/default.pa
```
3. Type your password
4 Find this line
### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

5.Make it this
### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle

6.Logut or reboot

and yes I know this post is almost a year old, but I've been looking for a solution to this problem forever and just happened to stumble upon the solution above.

---

