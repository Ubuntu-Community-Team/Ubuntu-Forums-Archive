---
title: "Suspend &amp; Hibernate don't work in 9.04"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2009-04-23
Hey guys!

I have a HP 550 Laptop.

I upgraded my 8.10 install to 9.04 a few days ago (got all current updates available at time of posting!)

I'm liking 9.04 a lot; boot time is a sec or 2 faster (always good!) notifications are good too. The only problem is that suspend and hibernate don't work.

In 8.10 they both worked perfectly bun in 9.04 they just go to the log in screen and don't power down. (which is just leaving the laptop on at full power!).

I'm having to shutdown the laptop every time I'm going away for a period instead of just suspending the session.

Is their anything i can check (in case a setting has been flipped during upgrade).
If you need more info ask and i'll post it...

Also side question....
What should the "System Testing" program do? i've ran it once and it justs sits in the bar minimized for 20 seconds then it disappears. should their be user interaction?

---

### Post by Sanitarium on 2009-04-25
I am having a similar problem. When I go to hibernate, the PC looks like it goes to hibernate, and its not using any power. So that part is fine.

The problem is when I turn the PC back on. It goes to the screen where it asks you for the password, and it accepts it, and then I get a screen where it is just my wallpaper, as if it has gone to the desktop and nothing has loaded. Restarting X doesn't work either.

---

