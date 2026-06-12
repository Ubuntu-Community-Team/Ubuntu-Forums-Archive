---
title: "Blanking the laptop screen"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by straffaren on 2007-03-12
Hi all!

I just switched from Windows XP to Ubuntu Edgy on my Dell Inspiron 6000. It's equipped with a Radeon X300 card and I'm using Beryl as window manager and everything's working great - except for one thing. At work, I hook it up to an external monitor and close the laptop lid. I've noticed that the computer was getting warmer than usual and I've discovered why: the laptop screen doesn't go blank when I close the lid. I fiddled with Preferences->Power Management and set it to "Blank Screen" but unfortunately this makes both screens go blank when I close the lid. I'd like the setup to work like this:

1) No external monitor connected - use the default laptop screen.
2) External monitor connected - use only external monitor, laptop screen is blank.

Is this possible? I've played a little with the aticonfig tool, but all I've managed to do so far is create a large two-monitor desktop (ie not in clone mode) but Beryl doesn't work with that setup and both screens still go blank when that power option is selected.

Anyone out there with a solution?

---

### Post by straffaren on 2007-03-13
I've managed to manually switch between my laptop and my external screen using the EnableMonitor option in my xorg.conf. But that requires me to kill X whenever I want to blank one of the screens and there has to be a better way to switch displays, right?

...right?

---

