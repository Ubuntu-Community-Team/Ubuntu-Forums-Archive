---
title: "Wacom Tablet Malfunctions"
date: 2011-09-13
forum: Hardware
---

### Post by amgoiree on 2011-09-13
I have a 4 year old wacom tablet (Graphire4) that suddenly developed a problem in Ubuntu 10.04 a few months ago. Whenever I click something, the mouse pointer freezes until I move the stylus out of the active area and then back in. I checked with a new bamboo tablet, but it still has the same problem. It had never had this problem for the year I've been using it up to that point. I dual boot and I tested my tablet on windows 7, it worked fine. I tried instructions on [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) and [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1) but neither method worked for me. Can anyone help??

---

### Post by Favux on 2011-09-13
Hi amgoiree,

Welcome to Ubuntu forums!

Let's first make sure that the tablet is on the Wacom X driver.  What is the output of the following commands run in a terminal?
```
xinput list
```
and
```
xsetwacom list
```
And are you using the Graphire4 or the Bamboo or both?

---

### Post by amgoiree on 2011-09-14
Woah! Actually I guess one of the two things I tried worked yesterday (I just  needed one more booting) - it worked when I turned my computer on today! :D
Thanks anyway though :)
Also, how do I check if my thread has a response?

---

### Post by Favux on 2011-09-14
Good!

You can use the thread tools on the upper right to subscribe to the thread.  That will get you a notification in your user control panel.

---

### Post by Megastar12 on 2011-09-15
[LEFT][COLOR=#333333][FONT=Arial]I've been using a Wacom Intuos 3 pen without any problems in CS3 and Lightroom2. Now, I can't seem to make the pen responsive at times (most of the time). I've uninstalled old Wacom drivers and installed the latest, repaired permissions, restarted the computer. As the pen seems to otherwise work fine, it must be an Adobe issue. Does anyone know a solution?
Sarah:):):):)

[Watch TV Online]("http://www.goonlinetv.com")
[watch online tv ]("http://www.goonlinetv.com")


[/FONT][/COLOR][/LEFT]

---

