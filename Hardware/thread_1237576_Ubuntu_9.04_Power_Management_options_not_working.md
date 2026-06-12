---
title: "Ubuntu 9.04 Power Management options not working"
date: 2009-08-11
forum: Hardware
---

### Post by budgemook on 2009-08-11
Hi,

I recently installed Ubuntu 9.04 on both my acer aspire one netbook and on a dell laptop which is a few years old. It's working away pretty well but now there is one issue which is being a bit of a pain.

The power management options don't seem to be used at all. I set it up so the display should never go asleep but on both machines the display does go asleep after some time. 

I leave my netbook on all day sometimes downloading large files but for some reason when i get home for work the display has gone asleep and ultimately ubuntu has crashed and has to be hard rebooted.

I reckon that if the display didn't go to sleep in the first place then the crash might not happen.

In work, the annoyance is for a different reason but the same issue. I have a desktop and a laptop beside each other. Usually I use the laptop for when I am on customer sites but when in my local office I use it to connect via VPN to networks and generally leave it tailing some log files. The display keeps going to sleep so I have to reach over and wake it up again. Okay, this is a mild inconvenience but at the same time, if there is an option to prevent this the surely it should work right?

I originally thought it was my netbook acting up as there are some other niggly bugs and there were loads with 8.10 but the fact that it happens on the dell makes me wonder.

For the netbook I used netbook remix to install and then changed things around so it looks like a regular ubuntu install. For the dell, i installed kubuntu but then downloaded the gnome desktop and deleted kde.

Cheers

Adrian

---

### Post by tantric rex on 2009-08-30
have you tried running config as root?  i recently stumbled upon a post which suggested that ubuntu provides for two levels of settings: (1) user, and (2) root.  maybe the root acct settings are overriding your users.

unfortunately:

(!) i can't find that post again to link you to
(@) i only started running linux (ubuntu 9.04) last week
(#) i haven't tried this fix because i don't have this issue

so i have no idea if doing this will break your box, but hope this helps!

---

### Post by SickBeast on 2009-08-30
I'm having a similar problem with my system.  I have an intel 855 chipset which I suspect is the problem.

It seems that they need to work on this issue as suspend/resume issues seem to be quite widespread.

If you go to system--preferences--power management, you can set some of the options.  If you're crashing on resume though you're having the same problem as me.  My display won't come back on at all during a resume.  If this were Windows it would be a showstopper bug IMO.

If there is any way in which I can contribute to resolving this issue, someone please let me know.  It's driving me nuts and I'm willing to put some time into it.

Some people have said that if they use an older kernel it works.

---

### Post by budgemook on 2009-08-31
Mine doesn't *always* fail on resume, just sometimes. I'm not even sure that it is suspended, the display is just off but my downloads are still going on in the background. I will try with some older kernals - any idea how old exactly?

BTW, the aspire one uses Intel 945GSE Express chipset.

---

