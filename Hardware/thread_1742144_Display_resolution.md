---
title: "Display resolution"
date: 2011-04-28
forum: Hardware
---

### Post by arunas.smaliukas on 2011-04-28
Hi guys,

this is **first time** I'm asking for help :) So the problem:

I think something is wrong with my monitor (BENQ FP767), and when I install Ubuntu, the resolution is too small - 1024x768 (I need 1280x1024). I have been using Ubuntu many years and there was no problems, now i have tried Ubuntu 10.10 10.04 11.04 and the same problem - "Monitor not detected".

**Interesting** **thing**
I have tried Debian, and there everything is fine.
Next, I have tried Mint (Ubuntu edition) - "Monitor not detected"
Mint (Debian edition) - everything is fine (Monitor is detected - he knows it is FP767)

**Results**
Now I have installed two Distributions: Ubuntu 11.04 (Monitor **not** detected), Linux Mint Debian Edition (Monitor **detected**).

[B]My solution
[/B]My idea is somehow copy drivers or whatever from Mint to Ubuntu.
I tried to copy /etc/X11 but it doesn't work... I found that in one of file (in /etc/X11) is written "/usr/bin/gdm3" in Mint, and in Ubuntu in the same file is written "/usr/bin/gdm", and I see that in Ubuntu there is no file /usr/bin/gdm3, and I have no idea what it is for....... I have tried more similar combinations, but my plan is dead..

[B]What help do I need
1) [/B]someone, please, say how to copy "video drivers" from Mint(Debian) to Ubuntu
**2) **or say how to force my resolution. My graphics card is nvidia, but i think i'm not using nvidia drivers, becouse there is no /etc/X11/xorg.conf file (where I think is possible to force resolution), but i remember i was trying this way in Ubuntu 10.10, and that didn't work..
**3)** any other ideas..

Thanks for a help,..
Ar&#363;nas

---

### Post by arunas.smaliukas on 2011-04-29
Or send me, please, some useful links...

P.S. I can give to control my PC :)) if anybody could help

---

### Post by InphekD on 2011-04-29
I don't think you can do that.

My suggestion: Try setting nomodeset option and see if it helps.

```
gksudo gedit /etc/default/grub
```Find

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Add nomodeset at the end. Should look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```In terminal write:

```
sudo update-grub
```Restart.

Detailed instructions: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

