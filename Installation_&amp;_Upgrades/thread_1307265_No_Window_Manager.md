---
title: "No Window Manager"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by zerubbabel on 2009-10-31
I did a clean install of 9.10 on my Dell Latitude D830, then restored my home directory from a backup, and all was well. Then I plugged in my external monitor and switched to using that with the laptop screen closed. Still all was well. Then I had to go somewhere, so I shut down the laptop, unplugged my external monitor, and went on my way, expecting no problem.

When I got to my destination, I turned on my laptop, and after logging in I had no window manager, that is, no window decorations. After fiddling around, I found that if I went to System>Preferences>Appearance and switched the visual effects to Normal and then reverted back to None (my preference), then exit, the window dressings reappear. But when I logout and login again, they are gone, and I have to go through the same ritual to get them back.

---

### Post by morphodone on 2009-10-31
This is exactly the reason I don't use visual effects...

---

### Post by macogw on 2009-10-31
Are you saying Desktop Effects are re-enabled on each login?

---

### Post by zerubbabel on 2009-10-31
I'm saying that although I don't use the visual effects, I found that if I switch them on and then immediately off again, it evidently restarts the window manager, because then I get my window dressings again, i.e., the title bar, buttons, edges, resizing handles, etc. But I'd really rather not have to do this. Why doesn't the wm just start up when I login? Or maybe it starts up and then dies....

---

### Post by macogw on 2009-10-31
Ah, ok. I thought you were saying it had Desktop Effects enabled and no window decorations...

Hmm..if you hold down the alt key and click and drag a window, does it move? If so, the window manager is running but brokenly not decorating. If not, the WM isn't running. You can hit alt+f2 and type "metacity" to start it.  Try adding metacity to System -> Preferences -> Session -> Startup?

---

### Post by zerubbabel on 2009-10-31
No, Alt-click'n'drag window didn't work, so I guess it wasn't running. But adding metacity to the startup list worked. Thanks.

---

### Post by Faolan84 on 2009-10-31
Also, uninstall Compiz and make sure metacity is installed. You won't be able to use Windows Effect, but then again they were not working for you anyways. It wil preven the problem from ever happening again because the default action will be just to use metacity.

---

### Post by macogw on 2009-10-31
Faolan:
Compiz wasn't interfering. Metacity just wasn't starting.  That was my first question.

---

