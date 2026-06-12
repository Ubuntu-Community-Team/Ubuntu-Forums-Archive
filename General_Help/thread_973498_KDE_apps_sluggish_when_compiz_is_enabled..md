---
title: "KDE apps sluggish when compiz is enabled."
date: 2008-11-06
forum: General Help
---

### Post by LunaEqualsLuna on 2008-11-06
I'm using GNOME and recently I've noticed that KDE apps have become very sluggish anytime compiz is enabled. I'm not sure if its any particular compiz settings that are causing it, but if i revert to metacity, KDE apps work perfectly fine. I'm not sure exactly at what point the sluggishness started, but it renders a lot of KDE apps useless now and if anyone has any idea what would cause this it would be a great help.

The main issues are:
Scroll bars: If i use the scroll bar in any kde app, it responds like 3 seconds later.

If i maximise or unmaximise a KDE window it responds 3 seconds later.

In general, a lot of operations performed in a kde window have a time lag attached to them which is very annoying to say the least.

I've reinstalled compiz and my kde apps and kcontrol and nothing seems to work.

Help?

---

### Post by ezramorris on 2008-11-06
> **LunaEqualsLuna said:**
> I'm using GNOME and recently I've noticed that KDE apps have become very sluggish anytime compiz is enabled. I'm not sure if its any particular compiz settings that are causing it, but if i revert to metacity, KDE apps work perfectly fine. I'm not sure exactly at what point the sluggishness started, but it renders a lot of KDE apps useless now and if anyone has any idea what would cause this it would be a great help.

The main issues are:
Scroll bars: If i use the scroll bar in any kde app, it responds like 3 seconds later.

If i maximise or unmaximise a KDE window it responds 3 seconds later.

In general, a lot of operations performed in a kde window have a time lag attached to them which is very annoying to say the least.

I've reinstalled compiz and my kde apps and kcontrol and nothing seems to work.

Help?

Hi,
I use GNOME, and I have had many problems with the responsiveness of programs when compiz or compiz-fusion was enabled, mainly the laggy scroll bars issue.

There most likely isn't really a proper solution to these sorts of issues, until computer hardware, Linux graphics drivers, KDE/GNOME and compiz[-fusion] gets better.

In the meantime, either don't use it, or if you insist, you could try disabling various plugins to see if they make a difference. You could start with resource heavy plugins such as the desktop cube and/or developmental or new plugins.

I used compiz-fusion for several months and loved it, apart from the slow response of programs. I temporarily disabled it so I could actually scroll web pages smoothly, and it stayed that way. Now I've completely removed it.

This probably wasn't the answer you were looking for at all, but just some food for thought.

---

### Post by LunaEqualsLuna on 2008-11-07
Have you always had this issue?

It wasn't like this before, an update somewhere along the line caused this but i have no idea what update that could be :(.

compiz and gnome and kde all were best of friends up until a few weeks ago :(

oh well i might have to consider upgrading to intrepid and see if that sorts things out, and once i get a working combo of drivers, lock them so they never change.

---

### Post by ezramorris on 2008-11-08
> **LunaEqualsLuna said:**
> It wasn't like this before, an update somewhere along the line caused this but i have no idea what update that could be :(.

Ah, I didn't realise this. I thought you'd just switched to KDE and it went bad.

The only thing I can think of right now is checking in 'Hardware Drivers' to check if your accelerated graphics driver really is enabled properly.

A number of occasions when compiz went <really> bad, it turned out that the restricted driver had disabled itself. No idea why, but enabling it usually put it back like it was before.

---

