---
title: "xrandr questions"
date: 2013-06-06
forum: Hardware
---

### Post by LinuxUser666 on 2013-06-06
Hello fellow Ubuntu users. I am running Ubuntu 12.04 LTS with Xfce4 DE and I have few questions about xrandr.
1.Is it possible to make a mirror image with it?
2.If I do ```
ssh -X user@host
``` do I have to specify a display? for instance: ```
export DISPLAY=:0.0
```
3.Is it possible to use a similar command like ```
xrandr -o left
``` to just keep it rotating for instance left by 90 degrees?

Thank you, my regards.
):P

---

### Post by The Cog on 2013-06-06
> 1.Is it possible to make a mirror image with it?
Yes. "--reflect x" for instance. You can choose x, y or xy. See "man xrandr"

With ssh -X you do not need to specify the display - ssh sets up everything you need.

"-o left" sets a particular orientation. Repeating the command will **not** rotate it further.

You may be interested in the program **arandr** which is a GUI app that makes the more common settings of xrandr easier: sudo apt-get install arandr.

---

### Post by LinuxUser666 on 2013-06-06
Many thanks for your explanation, I found those infos very useful, did not know of arandr. 

My regards. :KS

---

