---
title: "Program startup wait - very simple question"
date: 2008-07-10
forum: General Help
---

### Post by schmidtbag on 2008-07-10
Just so you all know, I spent at least an hour looking up how to solve this but I just can't get an answer.


BACKGROUND ON THE PROBLEM:  (not entirely necessary to read)
Anyways, a few weeks ago I was doing the screensaver as a wallpaper idea.  I have everything set up just as I want to (i set up 2 wbar docks to replace my missing icons).  The screensaver works at startup, I followed instructions on how to get it to work, but for some reason  it just randomly shuts down based on whatever I'm doing.

For example, if I start up pidgin, the first letter I type shuts down the screensaver.  I created a "Screensaver Refresh" launcher in my applications menu so every time it shuts down, I can just start it up again.  When I use that launcher, it works fine.  It never shuts down for days.


MY FINAL QUESTION:
The screensaver starts up before most of gnome is loaded, so I'm guessing the only way to fix this is to tell it to wait a few seconds until everything is settled.  I tried the following command in terminal:
```
sleep 5 && /usr/lib/xscreensaver/cubestorm -delay 35000 -speed 1.01 -count 3 -thickness 1 -root
```
and it works just as I want it to, BUT, if I run it in a launcher, it doesn't work.

So how do I make a launcher wait before starting up a program?  I am confident that the Sessions Preferences works like a launcher, because it too doesn't do anything.



As a second question, if anyone out there uses wbar, does anyone know how to make the background have an opacity/alpha value instead of just using a screenshot?

---

### Post by aashay on 2008-07-11
From what I know, you need to put the command in a script and execute that instead. Be sure to chmod +x the script too

---

### Post by sdennie on 2008-07-11
I don't completely understand your post but, I think what you are trying to ask is, "How can I make a complex command line thing run from a launcher".  The answer to that would be to make your launcher command:

```

bash -c "sleep 5 && /usr/lib/xscreensaver/cubestorm -delay 35000 -speed 1.01 -count 3 -thickness 1 -root"

```

---

### Post by schmidtbag on 2008-07-11
awesome!  vor what you told me to do worked perfectly, thanks.

i have seen both "bash" and "-c" being used before, but could you give a brief description of what those mean?  I always like to understand whatever I'm using.  For example, when it comes to programming, I never use someone else's code until I know how and why it works.

Thanks again

---

### Post by avtolle on 2008-07-11
From a CLI ```
man bash
```

---

### Post by schmidtbag on 2008-07-11
o cool, that "man" feature will save me a lot of time

---

