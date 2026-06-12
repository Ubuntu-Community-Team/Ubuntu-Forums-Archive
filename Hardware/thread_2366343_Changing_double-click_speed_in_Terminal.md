---
title: "Changing double-click speed in Terminal"
date: 2017-07-16
forum: Hardware
---

### Post by jjules on 2017-07-16
Hi everybody,

I just installed Ubuntu 17.04 on my new laptop. Could finally get the touchpad to work, but I don't have an option for double-click speed in my mouse settings. So I was wondering if there's a way to change it in the terminal? The problem is that I can't open folders etc. by double-clicking, so I'm pretty sure that I need to adjust the double-click speed.

I couldn't find anything online, but maybe one of you knows of a way :)

Thanks in advance!

---

### Post by vasa1 on 2017-07-17
I have this file, *~/.config/gtk-3/settings.ini*. If you don't have such a file, create it using any **plain** text editor. 

The first line should be:```
[][Settings]
```
Then, have this line:```
gtk-double-click-time=1000
```You could change the value which is in milliseconds to something more convenient. The lower the value, the more quickly you'll need to double-click.

Save the file. Close your file manager and reopen it and test the double-click if you also have a mouse attached.

For your touchpad, please run *synclient* in your terminal. I hope you get some output! If you do, look at altering ```
    MaxDoubleTapTime        = 100
```
Once you find a suitable value, you can add something like```
synclient MaxDoubleTapTime=100
```to your autostart so that it will take effect each time you log in. How, exactly that's to be done depends on your distro.

---

### Post by jjules on 2017-07-17
Thank you so very much!

I didn't know which value I needed to change with synclient. Now I've changed the MaxDoubleTapTime down to 50 instead of 180 and it works like a charm!
I've already changed some other synclient settings and added them to Startup Applications (I'm using Ubuntu), so I'll just need to add this one :)

Thanks again!

---

### Post by vasa1 on 2017-07-17
Then please see [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) for how to mark this thread [SOLVED]

---

