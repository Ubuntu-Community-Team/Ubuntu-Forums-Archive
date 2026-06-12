---
title: "Slowness when dragging a tab in Google Chrome"
date: 2011-01-04
forum: Hardware
---

### Post by matiasjrossi on 2011-01-04
Hi all,

I'm using Google Chrome stable (from Google's PPA) in Maverick.
I run with the default open source drivers for ATI.
My card is the Mobility Radeon HD 4570 that comes with Dell Studio 1555.

Whenever I detach a tab from a Chrome window, i have to wait about 4-5 seconds before the semi-transparent thumbnail of the tab appears. In that slice of time, the screen stops refreshing, making this small bug really annoying. After I regain control, dragging the semi-transparent picture feels smooth.

I use compiz as window manager.

The question is:
1) Is someone else experiencing the same? Under which same/different conditions?
2) Has someone been able to workaround this? Or does someone have a clue of what can be causing this?

Thanks,
Matías.

---

### Post by cipherboy_loc on 2011-01-04
I just installed the Chrome Daily Build (from the PPA), and when running under Fluxbox, I see no noticeable delay. 

My graphics card is:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

```
and I am currently using two monitors (the laptop monitor and an external monitor).

Try upgrading to the daily builds, and see if that helps any.

Cipherboy

---

### Post by matiasjrossi on 2011-01-05
Thanks for your answer.

I understand your point, but i've done a little more testing and appears to be a problem in the interaction of the video hardware/driver with chrome, because in the same installation with Catalyst drivers the problem disappears.

I'm not willing to use catalyst. The open source drivers give me a better set of features.

Any other idea, anyone?

Thanks again,
Matías.

---

### Post by CO_Shifty on 2011-01-27
I have the same problem, and Catalyst drivers are not an option since I have a legacy Radeon. 

I'll add another grievance; When dragging a tab between windows it doesn't pick the window you are hovering above. So, if you have a window partially covering another with multiple tabs you wont be able to place the tab in the middle area.

I desperately would like help with both of these issues. Thanks in advance.

---

### Post by CO_Shifty on 2011-01-28
Bump

---

### Post by matiasjrossi on 2011-02-01
Bump ;)

---

### Post by matiasjrossi on 2011-02-19
Reisntalled maverick from the ISO. After the first boot installed:

* bcmwl restricted driver
* chromium

Launched chromium and dragging a tab out of the window worked really smooth.

After restart something was updated (Indicator Applet Session showed in red). Before installing or changing any setting, the chromium tabs are slow again.

I will try to investigate further.

Matías.

---

### Post by matiasjrossi on 2011-02-21
I've added xorg-edgers' radeon/gallium/mesa testing ppa ([https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)) and now the tabs dettach smoothly.

Marking as solved.

---

### Post by CO_Shifty on 2011-02-23
> **matiasjrossi said:**
> I've added xorg-edgers' radeon/gallium/mesa testing ppa ([https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)) and now the tabs dettach smoothly.

Marking as solved.

I can confirm that it works. Detaching tabs and putting them back is smooth with the drivers from the ppa.

Thank you very much! You deserve a beer :),

Shifty

---

