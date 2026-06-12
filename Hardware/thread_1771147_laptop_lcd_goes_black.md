---
title: "laptop lcd goes black"
date: 2011-05-30
forum: Hardware
---

### Post by zedkin on 2011-05-30
Hi everybody,
I've used some linux based OS in the past, like ubuntu, kubuntu, puppy linux, dsl, debian, red hat....but for some software that I use for work, I was never been able to fully migrate from windows.
So with the time I left linux behind and only installed Windows 7 in my laptop. But now I want to install kubuntu again. I've downloaded the newest iso and used wubi to install it from windows.
Then I reboot my laptop and when I selected to boot my new OS, the screen went black. I connected an external monitor and everything worked fine, I even open the monitor config and it shows me my laptop lcd as the primary screen.
I though it was a KDE problem, so I burned an ubuntu iso to run live, and the same thing happened, I select to go live, and when the interface shows up, my lcd backlight goes off.....

Sometime ago I've installed ubuntu 9.04 and ubuntu 9.10 and everything worked fine.

If it's possible, I don't want to reinstall.....

thanks for your time...

Zedkin

ps: my laptop model is: emachines e725

---

### Post by Zorael on 2011-05-30
Could you copy and paste the terminal output of **xrandr**? I imagine you can do that with your other monitor connected.

---

### Post by zedkin on 2011-05-30
Hi,
I semi solved the issue....
I read over there that theres a bug with Intel Mobile Series 4's graphic cards....
Backlight doesnt work properly....to solve it I edited rc.local and inserted this:
```
setpci -s 00:02.0 F4.B-00
``` before the "exit 0" line....
But in any case that the screen turns off (ex. when inactive for some minutes) it doesnt goes on again.
There's someway to fix this bug permanent?

---

### Post by Zorael on 2011-05-30
That sounds like a real bug to me. If you found a bug report that seems to cover the same issue you're getting, subscribe to it and click This Affects Me uptop. If there doesn't seem to be one, file a new bug report.

Remember, unreported bugs can only be fixed by accient.

---

