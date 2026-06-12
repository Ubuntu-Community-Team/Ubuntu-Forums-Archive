---
title: "[SOLVED] Enabled effects, screen went wierd :("
date: 2008-11-14
forum: General Help
---

### Post by njones92 on 2008-11-14
I've had a quick check and I don't think anything like this has been posted yet...
(Just to let you know I'm very new to Kubuntu.)


I was using Firefox in Kubuntu 8.10 and was just playing around with the configuration menus. I saw something in there titled Effects (or something like that), so had a look and tried turning some on. Then I walked away from the computer and didn't realises that a confirmation message appeared giving me 10 seconds to confirm or change my mind about applying the efects. By the time I returned to the computer it was too late and it had already applied the changes.

But here the problem starts. The screen just goes completely black and where there should be a window there's just a faint white shadow around it.I can't see any text, images or anything! :(

I tried Ctrl+Alt+Del to log out and this worked and I can see the log in screen perfectly, but as soon as I log in the screen goes black (and sometimes bright white at random intervals).
(I should also mention that the mouse cursor is always visible and moves around the screen as normal. If I right-click it still activates menus, but they appear black with the faint shadows like the rest of the windows.)

I think this may be due to my nVidia MX4000 graphics card. About 30 mins before this problem occurred the hardware driver manager appeared saying that I needed to activate the 3D settings or something, so I clicked Activate, but nothing happened, so I just ignored it. Now I think this was a mistake :confused: . 


Does anyone know of a keyboard shortcuts to turn off all effects or some other way of rectifying this strange problem?

---

### Post by Sam Lars on 2008-11-14
At the login screen hit Alt+F1, log in, and run
```
sudo apt-get remove compiz
```
Hopefully that will remove compiz and get you back to basics.

---

### Post by njones92 on 2008-11-15
Hi.

Thanks for the reply, but this doesn't work :( .

First of all, Alt-F1 doesn't do anything... Not on my computer anyway :confused: .
Instead, I tried a console login (not sure if this is the right thing to do, but anyway...). I then tried typing the code that you suggested, and this went through the unintall processes but then said 'Package compiz is not installed, so not removed.'
Does this mean that the problem is not with the Effects that I enabled, or is it just something completely different?

---

### Post by Sam Lars on 2008-11-15
Yes, that was what I was getting after.  I think it needed to be Ctrl + Alt + F1.
I think you're right, it may not be about the effects.   After reading your post again, I think it may be the driver...
In you /etc/X11/xorg.conf, look for a line that says
```
Driver "nv"
```
or
```
Driver "nvidia"
```
Whichever it says, try the other one.
If that is not there, try removing the Nvidia driver:
```
sudo aptitude remove nvidia-glx-*
```

---

### Post by njones92 on 2008-11-16
Thanks again for the reply.

This is probably a stupid question with a simple answer, but like I said I'm VERY new to all this. So how do I actually look for this Driver "nv" line :-s .

Would it be possible for you to give the exact code that I need to type?

Also, would removing the nVidia driver actually solve my problem, or just make it worse?

Thanks.

---

### Post by njones92 on 2008-11-16
Hi again.

After posting last I spoke to a friend who thought he might know what to do, so I tried his suggestion - and it worked!

He suggested that I move the .kde file and rename it.

I think this is how I did it:

Code:
ls -a

to find out what the .kde directory is called,

then something like...

Code:
mv .kde .kde.0

to move the .de folder and rename it. Apparently this resets all kde window behaviours back to default.

Thanks for your suggestions anyway :) .

---

### Post by Sam Lars on 2008-11-16
That's good to know, you can mark this thread as solved with the thread tools at the top to help others with similar problems.

---

