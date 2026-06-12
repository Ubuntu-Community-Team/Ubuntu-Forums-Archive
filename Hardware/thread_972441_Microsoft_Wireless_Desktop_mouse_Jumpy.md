---
title: "Microsoft Wireless Desktop mouse Jumpy"
date: 2008-11-05
forum: Hardware
---

### Post by Merk42 on 2008-11-05
Today, after the updates, my wireless mouse wants to constantly reset to just left of center.  I'll use it and have it in the corner and it'll instantly jump the off-center location.  Even now as I type I see it sort of twitching occasionally in the center.

Rebooting doesn't work, nor does resetting the wireless signal.

I don't know what package it came in, but the individual elements are:
Wireless Optical Mouse 2.0
Wireless MutliMedia Keyboard 1.0A
Wireless Optical Desktop Receiver 2.0A

---

### Post by Merk42 on 2008-11-08
Bump?

I even tried a wired (Logitec) mouse and a different USB port and it still jumps

---

### Post by Merk42 on 2008-11-09
Bump **AGAIN**

I even tried bootin with NO mouse and it jumps
Tried the LiveCD and it jumps


Tried the LiveCD of openSUSE and it was fine....
Help me with this or I can no longer use Ubuntu.

---

### Post by Merk42 on 2008-11-13
Well, might as well post in the "Goodbye Ubuntu" thread since my computer is pretty much inoperable and no one seems to have the same issue to help me.

---

### Post by Merk42 on 2008-12-29
Did a fresh install of 64-Bit and it still jumps

Can't wait until the free beta of Windows 7 because I guess I'll be switching to that.

Thanks for all of your non-help guys!

---

### Post by cserpentis on 2008-12-30
Had something like that in the old days, but, oddly enough - with windows and an ancient mouse. Looking at your description I'd opt for some problems with the port - as you've said, that you've tried different mice.

And by the way - are you using a laptop? Cause if you are, it could have just been your touchpad acting up.

---

### Post by Merk42 on 2008-12-30
> **cserpentis said:**
> Had something like that in the old days, but, oddly enough - with windows and an ancient mouse. Looking at your description I'd opt for some problems with the port - as you've said, that you've tried different mice.

I also said I tried a different port.  Currently it's plugged into PS/2 via an adapter, but tried multiple USB ports, and as I said earlier, even tried with no mouse plugged in at all.
> **cserpentis said:**
> And by the way - are you using a laptop? Cause if you are, it could have just been your touchpad acting up.

Desktop I built with an ASUS A8N-SLI Premium motherboard

I'll think I'll try dual booting openSUSE since the liveCD for that worked. I'm thinking Ubuntu's decision to go with HAL over Xorg for the mouse is my problem, but I'm not sure.


I'm also thankful that someone is at least trying to help me this time.

---

### Post by scaine on 2008-12-31
I take it this doesn't happen in Intrepid?  And if not, and you're "threatening" to leave Ubuntu forever because of this issue, it's a strange decision given that Jaunty is still in heavy development.  Your choice though.

Got to this thread because of your sig in another thread.  It's optimistic to think that Ubuntu Devs read these forums looking for bugs to fix.  They fix what has been reported on Launchpad.  Why don't you link your sig to your launchpad bug (I assume, possibly also optimistically, that you logged one), then other Jaunty testers who are experiencing the same problem can tick the "this also affects me" box and raise the profile of your problem.

Otherwise, enjoy Windows 7 when you eventually buy in early 2010...!

---

### Post by Merk42 on 2008-12-31
> **scaine said:**
> I take it this doesn't happen in Intrepid?  And if not, and you're "threatening" to leave Ubuntu forever because of this issue, it's a strange decision given that Jaunty is still in heavy development.  Your choice though.


No, this started in Intrepid, haven't used Jaunty.  Intrepid started the whole HAL instead of Xorg for mouse, which is my current theory on what is causing the problem.

> **scaine said:**
> Got to this thread because of your sig in another thread.  It's optimistic to think that Ubuntu Devs read these forums looking for bugs to fix.  They fix what has been reported on Launchpad. How would I go about filing one, especially since this affects Intrepid (may or may not affect Jaunty)  I mean, I don't know of any error messages I could show with my bugreport.

> **scaine said:**
> Otherwise, enjoy Windows 7 when you eventually buy in early 2010...!

I will still try the beta when it is released, and if it's like Vista, and I find a bug, I get a copy for free.  In the meantime, I will be switching to a different distribution.  Most likely openSUSE like I said.  [I just need to see if I'll run into any issues using the same /home partition for a dual boot of Ubuntu and openSUSE.](http://ubuntuforums.org/showthread.php?t=1026148)

---

### Post by scaine on 2009-01-02
Regardless of not having a package to file against, I'd still raise a bug in launchpad, possibly against Xorg initially, to see if you get any feedback from the devs about what might be causing it.

Bugs for Intrepid here : [https://bugs.launchpad.net/ubuntu/intrepid](https://bugs.launchpad.net/ubuntu/intrepid)

But a [quick search for "mouse"]("https://bugs.launchpad.net/ubuntu/intrepid/+bugs?field.searchtext=mouse&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") didn't come up with much...

Good news about your (potentially) free beta though.  I didn't know that Microsoft ran the program that way.

I think you'll be lucky to avoid issues with dual-booting your distro with the same /home partition.  I've given up on that idea after too many things develop weird bugs that are solved by starting from scratch.  I've split my disk into three sections now - a 10Gb / partition, a 10Gb /home partition and everything else (about 200Gb) lives on a third partition which is mounted into /media/Data and I symlink it into my home directory as /home/scaine/Local.  That takes a lot of the pain out of rebuilding my /home partition on the rare occasion I have to, and one day I'll maybe think about multiple /home partitions - one for each distro I try (although I'm pretty much settled on Ubuntu these days).

Good luck with the mouse issue.  Sorry I couldn't help.

---

### Post by snkiz on 2009-01-08
If it helps to diagnose I have the same keyboard and mouse, and intripid is the first ubuntu that my mouse worked perfect, side scroll and all. Just have to get a new sound card before I upgrade because the old awe driver is borked and its to old to bother filling a bug.

---

### Post by pakman117 on 2009-02-09
Hi Merk,

I just experienced this same issue without changing anything in my setup.  I turned my computer off this morning when it was working great.  Then, when I turned it on this evening, the mouse was jumpy/reset to a random point.  Anyway, the solution to my problem was to just **unplug every USB device**.  When I unplugged my Xbox Controller connected via special adapter, the problem went away.  I do not have software installed to control this device.  I got the idea from [this]("http://ubuntuforums.org/showthread.php?t=748581&page=2") forum post where the author unplugged his Wacom tablet.  Thus, give it a try and unplug everything from your computer while the mouse is acting up.  As soon as you unplug the cause, the mouse should resume operation (at least, that's how it worked for me.)

Hope I got here before any drastic action occurred ;)

---

