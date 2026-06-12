---
title: "firefox 3 ubuntu 8.10 right click issues...."
date: 2008-11-04
forum: General Help
---

### Post by phoenix_snake on 2008-11-04
I am not sure if anyone has this on firefox 3 but I only have this on the linux version of firefox 3.

so when I right click on a few links, instead of a menu appearing sometimes a new tab opens up itself, a bookmark link, save address thing or once in a evolution email opens up? scrolling is jerky as well.

I am not running this with compiz, but what kind of a problem is this????????????

oh yeah I tried opera for linux, opera is horrible on ubuntu too, its too slow for me, only on linux and flash is horrible for me on ubuntu with opera.

any suggestions here either?

---

### Post by zeigfried on 2008-11-04
I'm experiencing the same thing. 
Sometimes 8.10 acts as I right-clicked then left-clicked in sequence and I ain't doing that.
In 8.04 everything was normal.

Cheers

---

### Post by Mr_JMM on 2008-11-04
I'll third this.

At first I thought it was some kind of programmed short so spent ages trying to replicate it. Sadly not.

---

### Post by phoenix_snake on 2008-11-04
as usual another ubuntu/linux problem, the windows and OS X version of firefox have no such problem, I just tried them to check again....

---

### Post by bryncoles on 2008-11-04
i also get this issue, though i can live with it most of the time. a littly annoying though...

---

### Post by phoenix_snake on 2008-11-04
> **bryncoles said:**
> i also get this issue, though i can live with it most of the time. a littly annoying though...
I hate it seriously, I thought firefox was open source, what went wrong here and this issue exists on every linux distro with firefox 3 I have tried :(

---

### Post by Xavura on 2008-11-04
Maybe you guys have some kind of mouse gesture plug-in enabled without realizing it? :p

---

### Post by kaibob on 2008-11-04
This problem can be caused by an extension. The best way to check this is to temporarily create a new Firefox profile by entering the following in a terminal window:
```
firefox -ProfileManager
```

You can also check by starting Firefox in safe mode: 

```
firefox -safe-mode
```

Just be sure not to make the changes permanent.

---

### Post by phoenix_snake on 2008-11-04
no the only extension I have is downloadhelper with the default theme and no compiz on right now and I checked to make sure it doesn't happen with firefox 2

---

### Post by phoenix_snake on 2008-11-04
alright so is there any other **useful or good** out there for me to try on linux cause both firefox and opera on linux suck.

any idea when google chrome comes out?

---

### Post by zeigfried on 2008-11-04
It seems like this is not happening only in firefox for me. 
After some time the issue happens in every app since I upgrade to 8.10.

---

### Post by johnnylavah on 2008-11-05
i am experiencing the same thing...

---

### Post by brandon88tube on 2008-11-05
Yep, same problem here

---

### Post by pelle.k on 2008-11-06
No need to confirm this any more. It's a knwon bug.
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295)

---

### Post by phoenix_snake on 2008-11-06
> **pelle.k said:**
> No need to confirm this any more. It's a knwon bug.
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295)
this bus is so old but still hasn't been fixed?

---

### Post by zeigfried on 2008-11-06
Any fixes / workarounds?

---

### Post by brandon88tube on 2008-11-06
I don't think any fixes have been found yet. If there have been please share.

---

### Post by pelle.k on 2008-11-06
> this bus is so old but still hasn't been fixed?
Yep. It's a BIG pain in the ***. But to be fair, it's showing up in some windows installations as well it seems. So i don't think it's entirely linux specific, even though it seems more common under this platform.
It seems it happens when the system is under some load.

> Any fixes / workarounds? 
Yes, if you hold the left mousebutton (or right, depending on your preference in X/gnome/kde) until the menu is actually drawn, you get the correct behaviour.

---

### Post by brandon88tube on 2008-11-06
> **pelle.k said:**
> Yep. It's a BIG pain in the ***. But to be fair, it's showing up in some windows installations as well it seems. So i don't think it's entirely linux specific, even though it seems more common under this platform.
It seems it happens when the system is under some load.


Yes, if you hold the left mousebutton (or right, depending on your preference in X/gnome/kde) until the menu is actually drawn, you get the correct behaviour.


Really? Well I am going to have to try that from now on and see what happens. If it works I can live with that for now as long as it stops selecting random commands from the right-click menu.

---

### Post by phoenix_snake on 2008-11-06
> **pelle.k said:**
> Yep. It's a BIG pain in the ***. But to be fair, it's showing up in some windows installations as well it seems. So i don't think it's entirely linux specific, even though it seems more common under this platform.
It seems it happens when the system is under some load.


Yes, if you hold the left mousebutton (or right, depending on your preference in X/gnome/kde) until the menu is actually drawn, you get the correct behaviour.
no, it doesn't happen any under windows or OS X for me, I think I posted earlier I surfed using firefox 3, the latest version under xp sp3, vista and OS X for 2 hours and nothing happened, I will take the system under load consideration and try do some heavy stuff under the other OS's and report any news.

is google going to make chrome for linux?

---

### Post by pelle.k on 2008-11-07
> no, it doesn't happen any under windows or OS X for me
But i did point out **just** that - it is less common under windows.

