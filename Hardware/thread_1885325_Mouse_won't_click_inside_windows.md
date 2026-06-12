---
title: "Mouse won't click inside windows"
date: 2011-11-23
forum: Hardware
---

### Post by Lamar15 on 2011-11-23
I recently bought an old emachine to use as a totally ubuntu system. Ubuntu 11.10 installed great however my mouse has very limited functionality. It works on the launcher but doesn't work at all inside a window once any application is opened. Also it doesn't work for drop down menus on the top right of the desktop. I don't believe it is an issue with the mouse itself because I tried switching to numbers pad control of the mouse and it behaved the same way. It works perfectly if I boot from the livedisk and I have tried completely re-installing with no results. I'm very new to ubuntu/linux(like 2 weeks) but really enjoy what I've found so far. If anyone has suggestions I'd be very grateful.

---

### Post by An Sanct on 2011-11-23
Welcome to the Forums!

Thats an interesting problem :)

Did you update your system yet? As I said it is interesting, it seems, that the "UI* control*" is not working properly...

As said, my first guess would be to update the system, open up a terminal and enter
```
sudo apt-get update
sudo apt-get upgrade
```

If you cannot get to the terminal, because of the User Interface limitation, you described, you can boot into "recovery mode", if you hold the shift key at boot time. There you can select the "remount" option, this will enable more functions to the recovery mode. Select "dpkg" from the (now larger menu), this updates the system from recovery mode.

If I was not fully clear or you have more problems, please let us know.

---

### Post by Lamar15 on 2011-11-23
Updated using recovery mode/remount. I got a little exited because it resized the display icons so I knew it had done something but sadly the mouse still has the same limited function. Also looking at my initial post I see that I didn't mention that I am able to navigate/start in open windows with tab and direction controls if that helps narrow things down at all. Well thanks for your time and advice and also thanks for the welcome glad to be here.

---

### Post by An Sanct on 2011-11-23
When you navigate to the controls, do they respond (do something) when you hit enter?

What kind of mouse do you use? PS2/USB???
Is your computer a laptop? If so, does it have a touch pad?

PS. the welcome is a small gesture ;) no problem

---

### Post by Lamar15 on 2011-11-23
Yes controls respond/run when I hit enter. I'm using a logitech trackball USB mouse...the PS2 port is completely unresponsive with a very old mouse that I tried doesn't even move the cursor. It is an old desktop that I know at some point was refurbished but I have no idea what was done then.

---

### Post by An Sanct on 2011-11-23
Interesting! With trackball, you mean something like on the attached image?

(so, simply said, the pointer controls are not referenced by the movement of the ground beneath the device)

Well, trackballs are not mice :) sorry to say that, but is is a fact...

Please check this [ubuntu community wiki]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB"). An alternative is, that you get a plain mouse until you fix the problem. I am sorry to say, but I have no experience with trackballs and Linux, I just know, that the mapping of the buttons is different (ie, left click on a plain 5$ mouse is "1",  right click is "2", but on a trackball the right click would be "8" or maybe "12" ....)

---

### Post by Lamar15 on 2011-11-23
I can't really convey how funny your response was. I got my wife and kid to come and view it. The mouse on the ubuntu wiki is the exact same mouse I'm using.I had no idea about mapping etc and I'm not opposed to using a standard mouse for a bit but trackballs for me are best and what I want.

---

### Post by An Sanct on 2011-11-24
> **Lamar15 said:**
> I can't really convey how funny your response was. I got my wife and kid to come and view it. The mouse on the ubuntu wiki is the exact same mouse I'm using.I had no idea about mapping etc and I'm not opposed to using a standard mouse for a bit but trackballs for me are best and what I want.
I'm always glad to amuse people! :)

Well, the wiki says it all and I personally have no experience with trackballs, so I hope, that you will find the correct answer there.

If you have any further questions or problems, feel free to share them on this forum. ;)

---

### Post by Lamar15 on 2011-11-24
You can mark this as solved. Bought a standard USB mouse and it works perfectly. Now that the desktop functions right all I need to do is configure my trackball mouse and return the standard one to get my money back.

---

### Post by An Sanct on 2011-11-25
> **Lamar15 said:**
> You can mark this as solved. Bought a standard USB mouse and it works perfectly. Now that the desktop functions right all I need to do is configure my trackball mouse and return the standard one to get my money back.

Nice move :)

Well, only the thread creator has the power to mark the thread as solved (... and admins ...). You can find the option under "Thread Tools", above.

---

