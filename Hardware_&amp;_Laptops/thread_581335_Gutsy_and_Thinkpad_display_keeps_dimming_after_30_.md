---
title: "Gutsy and Thinkpad display keeps dimming after 30 secs"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by jsully1 on 2007-10-19
Hi All,

I just upgraded to Gutsy on my Thinkpad T60.  When it's not plugged in every 30 seconds or so the display automatically dims to the absolute minimum.  I can crank it back up but then it just goes right back - quite annoying.  It's also got something to do with the power management - if the display is set to bright and then I go to power preferences the screen instantly dims.  Worse yet, I have display brightness set to 100% for both AC and battery.  Any ideas?

Sully

---

### Post by DarthTibault on 2007-10-20
Same problem here on the Dell Inspiron 1520.

It is indeed VERY annoying

---

### Post by chender on 2007-10-20
this is not a problem ... this is a feature derived from Apple software.  Go into Power Manager preferences, and untick 'DIM' and all will be solved.

---

### Post by jsully1 on 2007-10-20
What sort of feature dims a laptop screen every 30 seconds *while* I'm actively using it.  Also, dim when idle is unchecked for both AC and battery, and like I mentioned as soon as I go into power preferences it dims the screen, which is strange in and of itself.  It also doesn't go back to bright without me manually setting the brightness with the keyboard commands, which is like 15 keystrokes.

---

### Post by andrewkk on 2007-10-20
For what it's worth, my ThinkPad X60 correctly resumes full brightness after detecting keyboard/mouse activity, much like a screen saver. I've turned off dimming in AC mode, but I rather like the extra power conservation while I'm running on a battery.

I'm glad to see that the power concerns of laptops are getting some attention in Gutsy.

---

### Post by jsully1 on 2007-10-20
OK I fixed it... this one is a fun one.
In power preferences, in AC options the slider is for "Set display brightness" and it's on 100%.  The slider for Battery options however is for "Dim display by", which seems backwards... I don't understand why they both wouldn't be brightness sliders, but oh well.

---

### Post by finnen on 2007-10-21
What's even more fun is that in the swedish translation both sliders are translated as "Set display brightness". Thanks for clearing this up for me, it was really annoying

---

### Post by mattskr on 2007-10-25
Wow. That is one of the worst UI flaws I've ever seen. I was about to go back to 7.04 when I came across this thread. Also running on a T60.

---

### Post by prizrak on 2007-10-27
> **mattskr said:**
> Wow. That is one of the worst UI flaws I've ever seen. I was about to go back to 7.04 when I came across this thread. Also running on a T60.

Oh geez you gotta be kidding me with this one. I have been on this problem for my g/f for MONTHS!!!!!! I suppose reading is fundamental in this case but that's a pretty bad UI design issue.

---

### Post by mptpro on 2007-11-04
Thanks jsull1!

Driving me crazy, and you found it!  Crazy UI.  I'm sure they'll fix it in the next release.

Just switched over from Win XP/Vista and am loving Ubuntu!

---

### Post by sdyson on 2007-12-08
Very confusing, I hope they do something about that!

---

### Post by blind.cripple on 2007-12-10
Mine is even worse.

When I first installed Gutsy, the dimming feature didn't seem to know if I was using AC power or battery power, and so continuously changed the brightness from high to low.  All the time.  The only fix I had was to log off, and then back on.  This would only last until the monitor automatically dimmed again.  VERY frustrating.  I turned the auto dim off and changed the slider settings, but it still occasionally goes crazy every now and then.  Is there an available update?

---

### Post by tepidarium on 2007-12-28
> **chender said:**
> this is not a problem ... this is a feature derived from Apple software.  Go into Power Manager preferences, and untick 'DIM' and all will be solved.

Not so.  I've got the same problem on my T60 thinkpad running gutsy.

I have unchecked "Dim when idle" on battery power and gutsy is *still *dimming the screen after 30 secs of idle.  Any way out of this?

---

### Post by shamrock_uk on 2008-01-14
> **tepidarium said:**
> Not so.  I've got the same problem on my T60 thinkpad running gutsy.

I have unchecked "Dim when idle" on battery power and gutsy is *still *dimming the screen after 30 secs of idle.  Any way out of this?

^^ Just checking, you did read the rest of the thread about the inconsistent UI, right? Slide the battery slider to the left, not the right. 

This has been filed as bug 155840:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/155840](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/155840)

---

### Post by Yellow Pasque on 2008-01-14
Yeah, I've never liked the power mgmt prefs UI. I use gconf-editor to manually access the settings.

Run (sudo?) gconf-editor and look under /apps/gnome-power-manager/ for all the power mgmt settings, including some that can't be accessed from any front-end dialogs.

---

### Post by EyesOnFire on 2008-03-18
God this was so annoying and the solution was soooo unintuitive.....

Thanks for tinkering....

---

### Post by nrgtek on 2008-03-27
> **shamrock_uk said:**
> ^^ Just checking, you did read the rest of the thread about the inconsistent UI, right? Slide the battery slider to the left, not the right. 

This has been filed as bug 155840:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/155840](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/155840)

Except for when your running on battery power and you already have your screen dimmed by 20% - then it idles and your back up to 100% brightness. 

Insanely annoying.

---

### Post by zymurgist on 2008-04-23
UI interface aside .. 

.. why does my display dim when idle even though I have unchecked the "dim on idle" box, and why doesn't it come back, when I start using the mouse and keyboard?

Again .. a T60 and Gutsy.

---

### Post by Yellow Pasque on 2008-04-23
See this thread
[http://ubuntuforums.org/showthread.php?t=667057](http://ubuntuforums.org/showthread.php?t=667057)

---

### Post by jsully1 on 2008-04-29
It seems that this bug was fixed in the version of Gnome that ships with Hardy.

---

### Post by bazder on 2008-07-06
> **jsully1 said:**
> It seems that this bug was fixed in the version of Gnome that ships with Hardy.

nope! don't think so, here we are in July'08 and all the annoying crap with laptop dimming is still happening with 8.04 on a Dell Latitude X1 which ran earlier versions of Ubuntu with NO PROBLEM!  No, there's nothing in the BIOS settings that has been changed ... it really seems to be a case of just flat out BUGGY CODE, period!  

geez this is disappointing.  The whole point of Ubuntu is supposed to be "it just works out of the box" and now my laptop is UNUSABLE !!!

good grief what a mess ...

---

