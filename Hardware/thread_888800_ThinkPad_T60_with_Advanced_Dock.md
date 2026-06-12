---
title: "ThinkPad T60 with Advanced Dock"
date: 2008-08-13
forum: Hardware
---

### Post by maxim0512 on 2008-08-13
I'm running a mostly out-of-the-box install of 32-bit Hardy with fglrx on a ThinkPad T60 with an ATI card.

After some tweaking, I've been able to get the machine to suspend and wake up whether the laptop is in the dock or out of the dock.

However, I am still having the following issues related to docking, undocking, and sleep:

1. The undock button on the ThinkPad Advanced Dock has no effect.

2. Undocking the T60 by simply removing it from the dock seems to work, but it doesn't know to switch video from the external VGA port of the dock to the built-in LCD. (Pressing Fn-F7 does work, however)

3. Docking the T60 doesn't know to switch video to the external VGA port of the dock. (Pressing Fn-F7 does work, however)

4. If I undock the T60, redock it, and suspend it, then when I wake it back up, the X session hangs. I can switch to a new virtual terminal (ctrl-alt-f1), but running "sudo /etc/init.d/gdm restart" gives me a "X is already running on display 0, do you want to try a different display" message. Choosing no causes the message to repeat. Choosing yes causes the system to hang.

I played around a little with the SUSE dockutils, but I didn't have much luck. Any thoughts on how to address any/all of these issues?

Thanks,
Max

---

