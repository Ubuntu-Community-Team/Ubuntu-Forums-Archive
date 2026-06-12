---
title: "Toshiba A210 Laptop - Volume Control Wheel"
date: 2008-05-26
forum: Hardware
---

### Post by bobnutfield on 2008-05-26
Hello Everyone,

This is not a post about something not working, but a post about WHY something DOES work.  I have a Toshiba Equium A210 laptop with both Ubuntu 8.04 and Slackware 12.1 installed.  This laptop has a volume control wheel in the front.  In Hardy, this wheel works to control the volume and a graphical slide bar pops up.  I am trying to get this little feature to work in Slackware as well.

Usually, this kind of feature is part of the keyboard shortcut bindings, but I cannot find anywhere in Hardy which shows this,  In /etc/X11/xkb/int you can usually find the keyboard shortcuts, but there is nothing about this there.  I am beginning to think that this volume wheel is not related to the keyboard (could be wrong), so I am probably not going to find the answer in X11.

Can anyone tell me where to look to find out what file controls this volume control wheel?  This thing worked "right out of the box" in Hardy so it was recognized in the install.  If it is, in fact, keyboard related, where would I look?

Thanks in advance for any replies.

Bob

---

### Post by ShodanjoDM on 2008-05-26
I don't know if this work, but you could try running xev

```
$xev 
```

and moving the volume wheel backward and forth and watch the output in the terminal.

From the man page:

> Xev creates a window and then asks the X server to send it events whenever anything happens to the window (such as it being moved, resized, typed in, clicked in, etc.). _It  is  useful  for seeing what causes events to occur and to display the information that they contain;_

---

### Post by bobnutfield on 2008-05-26
Thank for that reply....a great new tool to know.  I was not familiar with that.  The out put gives this when the wheel is moved while running this command:

> KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

This should be enough to google around for my answer.  Probably would have been easier if there were keys being identified.

Thanks again for your help, that was very useful.

---

