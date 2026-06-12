---
title: "gnome-settings-daemon crashing in Intrepid"
date: 2008-11-24
forum: General Help
---

### Post by upallnight on 2008-11-24
I just did a fresh install of Intrepid and then updated everything.

I've been noticing the gnome-settings-daemon crashing anywhere from every minute to every hour and it seems to be random.

Anyone else experiencing this? You can tell when it happens because your Theme is reverted back to a blue blocky one.

I want to find some logs from this daemon so I can check for error messages.

---

### Post by Anessen on 2008-11-24
I am having almost exactly the same problem since I downloaded some updates a couple of days ago.

It looks like gnome-settings-daemon either doesn't start at all for me or crashes instantly in about 1 in 2 times I start the computer. It will log in with a default theme, an when I go to the appearance box it complains that the daemon isn't running.

When I run it in the background from a terminal, the theme gets restored and everything is OK.

I haven't had it crash after it has successfully started though.

This is since a set of update about 3-4 days ago, there was no problem before then.

I am not running Compiz. I have a modified industrial theme using different combinations of default icons, fonts and other appearance options. There are no "third party" appearance parts being used, its just a combination of default ones.

---

### Post by caleb12 on 2008-11-24
I had this problem a few weeks ago, it was related to a file that had been updated... that the settings manager didn't like; hopefully it helps... here's the thread:

[http://ubuntuforums.org/showthread.php?t=955679](http://ubuntuforums.org/showthread.php?t=955679)

Although, it seems to me that this issue was fixed in a few days by another release... So, there's a good chance this isn't the cause.

After it crashes try launching it from the command line and pay attention to the output, see if there's an error message available at least that will get you going in the right direction...

---

### Post by upallnight on 2008-11-24
After gnome-settings-daemon crashes, I launch it from a terminal and it goes to the background without any output.

Anyone know where gnome-settings-daemon writes its logs?

---

### Post by caleb12 on 2008-11-24
I don't know of any logs, the only output I've ever seen is on the console after restarting the manager at a command line. That's kind of creepy that it doesn't give out an output, I mean even when it's working properly it spits out something... 

It could be caused by a corrupt settings file, maybe under ~/.gnome2/session - who knows, maybe try creating a new user and logging in as that. Then try to get the manager to crash, at least you'd know if it's user specific or system wide that way.

---

