---
title: "Tablet T4220 and screen rotation"
date: 2008-05-21
forum: Hardware
---

### Post by roy.nico on 2008-05-21
Hello, 

i'm have a small problem with the rotation of the screen of my tablet, under Hardy (that i installed this morning), but it was the same with gutsy :
* when i boot, the login screen (gdm) appears, i see a message saying that the driver fsc is loaded. At this point, the rotation works (both using the tablet buttons, are turning the screen into "tablet position"). 
* If i log on in landscape position (the usual one), then, the rotation does not work any more, neither with the tablet buttons nor by rotation the screen. 
* But if in gdm, i first trun the screen to Portrait position, and then log on, then the rotation works in my session. 

It looks like, when logging in in landscape position, that the modules/driver fscb is unloaded.

Does anyone has an idea ? 

nico

---

### Post by roy.nico on 2008-05-24
I solved the problem, just by adding my user tot the group "users". 
THe answer was actually here: [https://help.ubuntu.com/community/T4220]("https://help.ubuntu.com/community/T4220"). It is sayed explicitly : 
> If you install the binaries from the ubuntu repository, everything should be set up to have fscd start at login. The problem is that the file /etc/udev/rules/65-fsc_btns.rules sets the /dev/event[0-9] devices to be owned by the group 'users', but (at least for me) you aren't a member of the 'users' group by default. After adding yourself to the 'users' group, fscd should start when you log into Gnome.

Nico

---

### Post by Brijamelsh on 2008-07-10
i have a t4215 but my rotation dosnt work, is there something i can do to get the same functionality of the t4220?

---

