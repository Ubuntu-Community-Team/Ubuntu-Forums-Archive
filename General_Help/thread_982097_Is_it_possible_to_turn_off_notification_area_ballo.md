---
title: "Is it possible to turn off notification area balloons?"
date: 2008-11-14
forum: General Help
---

### Post by bawbag31 on 2008-11-14
I have been looking around for a check-box to disable the balloons, but I cannot find one.  I do not want to get rid of the notification area altogether, just the balloons such as the one that tells me I am connected to a wireless network.

If there is such an option, could someone tell me where it is, please?

Thanks

Phil

---

### Post by sdennie on 2008-11-14
If you reall don't want to ever see any notification balloons, you should be able to:

```

sudo chmod -x /usr/lib/notification-daemon/notification-daemon
pkill notification-daemon

```

That makes the daemon non-executable and will prevent it from ever being started.  You can't just "apt-get remove" it without taking some other important packages with it so, this is the only method I know of if you want to disable all the balloons.

---

### Post by bawbag31 on 2008-11-16
Thanks for the reply.  I'll give it a go.
Cheers,
Phil

---

### Post by hardusb on 2010-01-31
Would this work on the latest ubuntu netbook remix? I tried another tutorial and it disabled my whole userinterface!, I managed to fix it, but now I still have this annoying popup balloons for everything.

Thanks,

Hardus

---

### Post by xander98989 on 2010-02-03
Disabling /usr/lib/notification-daemon/notification-daemon will break the UNR launcher desktop as will disabling
[FONT=Verdana]/usr/share/dbus-1/services/org.freedesktop.Notifications.service [/FONT]
or /usr/share/notify-osd/notify-osd. I can't figure out how to stop the balloons safely and it's driving me crazy.

Edit: notify-osd is in /usr/lib/... My mistake.

---

### Post by nevdelap on 2011-03-08
Here is a solution for turning off the balloon notifications from power manager at least.

(My charger has an oversensitive thermal cutout which has it going on and off constantly in hot whether so a notification every few seconds was driving me NUTS!)

In gconf under /apps/gnome-power-manager/notify there are six check boxes for the six types of notifications it produces. I've turned off 'discharging'. Happy now.

There are probably other apps that can have their notifications turned off in there. Stopping the daemon from running doesn't help for this case because it just pops up message boxes which are even more annoying.

:)

---

