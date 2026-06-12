---
title: "Enabling boot logging?"
date: 2008-11-24
forum: General Help
---

### Post by blazemore on 2008-11-24
I'm trying to fine tune my rig's boot-speed, and have so far got it down to 18 seconds (From Grub to GDM) using a custom kernel, disabling fsck, and profiling.
However, when my system boots I see a lot of text flashing up, and I want to be able to log this, including timestamps, so I can strip out what I don't need.
I especially need the first 5 seconds (where everything is timestamped, before the font loads).
While Bootchart is useful, it doesn't give me enough detail.

I've tried following tutorials and googleing it, but /var/log/boot remains empty (apart from the default message saying nothing has been logged yet or something)

---

### Post by blazemore on 2008-11-24
*bump* I want to get under 18 seconds tonight!

---

### Post by AAOFan on 2008-11-24
Have you played with bum? Have you also checked dmesg? Although on mine from 0-25 is blank lol

---

### Post by blazemore on 2008-11-24
I just really want to log everything that runs when the system is booting up. I might film it with a video camera if I can't get this to work.

---

### Post by zephyrcat on 2008-11-24
I am sure this is not what you are looking for, but if you could transfer what you have done into a virtual machine, you could do a screen capture and go frame by frame...

---

### Post by blazemore on 2008-11-24
That's REALLY not what I want to have to do!

```
 $ cat /var/log/boot
(Nothing has been logged yet.)
```

This is definitely the way to go. Is there a "log" option in Grub or something?

---

### Post by AAOFan on 2008-11-24
Ok, I know exactly what you want now.

```
sudo gedit /etc/default/bootlogd
```

Change:
BOOTLOGD_ENABLE=No

to

BOOTLOGD_ENABLE=Yes

There you go!

If that doesn't work for you then check here for more answers. [Link]("https://answers.launchpad.net/ubuntu/+question/2933")

---

### Post by blazemore on 2008-11-25
I still get
```
 $ cat /var/log/boot
(Nothing has been logged yet.)
```

---

### Post by AAOFan on 2008-11-25
> However, as you can see from your /var/log/boot message file, another logging daemon is now in use, it's called 'logd' and is part of 'upstart'. This is really the bootlogd replacement. As this one, it's only capturing start jobs output directed to the console and so doesn't print kernel boot messages.

The kernel boot messages should be saved in your /var/log/dmesg, but if you cannot see all of them in there, that's another story.

BOOTLOGD logs to that file. They replaced it with upstart-logd which writes to dmesg instead. That's why it's not working.


So enabling the BOOTLOGD will not work after all.

I hope that answers you question.

---

### Post by Ghilteras on 2008-12-02
ok we can't use bootlog, how can we see boot logs then?

my dmesg is largely incomplete, i just wish a nice complete boot log

---

### Post by HousieMousie2 on 2008-12-04
Upstart, which replaced sysvinit, doesn't work correctly.  I believe the last time we had working boot logs was in Dapper Drake.

LaunchPad:[[COLOR="RoyalBlue"]logd not running[/COLOR]]("https://bugs.launchpad.net/bugs/98955")

Unfortunately they only consider this problem to be of 'medium' importance... but at least it isn't still sitting at 'wishlist' level.

I guess they figure if Upstart only half way works then that makes it a success.  #-o  lol

---

