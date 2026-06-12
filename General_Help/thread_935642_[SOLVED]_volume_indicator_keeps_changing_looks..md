---
title: "[SOLVED] volume indicator keeps changing looks."
date: 2008-10-01
forum: General Help
---

### Post by rosj04 on 2008-10-01
Hi,

I have a weird "problem". And since I'm still a major noob to linux/ubuntu and what is what I don't really know how to look for a way to correct it other than post here :3

What happens is that when I start my computer and boot into gnome my volume indicator (what you see on the screen when you change the volume) keeps changing looks randomly. This happens also when I restart the X session by hitting ctrl-alt-backspace.

And furthermore, I've noticed that it seems to create problems when it happens because mpd stops working if I restart the X session and the indicator changes. 

Do I have some conflicting software installed perhaps? I run gnome with compiz as my default window handler and pulseaudio as my soundserver.

I've included 2 screenshots containing the 2 different looks, example 2 being how I want it to look.

Thanks for any help given :

Edit: Also, when the volume indicator seen in example 1 is started my touch buttons on my xps dell m1330 stops working. I normally use keytouch to get them working and I've checked and it still loads with the example 1 volume indicator but it doesn't work anyway.

---

### Post by rosj04 on 2008-10-02
no one has any inkling of what could be wrong? program conflict? theme conflict? :-/

(sorry for bumping)

---

### Post by rosj04 on 2008-10-04
sorry if I keep bumping, but this is a big problem for me (having to restart up to 10 times everytime I wanna use the computer).

I have a friend who is also using ubuntu and he is experiencing the same thing, the look of the volume indicator keeps changing. 

Does any know what part of the system handles that?

---

### Post by rosj04 on 2008-10-05
done some reading (alot actually :P) and it seems that the example 2 volume bar is thanks to keytouch and the example 1 bar is drawn by gnome itself. 

I've been trying to find if its possible to disable the gnome one in gconf but haven't had any luck. 

Does anyone else know of any way to disable it?

thx in advance.

---

### Post by erdu on 2008-10-05
I have the same kind of problem. Since a couple of weeks I can no longer get the big volume indicator, only a small bar. Worse, even that small bar is not always showing up, seems to be random.

---

### Post by rosj04 on 2008-10-06
Well I discovered the cause of my problem, quite simple really.. it was staring me right in the face. 

I still had my keyboard shortcuts set under system > preferences > keyboard shortcuts 

which interfered with keytouch the program I use to control my keyboard media keys (it also gives the small volume bar). Once I removed all the shortcuts keytouch started working and the small bar returned. 

Might be something similar to your problem but in reverse erdu? do you have keytouch installed?

---

### Post by erdu on 2008-10-07
You're right. I uninstalled keytouch, and the problem was gone...thanks for the hint!

---

