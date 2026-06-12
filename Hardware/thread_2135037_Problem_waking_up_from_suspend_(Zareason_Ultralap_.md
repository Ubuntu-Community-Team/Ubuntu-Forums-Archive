---
title: "Problem waking up from suspend (Zareason Ultralap 430) and gnome shell freezing."
date: 2013-04-13
forum: Hardware
---

### Post by Reding on 2013-04-13
Hey everyody,

I'm posting here to share my problem on waking up the computer from suspend. It's been few days now that i can't wake up from Suspend anymore, and that suddenly, without changing anything in the settings. I've just made a couple of updates through the Software Center but that's it, I don't think it has a relation though.

I'm on a Zareason Ultralap 430. The computer does go to suspend (blinking light on the side of computer testifying it's suspended) but whatever the button i press on the keyboard it just shutdown.

Any ideas ? I couldn't find any valuable infos to solve my problem in previous threads, any help would be appreciated !

Ps: I experience quite a lot of freezes as well on gnome shell 3.6 especially when going to the Activites button, the system gets stucked without any possibility of getting out of it (reassigned, ctrl-alt-delete to open the system monitor but doesn't seem to do the trick ; can't open the terminal either (attempting to use kill all - name of the programm)

Thanks in advance :)

Red

---

### Post by Reding on 2013-04-13
Nobody can help me ? Come on :) Up !

---

### Post by SilverTungsten on 2013-04-14
A couple of things.  First, don't use hibernate aor sleep modes.  When you are not actively using the machine, just shut it down.  What happens (even in Windoze) is that your file system gets corrupted.  So, that said, now to clean up your file system.  Run "sudo touch /forcefsck" then reboot your machine.

---

### Post by Reding on 2013-04-15
I've done the system cleaning, hasn't changed anything so far. Didn't seem to find anything corrupted either.

So far, I still can't resume from suspend.

---

