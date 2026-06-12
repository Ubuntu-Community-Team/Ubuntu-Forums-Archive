---
title: "Random Firefox crashes in Kubuntu 8.10"
date: 2008-11-12
forum: General Help
---

### Post by Mamono on 2008-11-12
So I wiped out Windows and installed Kubuntu on my work desktop.  I've been using Kubuntu on my home desktop (running KDE 3.x) for over a year now and haven't experienced any problems.  Well, this was my first foray with 8.10 and (with the exception of a short test some time ago) KDE 4.  Everything works fine except for the the fact that Firefox will just randomly crash.  It happens usually at least twice per day.  I chalked it up to something strange that I need to debug, a minor annoyance but not a deal-killer.

Well, last night I installed Kubuntu 8.10 on my wife's laptop.  To my surprise, Firefox crashed randomly there, too.  This was even before I could get any extensions or anything installed (indeed, it crashed as I went to just SEARCH for Adblock Plus.)  Being that these are both fresh installs it is unlikely that there is some old corrupt profile issue going on.  They are also two different systems.  My work desktop is a Dell Optiplex 745 and my wife's laptop is a Dell Latitude D830.

Anyone else experiencing any Firefox oddities with Kubuntu 8.10?

---

### Post by dan.s.ward on 2008-11-16
Yes. I'm experiencing the same behavior. It is totally random though. Very difficult to debug. Fortunately, it does save my session so I just need to restart it to get back to what I was doing. But, its very annoying just the same.


*********** After a little bit of investigation ********************

Its not random at all. I can force the crash by scrolling quickly with my wheel. I'm using a Logitech TrackMan Wheel mouse. As long as I scroll slowly using the wheel or at any speed using any other method it is fine. But if I attempt to scroll quickly with the wheel, Firefox terminates abruptly. There are no error messages. It just just disappears.

I am primarily a PHP and .NET developer so I'm not really sure where or what to look for that may provide more technical details that may be helpful to find the source of the problem. If someone could tell me what information to look for and how and where to retrieve it, I will post it.

---

### Post by dan.s.ward on 2008-11-18
Today's update seems to have fixed the issue for me.

---

### Post by automaton26 on 2008-11-21
My firefox 3.0.3 vanishes quite frequently, usually when I'm scrolling with the mouse, but sometimes when I scroll the scrollbar instead.

It makes posting on these forums very difficult !

I've reported it to launchpad.

---

### Post by pbhj on 2008-11-23
Same for me, random crashes caused by scrolling.

Using 8.10 64-bit.

I've got FF 3.0.4 which appears to have reduced the instances, however it may also be the disabling of noscript add-on. I was seeing very high CPU usage on scrolling too.

---

### Post by automaton26 on 2008-11-24
3.0.4 didn't solve it for me, unfortunately.

---

### Post by automaton26 on 2008-11-24
I've also tried installing the "System Settings...Appearance...GTK Styles and Fonts...Firefox scrollbar fix", but it may not be related.

UPDATE: That didn't work either.

---

### Post by sweetmiracle on 2008-11-26
This has been making me crazy for a while now...

Thanks for the ideas!

---

### Post by michaelzap on 2008-11-26
I was also plagued by this using regular (Gnome) Ubuntu after upgrading to Ibex. I reinstalled Ibex from scratch and the problem disappeared, but removing winbind may have been all that I needed to do. More info here:
[http://ubuntuforums.org/showthread.php?p=6178246#post6178246](http://ubuntuforums.org/showthread.php?p=6178246#post6178246)

---

### Post by automaton26 on 2008-11-27
Thanks for the link.

I _don't_ think I have Samba/winbind (fresh Intrepid install), but I _do_ have a static IP. I have 32-bit kubuntu with open source ATI drivers.

I've also tried using "NoScript" add-on, but it still happened.

**17/01/2009 Update**
Still happens :( despite looking at many other threads. I'm currently trying it without the "Flashblock" add-on.

---

### Post by flanagan on 2008-11-27
I also had Firefox crashing after upgrading to Intrepid, but for me, it seemed to only happen when scrolling quickly on any page containing Flash content. I also had the mouse completely freezing up on me several times per day.

I had been using a cheap Microsoft USB mouse. (Cheaply made that is; not necessarily inexpensive). I went out and bought a Logitech cordless variety, and I have not had either problem in the three days I have been using the new mouse.

At least for me, it was a device problem. Your mileage may vary. The good thing is that I think I have finally rid my system of its last MS product.

---

### Post by automaton26 on 2008-11-29
Neither of my solutions worked, but you could be right - it *may* be just when scrolling quickly on pages containing Flash content.

I use the FlashBlock add-on, and I have a Microsoft mouse.

I'll try removing one/both of those and report back.

---

### Post by automaton26 on 2008-12-02
Following the suggestions in the following post finally seemed to cure the problem for me:

[http://ubuntuforums.org/showpost.php?p=6589866&postcount=16](http://ubuntuforums.org/showpost.php?p=6589866&postcount=16)

---

### Post by pbhj on 2008-12-08
I think the upgrade to 3.0.4 has fixed things for me.

---

### Post by dan.s.ward on 2008-12-16
**Status Update:** My Firefox crashes started up again and became more frequent and random. It even started crashing when I had left it idle or while I was using another program.

**Conclusion:** I'm convinced that Firefox is a Windows application. It only works well until you start to rely on it.
[B]
Problem Solved:[/B] I switched to SeaMonkey.

**Farewell Firefox!** ):P It was fun while it lasted.

---

### Post by sweetmiracle on 2008-12-18
I searched around a bit and found a suggestion that may help: try adding [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") to Firefox. I've had it on for a few days now, and the crashes and freeze-ups have ceased.

[Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") is supposed to work, too, but I haven't tried it.


Hope it helps!

---

