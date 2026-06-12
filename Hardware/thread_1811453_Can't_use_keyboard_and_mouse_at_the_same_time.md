---
title: "Can't use keyboard and mouse at the same time"
date: 2011-07-24
forum: Hardware
---

### Post by kolzene on 2011-07-24
I just upgraded my Pavillion with a Geforce GT 440 card, and activated the proprietary driver. All works great, except that any time I am pressing a button on the keyboard, the mouse pointer will not move. Not normally a problem, but it makes many games (in particular FPS) impossible to play, as I can not turn and move at the same time. My Kubuntu is 10.10 (64 bit), the mouse is a USB Logitech Dual Optical MouseMan, and the keyboard is old enough I need an adapter to plug it into the ps/2 port. Net searches haven't pulled up any solutions. Any ideas other than upgrading to 11.04 (which I know I have to do anyway someday, but I hate doing, so I procrastinate)? I just want my games to work before I get around to doing that.

---

### Post by enimeizoo on 2011-07-25
It could be a problem from the keyboard or the adapter. That is what I would have said if you did have the same problem with your older graphic card, since uncommon keyboard event can cause weird things.

It is weird, though, the graphic card isn't supposed to control mouse events at all. It isn't even supposed to be aware of them. Did you try to disable desktop effects? Does it work fine without the proprietary drivers? 

Do you have another desktop environment to try (gnome, xfce, whatever)? A live CD ? Another keyboard to try? 

You also could get more info with xev. Not sure how useful it would be, but... See if you get motionnotify events when you move the mouse while a key is pressed. Also, you could post a few keyboard event, just to see if there is something weird.

---

### Post by cyb3rkn19ht on 2011-09-13
Found the fix! Here is a link:
[http://ubuntuforums.org/showpost.php?p=4310834&postcount=6](http://ubuntuforums.org/showpost.php?p=4310834&postcount=6)

I have the same problem. I tried to run motionnotify but it is not a command. I don't have another keyboard but I do have another mouse. It still happens with the other mouse I have.

---

### Post by kolzene on 2012-05-11
Thanks! This has been bugging me for months! I'd almost given up checking. :)

---

