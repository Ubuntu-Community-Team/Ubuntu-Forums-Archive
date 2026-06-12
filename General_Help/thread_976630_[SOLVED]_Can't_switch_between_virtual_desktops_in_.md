---
title: "[SOLVED] Can't switch between virtual desktops in 8.10!"
date: 2008-11-09
forum: General Help
---

### Post by Irwin J. Finster on 2008-11-09
I just installed 8.10 and it seems I can't switch between my virtual desktops. Nether by clicking on them in the taskbar, nor by dragging open windows to the side of the screen. What could be wrong?

---

### Post by drs305 on 2008-11-09
As a start, check this and see if the number is greater than 1:
```
gconf-editor /apps/metacity/general/num_workspaces
```

If it isn't, change it to the number you desire and add "workspace switcher" to your panel (Rt Click, Add to Panel, Workspace Switcher) if you desire.

---

### Post by 73ckn797 on 2008-11-09
If there is the icon at lower right panel, right click and designate number of desktops. If compiz is installed & running, see if desk wall is activated. I had an issue with switching desktops, would not work, after switching to desktop cube.

---

### Post by Irwin J. Finster on 2008-11-09
Thanks both for your help! It is actually as you say, when Desktop Cube is activated I can't switch, only with wall. But I would love to have the Cube. Do you know of any way to resolve this issue?

Thanks!

---

### Post by 73ckn797 on 2008-11-09
That is something that I will look into. If a solution is found I will reply back. Do the same yourself.

Do a search using any key word related to this and you might find the answer in the forums.

I will check for any bug reports on Launchpad.

---

### Post by 73ckn797 on 2008-11-09
There is a bug report for this issue. Will have to await any solution.

---

### Post by mc4man on 2008-11-09
Two things to ck. With desktop cube enabled you also must enable 'rotate cube' and the desktops must be 'columns'

---

### Post by Irwin J. Finster on 2008-11-09
@ mc4man HOLY ****! That was it! NOw it works Beautifully! Thank you so much all of you!

---

