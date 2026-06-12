---
title: "infininate loading on xsession. unknown process, high cpu usage!!!!"
date: 2010-03-05
forum: Hardware
---

### Post by ultiphoenix on 2010-03-05
Hi guys, i've run into quite a irritating issue the past 2 days. I dont know what causes this, but im guessing its something with X.

When i log into a x session, it just keeps loading after im logged in and can do whatever. if i check the system monitor, there is no processes running above 5%, system is in idle. But my cpu usage is 70%, and it just keeps loading. The loading cursor never goes away.

When i log out or try and restart, it complains about waiting for some unknown process.

Has anybody had this issue yet? it seem to only happen after i do some updates.

I've already verified its not the nvidia driver, running with the 'nv' or 'nouveau' driver makes no difference to this issue.

The process seemed to have stopped for the first time now by itself, i wonder if it might be gone although i doubt i'll be that lucky.

Please if anybody has this problem, or know what it is or how to fix it, please post solutions.

My laptop is running so slow, i can work on it.

---

### Post by Frogs Hair on 2010-03-06
Hello,

I don't know how to fix it, but you can find out what it may be by, opening the system monitor and selecting the process tab to view running processes .

That would give you a place to start.

---

### Post by colly11 on 2010-05-08
I've got the exact same problem as this. Just started after upgrading to 10.04. Did anyone have any luck in finding a solution? It's getting really annoying!!

It seems as though ubuntu is constantly starting and killing processes so that the ID of the "unknown" process listed in system monitor is constantly climbing. The repeated, infinite starting and killing of the process is eating my CPU time.

Please help !! somebody... 
Thanks.
Colly

edit: Through process of elimination I found it was "Disk Notification" start-up application (usr/lib/gnome-disk-utility/gdu-notification-daemon). Does anyone have any idea why this application behaves like this?

---

### Post by selopo on 2010-05-10
Exactly the same issue just after upgrading to 10.04.

I found this that it can be related. I'm not at home so I'll try after...

[http://ubuntuforums.org/showthread.php?p=9250302](http://ubuntuforums.org/showthread.php?p=9250302)


The funny thing is that it doesn't happen after all boots and normally just doing logoff-logon solves the CPU consumption. Looking forward to an explanation.

---

### Post by JoakimP on 2010-08-02
Im not sure that this is still a problem for you, but I found a solution to the problem when I had it. For me it was a configuration issue withNautilus.

Have a look at this post: [http://ubuntuforums.org/showpost.php?p=9668140&postcount=11]("http://ubuntuforums.org/showpost.php?p=9668140&postcount=11")

Hope it'll help!

---

