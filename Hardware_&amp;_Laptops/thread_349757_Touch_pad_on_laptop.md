---
title: "Touch pad on laptop"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by randeffect on 2007-01-30
Hi everyone, I'm pretty new to linux and I've been doing good at figuring everything out by myself. Which I find surprising, haha. I just wanted to know if there was a way to turn of the tap to click on the touch pad of my laptop. It's pretty annoying opening a link or program when I only mean to move the mouse, or just having my program minimize when I'm typing because my hand accidently hit the touch pad.

---

### Post by pelagic on 2007-01-30
I've been asking the same question a while ago. Here is the answer I got:
[http://www.ubuntuforums.org/showthread.php?t=258281](http://www.ubuntuforums.org/showthread.php?t=258281)

/pelagic

---

### Post by randeffect on 2007-01-30
Thanks for the help I appreciate it

EDIT: MaxTapTime wasn't on there I guess I'll just deal with the touch pad.

---

### Post by sirozha on 2007-01-30
> **randeffect said:**
> Hi everyone, I'm pretty new to linux and I've been doing good at figuring everything out by myself. Which I find surprising, haha. I just wanted to know if there was a way to turn of the tap to click on the touch pad of my laptop. It's pretty annoying opening a link or program when I only mean to move the mouse, or just having my program minimize when I'm typing because my hand accidently hit the touch pad.

I'm in no way an expert in Linux, but having myself spent the entire weekend on this issue, I can share what I was able to do. 

1. I don't know if the Mouse utility that comes with Ubuntu controls your mouse pointer's speed. If it does, you can disregard steps  (2) and (3), but you may still want to follow them because you may gain extra control of your touchpad through gsynaptics.

2. Open xorg.conf (sudo gedit /etc/X11/xorg.conf), find the section that starts with

Section "InputDevice"
Identifier "Synaptics Touchpad" 

and add the following string:

Option "SHMConfig" "on"

mind you, I have an ALPS touchpad. So, if yours is Synaptics, you may not need to add the "SHMConfig" string to xorg.conf. You may want to first try the following step without it, and if it doesn't work, you can try to add it. 

3. Download and install gsynaptics (you can find it through the synaptics package manager). Don't confuse gsynaptics with synaptics -- those are two completely different things. 

4. Enable the "tap-off" feature. This is a very helpful feature that exists in the ALPS touchpad's Windows driver. It turns off touches as clicks while you are typing. Last time I checked, this feature didn't exist in the Synaptics Windows driver, which renders the Synaptics touchpad almost unusable. Go to the terminal window and type the following:
syndaemon -t -d -i 1

(Explanations). This daemon disables your touchpad's ability to use taps as clicks. The parameters have the following meaning:

-t -- disable touch as click
-d -- run as a daemon
-i -- sets interval between the last key stroke and the first tap that registers as a click. The default interval is 2 sec. If you want to make it shorter, use "-i 1" just like in the command above. If you don't want your touch pad to ever use touches as clicks, don't use the "i" parameter at all. 

You can even monitor how syndaemon disables and re-enables the touchpad's ability to use touches as clicks. If you just type syndaemon at the command prompt (after you have issued the command above), and then start typing, you will see that syndaemon will be reporting "disable" and "enable" modes. 

5. Final step. In order for syndaemon to run every time you restart your laptop, go to System -> Preferences -> Sessions, then click on the "Startup Programs" tab, then click on "Add" and add the same command line as you did in the beginning of step 4 (i.e. syndaemon -t -d -i 1) or whatever value you want to assign to the i" parameter if any. 

Hope this will help you avoid wasting hours on this project.

---

### Post by mastergunner on 2007-08-26
.....

---

### Post by t2000kw on 2007-08-26
I've tried doing this, installing TPConfig, installing gsynaptics, putting the syndaemon -t -d -i 1 comand in startup, all to no avail. 

When I run gsynaptics I get a message about shared memory and also that I need to be sure that I have:
Option "SHMConfig" "true"  (as opposed to "on")

I've tried it with "on" and "true" and it doesn't seem to matter at all. 

Any ideas here?

I'm getting a bit tired of typing text and it ending up in the middle of a paragraph a few lines above where it's supposed to be, or closing windows or other strange behavior due to the touchpad thihking I'm wanting to do somethign other than type text.

We're supposed to be able to configure the touchpad not only to ignore taps for x number of seconds but also to use the scrolling regions, using gsynaptics. I haven't tried Ksynaptics but I would guess it's similar.

---

### Post by t2000kw on 2007-08-26
I managed to get the syndaemon working but not gsynaptics. Then, on a hunch, I wondered if syndaemon was working, maybe things were finally in place for gsynaptics to work. So I reinstalled it from my deb file I made from an RPM package. It worked. (Gsynaptics is not available in Synaptics in Dapper, the version I use on the laptop due to problems with USB scanners in Feisty.)

---

