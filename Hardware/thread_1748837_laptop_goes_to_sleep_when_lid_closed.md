---
title: "laptop goes to sleep when lid closed"
date: 2011-05-04
forum: Hardware
---

### Post by LuaMadman on 2011-05-04
Hi

My Asus K50i goes to sleep when I closes the lid.
I have set all options to nothing in Xfce Power Manager.
It's set to sleep the mointor after 10 / 5 minutes.

But it goes to sleep within 30 seconds when i close the lid.

Running Xubuntu 11.04

Did not have this problem on 10.04 or 10.10.

---

### Post by soumen97 on 2011-05-04
Try updating the kernel, they released some new kernel versions which may have bug fixes for these type of problems.

---

### Post by LuaMadman on 2011-05-04
How do I do that?

Update manager says i'm up to date.

---

### Post by LuaMadman on 2011-05-15
I solved it!

Thought i would write some more info about the problem, if anyone else get's it.

All my settings in Xfce powermanagment was set to do nothing when it comes to the computer. The monitor was set to sleep after 15 minutes. Yet it got suspended. But not always. Some times it worked as it should.

I almost all the time have the ac cable connected. But today I disconnected it, and noticed that I have 2 battery icons. My guess was that xfece somehow have bugged, but then i noced that they report on battery info from them was diffrent. Rightclicking on the one I didn't recongnize and selecting prefernce got me the GNOME power manager.
It was that was set to suspend.

I haven't installed it, so I guess it came with some other program or update.
Uninstalled it from package mananger, and now it works perfect.

GNOME icon didn't show up when using the AC cable, only when running in battery it showed.

---