EDIT: if you're just out for another browser, install epiphany (the official gnome browser) or opera.

---

### Post by phoenix_snake on 2008-11-07
> **pelle.k said:**
> But i did point out **just** that - it is less common under windows.

EDIT: if you're just out for another browser, install epiphany (the official gnome browser) or opera.
not less common, it doesn't happen at all :confused:

---

### Post by stinger30au on 2008-11-07
firefox version 3.0.3 does this in 8.04 and 8.10 on 2 different pc's i have 


when right clicking , hold down the mouse button till the menu appears then move and select what you want

works for me


i used to have the same isses untill i found this

---

### Post by phoenix_snake on 2008-11-07
> **pelle.k said:**
> But i did point out **just** that - it is less common under windows.

EDIT: if you're just out for another browser, install epiphany (the official gnome browser) or opera.
oh yeah I would install another browser but the last update broken my ethernet and network manager no longer starts, any help on that, do u need to the output of the command in a terminal? 

[http://ubuntuforums.org/showthread.php?t=973395](http://ubuntuforums.org/showthread.php?t=973395)

---

### Post by pelle.k on 2008-11-07
> not less common, it doesn't happen at all
How could i possibly know about your situation in great detail. What i'm saying is that it does happen, for **other people**. To clarify, the problem apparently **does** exist under windows as well (according to the bug report). If you don't have it, good for you.

> oh yeah I would install another browser but the last update broken my ethernet and network manager no longer starts, any help on that, do u need to the output of the command in a terminal?
You should start a new thread for that. I'll be glad to help if you put a link to it though.
EDIT: i'm too slow :) just noticed the link...

---

### Post by phoenix_snake on 2008-11-07
> **pelle.k said:**
> How could i possibly know about your situation in great detail. What i'm saying is that it does happen, for **other people**. To clarify, the problem apparently **does** exist under windows as well (according to the bug report). If you don't have it, good for you.


You should start a new thread for that. I'll be glad to help if you put a link to it though.
EDIT: i'm too slow :) just noticed the link...
other people? aren't linux devs supposed to be able to fix it pretty fast, I mean its usually noticeable on linux more right? why do u think that is?

the default browser shouldn't have bugs like these....

---

### Post by pelle.k on 2008-11-07
> other people? aren't linux devs supposed to be able to fix it pretty fast
There is no such guarantee. If it's even a linux **kernel** problem that is.

> the default browser shouldn't have bugs like these.... 
I'm not particularity enjoying this bug, but complaining doesn't help. It's open source. Help fix it.

You're blowing off steam. That's OK, but this is a support thread so can we please stick to the "support" theme of it?

---

### Post by phoenix_snake on 2008-11-07
help fix it? thats not my job, sorry the devs do that :)

---

### Post by TiniBits on 2008-11-12
simple solution to this problem is installing a firefox addons for [mouse gestures]("https://addons.mozilla.org/en-US/firefox/addon/39"), or use middle click.

---

### Post by alisonjo2786 on 2008-11-13
this has happened to me for months with Hardy (and Firefox 3).  it's obnoxious.  basically it's as if it's picking a choice from the right-click-menu at random and executing that command (although I don't know how random it is b/c most of the time I get "send email", save as, new tab, or new window, but anyway...)

> **zeigfried said:**
> Any fixes / workarounds?

The click-and-hold suggestion may work, I'll have to try that.  **BUT, my suggestion/what I've been doing** is I went to Edit > Firefox Preferences > Applications and set pretty much everything to "Always ask", so at least it wouldn't start trying to open an email every other second (which is especially annoying for me b/c my computer is so unbelievably slow and stupid) -- and I did the same thing for any add-ons I installed that included additions to the right-click-menu.

Hope that helps!

---

### Post by alisonjo2786 on 2008-11-13
> **pelle.k said:**
> I'm not particularity enjoying this bug, but complaining doesn't help. It's open source. Help fix it.

Understood, but, what can folks like me/us do to help?  I don't mean that in a contrarian way, I'm being very sincere.  What **exactly** can/should I do to help?  Though I'm not super new, I'm too new to know what to do, but whatever would help, I'll do it.  This is an obnoxious bug.

---

### Post by pelle.k on 2008-11-13
> What exactly can/should I do to help?
Well, there are no rules to follow. You could help out by learning C/C++ and help out in the long run. People just want quick fixes, but no one wants the long time commitments necessary to help create a great product/application.
You could also experiment by using different firefox builds, and look for signs of that same bug, and draw conclusions upon that. You could learn how the XUL framework in mozilla works, and how that is tied to GTK (in this case), and see if you can reproduce the problem on your own.
Join the bugtracker, help them confirm fixes/patches, and/or find duplicate bugs.
You can debug applications using gdb/strace.
Find out what "firefox-gnome-support" does, and if it can be related to the problem.
Install the latest sources and see if the problem still exists.

The thing is, you don't *have* to be an expert. I've patched a recent bug in rhythmbox, and sent the patch to the gnome bugtracker, and i've never done any programming in C. It takes a lot of patience, and you have to think and get involved, but if that is what it takes, then so be it.
So, in short, be creative, use your imagination.
I hope that'll help you get started. Good luck.

---

