---
title: "Is Unity 3D required to use Compiz Grid?"
date: 2012-01-28
forum: Hardware
---

### Post by rhuppert on 2012-01-28
[LIST]
[*]Running 11.10 with Geforce 8400 GS.
[*]Installed additional Nvidea graphics drivers.
[*]Compviz Grid enabled, but not working.
[*]Unity support test says "no" for not blacklisted and Unity 3D support.
[/LIST]
Am I SOL for running grid with my current configuration or do I have options?


Thanks.

---

### Post by grahammechanical on 2012-01-28
There are two desktop environments with 11.10. Unity 3D (called Ubuntu at the log in screen) uses Compiz as the window manager. But Ubuntu 2D uses Metacity as the widow manager. The Compiz Configuration Settings Manager will only work with Ubuntu/Unity 3D because it cannot work with Metacity.

Try logging out and clicking the cog icon. Do you see Ubuntu as an option? Or only Ubuntu 2D? If you can select Ubuntu then you will find that the Compiz Grid may now be working.

Regards.

---

### Post by rhuppert on 2012-02-03
@grahammechanical - thanks for the help.

Indeed I logged in under Ubuntu (3D) and, while I can enable Compiz Grid, it does not work as advertised.  IOW, the key bindings for window placement don't have any effect.  Kind of strange.

I suppose Python Window Manager is an option.

---

