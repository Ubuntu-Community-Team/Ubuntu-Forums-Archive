---
title: "After today's update: Kalarm wont work. HELP!!"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by tiggsy on 2009-05-05
I have kalarm, and up to this morning, it worked fine. I use it extensively, it's very important that i get it to work again, or i will lose all my scheduling, including birthdays, reminders to pay bills on time, all that stuff.

It doesn't load on boot, as it used to. If i try to start it in the terminal i get:

```
kalarm
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/tiggsy/.DCOPserver_tiggsys-desktop__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.

```

---

### Post by tiggsy on 2009-05-05
Doesn't anyone have any ideas to help?

---

### Post by tiggsy on 2009-10-20
After upgrading to Jaunty Jackelope, Kalarm (which i finally got working in May in Hardy) has blank screens when you try to add or edit an alarm. They are just big gray squares so it's no longer possible to add or change an alarm.

I went to report it as a bug through the built-in feature in Help, but it is already listed there as an Ubuntu-only bug - so they aren't inclined to do anything about it.

Does anyone have a fix?

---

### Post by louieb on 2009-10-20
You mean you get a big back blob like I get when opening the system monitor in Karmic?
Have you checked [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

---

### Post by tiggsy on 2009-10-20
No. It's a big grey blob.

And I'm not using Karmic Koala (though I intend to once it's out of beta), but Jaunty, as I said.

Thanks for pointing me to the ubuntu bugs (didn't know where that was). I found the problem, and a temp workround here: [https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/391889](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/391889)

Basically, to stop the window being blank, resize it!

---

