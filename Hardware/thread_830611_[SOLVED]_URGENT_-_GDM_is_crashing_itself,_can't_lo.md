---
title: "[SOLVED] URGENT - GDM is crashing itself, can't log in! Managed to get to terminal th"
date: 2008-06-16
forum: Hardware
---

### Post by rainwalker on 2008-06-16
The login screen is crashing before I can do anything, and then it keeps crashing when it tries to restart!

[COLOR="DarkOrange"]**SOLVED: I ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to set it back at defaults, and that fixed things!**[/COLOR]

Background:
I've had an issue for the past week or so where I would have to log in twice; the first time it would show me this:
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/IMG_3510-2.jpg[/IMG]
and then kick me back to the login screen, after which I could successfully log in. I didn't think much of it, but now something is SERIOUSLY wrong.

I changed my GDM theme earlier and logged out to see it, and that same thing happened. I changed it again and logged out, but this time when the login screen tried to load it crashed, showing me that above text again. It would immediately try to reload, and promptly crash just like before. This repeats a few times before a message pops up telling me the greeter application is crashing (duh!) and is going to try and start an alternative one. That won't work, though, because there is no alternative...so it enters the cycle of crashing again.
However, I've managed to Alt + F4 into a virtual terminal and log in, then start X with the "startx" command. Usually it kicks me off after a minute or two, though, but I think I've fixed that with "sudo killall Xorg" before starting X.

Please help, something is seriously wrong here! I haven't messed with anything significant lately, aside from following this guide: [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by rainwalker on 2008-06-16
UPDATE: I booted into recovery mode and in a root terminal did ```
dpkg-reconfigure gdm
``` and got this: >      * Reloading GNOME Display Manager configuration...
     * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

What do I do?

---

### Post by Odrodzona-Sarmacja on 2008-06-16
I dont know if this issue shows up with onely one bug, but... I got error in the same place when I messed up my /boot/grub/menu.lst

I had like root=/dev/hdaX instead of root=/dev/sdaX.

Also when you wait for 5 minutes after seeing this message there is comming a short message about what exactly error it is, so you can fix it. Or at least it was in my case.

However I guess it is something else malfunctioning in your case. Can you find any gdm error messages in /var/log/syslog? Maybe that could help you.

---

### Post by rainwalker on 2008-06-16
I do remember doing something with my menu.lst...I don't remember what, though.

It never told me exactly what was going wrong, which was why i was so worried. Apparently reconfiguring X did the trick, though.

I'll check that log, thanks :)

---

