---
title: "[SOLVED] How to disable and re-enable compiz quickly?"
date: 2008-10-31
forum: General Help
---

### Post by emshains on 2008-10-31
So, I know winefix does that pretty easily, at least when I run HL2.  But I am looking for a way to disable it manually, with just a push of an icon or a command in the shell, because for native games and some other wine games that take a lot of resources I try to avoid using them with compiz, but I don't want to reset the compiz settings, because every time I set it to "none" it resets all my settings, so I have to bother with them again for 30min after I played the game I wanted. And when I kill the compiz.real process, it disappears (that's a surprise, now isn't it), but I get no gnome window borders at all, I have the window, but there is no "bars" around it. 
And I would like a command that would also bring compiz back :). 

P.S. I apologize for my bad English.

---

### Post by blade32 on 2008-10-31
There is a compiz icon in the repository.

---

### Post by PsychedelicReaction on 2008-10-31
it's the fusion-icon  package

---

### Post by emshains on 2008-10-31
All it does is restarting the compiz or making another process of compiz, thus making the whole PC slower. Clearly not the result I wanted.

It looks like it wants to disable it, but when it finally closes it, just reopens, propably because it can't find another window decorator, like the usual gnome.

---

### Post by jocko on 2008-10-31
The command line for disabling compiz (or rather replacing it with metacity) is:```
metacity --replace
```
And to activate compiz again:```
compiz --replace
```

You could just make starters for those commands on your panel or desktop.
Or find out how to make a script that checks if compiz is running or not and runs the proper command (I have no clue how to do it, but it is possible).

---

### Post by Wayne_V on 2008-10-31
sudo apt-get install compiz-switch

Adds Compiz-Switch to Accessories --- turns compiz on or off with one click.

---

### Post by emshains on 2008-10-31
> **jocko said:**
> The command line for disabling compiz (or rather replacing it with metacity) is:```
metacity --replace
```
And to activate compiz again:```
compiz --replace
```

You could just make starters for those commands on your panel or desktop.
Or find out how to make a script that checks if compiz is running or not and runs the proper command (I have no clue how to do it, but it is possible).

I will try that later, but since I don't remember myself installing metacity, will it work ? When I didn't set compiz to run with emerald, it always whined about how I should do the "emerald --replace" thing. So, is the --replace an option that makes a window decorator/manager become the primary one or the one that is used at the moment ?

---

### Post by jocko on 2008-11-01
> **emshains said:**
> I will try that later, but since I don't remember myself installing metacity, will it work ? When I didn't set compiz to run with emerald, it always whined about how I should do the "emerald --replace" thing. So, is the --replace an option that makes a window decorator/manager become the primary one or the one that is used at the moment ?

The --replace option makes metacity (or compiz) replace whatever window manager is running. Without --replace it will just see that another window manager is running and refuse to do anything... 

Metacity is always installed by default, as not all graphics cards or drivers are capable of running compiz...

---

### Post by emshains on 2008-11-01
Thanks a lot! That solved a hell of a lot things!!!

---

### Post by iblee on 2010-02-21
> **jocko said:**
> The command line for disabling compiz (or rather replacing it with metacity) is:```
metacity --replace
```And to activate compiz again:```
compiz --replace
```You could just make starters for those commands on your panel or desktop.
Or find out how to make a script that checks if compiz is running or not and runs the proper command (I have no clue how to do it, but it is possible).

Fantastic! Thanks for pointing this out. A quick search on:

[FONT=Courier New]"lenovo 3000 n100 disable compiz ubuntu karmic koala[/FONT]"

and I found this thread. 3 seconds later- problem fixed. I'm really glad people share their problems. As I move more and more to using ubuntu full time, stuff like this makes it rewarding.

[http://www.flickr.com/photos/iblee/4372119739/](http://www.flickr.com/photos/iblee/4372119739/)

---

### Post by kafkaPenguin on 2010-06-05
I recently upgraded to Karmic and was having this problem.  Thanks for posting the fix!  It has speeded up the system a hundred fold!

---

### Post by Maju on 2010-06-05
Hi. I just discovered that this compiz thing was causing my computer to slow down intermittently, it seems, and anyhow I like better the metacity looks, with the x to close windows and all the oldies. 

When I apply the 

```
metacity --replace
```

I get back the old look and, I presume, that *evil* compiz.real thing is neutralized but I can't close the terminal without making all to crash (no windows borders, all blocked - can't do but restart).

How can I permanently change back to metacity?

Note: I am on Ubuntu Jaunty and recently made a cleanup which apparently triggered the compiz format to become hegemonic. At first I did not noticed any slow down but now it has become a true annoyance.

Thanks in advance.

---

### Post by Boondoklife on 2010-06-05
If you just don't want to use compiz then set Desktop Effects to None, You can also enable meta city to do compositing (For the clear docks etc) with Ubuntu Tweak.

Ya this is good for an end user system, I have a script that I used to switch between the two on the desktops of our pcs.

---

