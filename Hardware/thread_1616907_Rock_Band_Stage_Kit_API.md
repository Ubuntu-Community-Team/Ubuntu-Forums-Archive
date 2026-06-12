---
title: "Rock Band Stage Kit API"
date: 2010-11-08
forum: Hardware
---

### Post by tudor117 on 2010-11-08
Hello!
I recently got interested in the Rock Band Stage Kit (or fog machine) and I was wondering if it could be used within linux. I looked if anyone made a driver and surprisingly I found an API which uses the xinput dll from windows. I realize that it won't work on linux, however I'm wondering how hard it would be to port it over considering that there is the xpad and xboxdrv driver. 
The API is also written in C# which isn't the greatest for linux. 
The commands the stage kit takes are relatively simple and it isn't a huge project, but I'm a beginner programmer and wouldn't really dare to try writing drivers.
The stage kit costs about $30 and it would be great fun to play around with.

Here's the code: [_http://stagekit.codeplex.com/_]("http://stagekit.codeplex.com/")

I'm hoping someone would port it over or at least help with the porting.

**UPDATE**: -------- Here are the api's on github by jummama
For the wxWidgets GUI stagekit tester:

[https://gith*******/jummama/wxStagekit](https://gith*******/jummama/wxStagekit)

and for the ridiculously simple terminal tester app:

[https://gith*******/jummama/stagekit](https://gith*******/jummama/stagekit)

---

### Post by tudor117 on 2010-11-08
So no one wants to port it.
Fine. 
Any chance in getting advice on porting it?
It's in C# 3.5.

---

### Post by sunnynice on 2010-11-09
> **tudor117 said:**
> So one wants to port it.
Fine. 
Any chance in getting advice on porting it?
It's in C# 3.5.
 might be some chance.

---

### Post by tudor117 on 2010-11-13
Bump?
. . .

---

### Post by jummama on 2010-11-23
Been a while since I've been on the forums here, but I just got one of these, and it seems all you need to do is send rumble effects through force feedback to signal it. I'm using ioctl, but perhaps sdl would support force feedback? Not sure on that part, but if I get real brave I might try to patch the xpad.c driver to use kernel led support as an abstraction for the stagekit.

---

### Post by tudor117 on 2010-11-23
WOA! You already surpassed my knowledge ;)
Because of the force feedback, I was recommending the xboxdrv driver; that is it supports rumble.
Anyways, I do hope that you try this out :D

---

### Post by jummama on 2010-11-23
Well in my poking and prodding at it, and using that c# version as a reference, I've been able to hobble together a fairly simple c api consisting of commands like sk_fogon() and sk_setred(byte)... just want to do a little bit of code factoring and a simple test gui instead of my current, ugly terminal tester, then I'll stick it on github for anyone that's interested

---

### Post by tudor117 on 2010-11-23
WOW! You're the best!
I'd be pretty cool if there was a plugin for media players to support it as visualization. It won't be too hard to do after your api!
Thanks!

---

### Post by jummama on 2010-11-24
It's up on github. It's still ugly, but it does work, lol...

For the wxWidgets GUI stagekit tester:

[https://gith*******/jummama/wxStagekit](https://gith*******/jummama/wxStagekit)

and for the ridiculously simple terminal tester app:

[https://gith*******/jummama/stagekit](https://gith*******/jummama/stagekit)


They both use the same api, which is provided by stagekit.c and stagekit.h. stagekit.h is the closest thing to documentation I really have for it yet, but I'll keep my github up to date. Happy coding!

EDIT: seriously? can't post urls here? I'm sure anyone around with the ability to make use of this can figure out what goes in place of gith******* by reading the rest of the post though, lol

---

### Post by tudor117 on 2010-11-24
Excellent job! Maybe some dj apps may use this as plugins.

Just a suggestion, instead of using the event number, use the event id. That would be */dev/input/by-id/usb-Performance_Designed_Products_PDP_Home_Stage_Kit_0100C06F-event-joystick*
That would make it more generic and it should work for everyone!

Anyways, thanks so much for posting this!

EDIT: never mind, i see you added probing for the event file.

---