### Post by solitaire on 2009-04-25
Well all "Suspend" and "Hibernate" does do on my laptop is log me out! :(

You're at least getting some of the services to shut down, or not to restart properly!

Anyone got any ideas?
I'm killing my "green" credentials keeping this laptop on all the time!! :D

---

### Post by sttal on 2009-04-25
I have a similar problem! in the menu it only shows the shutdown and restart options.

---

### Post by saf-t scissors on 2009-04-25
Same here. Suspend works fine, but hibernate saves the current session to disk and kicks me back to the user login prompt. I'd rather it just save the state to disk and shut down, but can't find settings to control this.

This is a Dell Inspiron 700m, FWIW.

---

### Post by solitaire on 2009-04-28
*Bump*

Anyone got any ideas?

---

### Post by nortexoid on 2009-04-29
Is your swap partition large enough to accommodate hibernation? If not, it will kick you back to the desktop.

One unfortunate thing about the installation process is that it does not warn you that, in order to use hibernate, your swap partition (or file, if that's what you use) has to be large enough to store the hibernate information, plus whatever is currently being used by the system on swap at the time of attempted hibernation.

In theory there is a way of setting up a swap file after an installation that does not reside on the swap partition (or it might, if you wanted) and to tell hibernate to store the information in that file. I don't know how it's done. Anyone? More information is here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by solitaire on 2009-04-29
I've 1Gb swap (1Gb ram in system as well)

The same happens for Suspend as well as Hibernate (BOTH worked in 8.10). So i don't think it's an issue with my swap drive size.

---

### Post by saf-t scissors on 2009-05-01
> **nortexoid said:**
> Is your swap partition large enough to accommodate hibernation? If not, it will kick you back to the desktop.

I'm not sure that's the same issue. It's not kicking me back to the desktop, it successfully saves state, then puts me back at the login prompt. If I shut down from there, I can boot up later and it reloads the previous state. It's just not shutting down automatically.

---

### Post by zoniq on 2009-05-03
Same problem here. Suspend/Sleep just locks the screen, but doesn't actually do anything else. It worked perfectly in 8.10

EDIT: I justed ran 'pm-suspend' manually instead from the KDE energy widget. There it works. So at least for me it seems to be a problem with the KDE widget.

---

### Post by solitaire on 2009-05-03
Their are some entries in the log files every time i run the "pm-suspend" command
Nothing happens except for these log entries.:

Auth.log
```
May  3 22:51:08 Europa sudo:     bill : TTY=pts/0 ; PWD=/home/bill ; USER=root ; COMMAND=/usr/sbin/pm-suspend
May  3 22:51:08 Europa dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=3797 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.269" (uid=0 pid=4265 comm="hal-get-property --udi /org/freedesktop/Hal/device"))
May  3 22:51:08 Europa dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=3797 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.270" (uid=0 pid=4293 comm="lshal "))
May  3 22:51:08 Europa dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=3797 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.271" (uid=0 pid=4307 comm="hal-get-property --udi /org/freedesktop/Hal/device"))
May  3 22:51:08 Europa sudo:     bill : TTY=unknown ; PWD=/home/bill ; USER=bill ; COMMAND=/usr/bin/pactl suspend-sink 1
May  3 22:51:08 Europa sudo:     bill : TTY=unknown ; PWD=/home/bill ; USER=bill ; COMMAND=/usr/bin/pactl suspend-source 1
May  3 22:51:08 Europa sudo:     bill : TTY=unknown ; PWD=/home/bill ; USER=bill ; COMMAND=/usr/bin/pactl suspend-sink 0
May  3 22:51:08 Europa sudo:     bill : TTY=unknown ; PWD=/home/bill ; USER=bill ; COMMAND=/usr/bin/pactl suspend-source 0
May  3 22:51:08 Europa dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=3797 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.272" (uid=0 pid=4372 comm="hal-get-property --udi /org/freedesktop/Hal/device"))

```kern.log
```
May  3 22:51:08 Europa kernel: [29384.472503] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.472708] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.696103] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.696223] CPU0 attaching NULL sched-domain. 
```debug.log
```
May  3 22:51:08 Europa kernel: [29384.472503] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.472708] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.696103] CPU0 attaching NULL sched-domain.
 
```syslog.log
```
May  3 22:51:08 Europa anacron[4343]: Anacron 2.3 started on 2009-05-03
May  3 22:51:08 Europa anacron[4343]: Normal exit (0 jobs run)
May  3 22:51:08 Europa kernel: [29384.472503] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.472708] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa anacron[4412]: Anacron 2.3 started on 2009-05-03
May  3 22:51:08 Europa anacron[4412]: Normal exit (0 jobs run)
May  3 22:51:08 Europa kernel: [29384.696103] CPU0 attaching NULL sched-domain.
May  3 22:51:08 Europa kernel: [29384.696223] CPU0 attaching NULL sched-domain.
 
```Does anything in the logs point to the problem I'm having??

---

### Post by solitaire on 2009-05-03
I've entered it as a bug:

[https://bugs.edge.launchpad.net/ubuntu/+bug/371411](https://bugs.edge.launchpad.net/ubuntu/+bug/371411)

Please check it and if it matches your exact problem then please subscribe. 

If you are having a RESUME problem this is a different issue and bug.

If i've missed anything from the bug report let me know and i'll update it as required!

---

### Post by TiredBird on 2009-05-09
> **sttal said:**
> I have a similar problem! in the menu it only shows the shutdown and restart options.
Likewise.

---

### Post by TiredBird on 2009-05-10
My problems related to suspend and hibernate have been solved thanks to the posts in these threads: [http://ubuntuforums.org/showthread.php?t=1144999]("http://ubuntuforums.org/showthread.php?t=1144999.") and [http://ubuntuforums.org/showthread.php?t=814939]("http://ubuntuforums.org/showthread.php?t=814939").

---

### Post by solitaire on 2009-05-10
> **TiredBird said:**
> My problems related to suspend and hibernate have been solved thanks to the posts in these threads: [http://ubuntuforums.org/showthread.php?t=1144999]("http://ubuntuforums.org/showthread.php?t=1144999.") and [http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939).

I tried those threads! nothing worked. Everything says my Laptop can suspend and Hibernate but they just don't.

Weird problem...

---

### Post by solitaire on 2009-05-17
**BUMP**

Anyone got any ideas?

**BUMP**

---

