---
title: "Hardy: suspend, backlight won't turn off."
date: 2008-05-01
forum: Hardware
---

### Post by saintdev on 2008-05-01
Hi, I've been using ubuntu for a while now because it was the only distro that would suspend (and hibernate) properly with my Dell Inspiron 8200. Ever other distro I've tried has had some problem (won't wake from suspend, won't hibernate properly, etc..) ubuntu was the only one that got it right. Sadly I just upgraded to Hardy and that is no longer the case. I now have the same problem as I did with SuSE. That is when I suspend my laptop, the backlight doesn't shut off. It suspends, and resumes just fine, but I'm faced with a bright white screen while it's supposed to be off. Every version of ubuntu up until Hardy has been fine. Hibernate works just fine, it's only suspend that presents this issue.

I have a GeForce 2 Go, and am NOT using the binary nVidia drivers. If anyone has any suggestions how to work-around this, or a fix, I would greatly appreciate it. I use suspend a lot, and this really makes it a no-go for me. If you need any more information, just let me know I'll be glad to post whatever you may need to help.

---

### Post by alphabeta23 on 2008-05-04
I have the same issue with a Dell C600 with a ATI Rage Mobility M3 graphic card. All Ubuntu versions until Hardy hibernated just fine...

Any help appreciated!

---

### Post by alphabeta23 on 2008-05-09
This problem is really annoying - has nobody an idea how to fix it?
Thanks in advance and with greetings from Berlin

---

### Post by Zorael on 2008-05-09
You could try the workaround mentioned over at [http://ubuntuforums.org/showpost.php?p=4907004](http://ubuntuforums.org/showpost.php?p=4907004). It didn't work on my laptop, but might work on yours.

Discussion at [http://ubuntuforums.org/showthread.php?t=784683](http://ubuntuforums.org/showthread.php?t=784683).

---

### Post by greenkid336600 on 2008-06-01
I have a similar problem with my Dell Inspiron 8200.  The backlight will not turn off no matter what.  I can adjust the brightness (but not turn off the backlight) when it is booted originally, and then when I resume from Suspend the backlight doesn't work at all (stuck off), but the screen does (as does the operating system - I can just barely make it out by using a flashlight.)

I have tried using the following methods:

$ sudo -s
# echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
# exit
([http://ubuntuforums.org/showpost.php?p=4907004](http://ubuntuforums.org/showpost.php?p=4907004))
returns:
bash: echo: write error: Invalid argument


xbacklight -set 0
([http://ubuntuforums.org/showthread.php?t=762628](http://ubuntuforums.org/showthread.php?t=762628))
returns:
No outputs have backlight property

xset dpms force off
([http://www.groupsrv.com/linux/post-670693.html](http://www.groupsrv.com/linux/post-670693.html))
returns:
[screen turns off, backlight still on]

---

### Post by saintdev on 2008-06-01
> **greenkid336600 said:**
> ...then when I resume from Suspend the backlight doesn't work at all (stuck off)

I used to have to deal with this with other distros when I would resume from suspend. Here's how I get around it.

1) Switch to a virtual terminal (Ctrl-Alt-F1)
2) Press the CRT/LCD switch a 2 or 3 times (Fn-F8)
- I think it's 2 times, but just stop when the screen comes back on.
3) Switch back to X (Alt-F7)

Not sure if this will work with all the video cards available for the 8200s, but it works for me.


@Zorael, The problem isn't that I can't adjust the backlight. That works just fine. The problem is after the computer has suspended, and everything is asleep the backlight is still on. Meaning I'm left with the backlight consuming power (and a bright white screen).

---

### Post by cellulararrest on 2009-04-30
I am still having this issue with Jaunty. I still haven't been able to find a good explanation. Are there any debug files I could checkout?

---

