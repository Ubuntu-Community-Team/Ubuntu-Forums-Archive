---
title: "nVidia Ti 4400 effects and dual monitor not working"
date: 2008-09-05
forum: Hardware
---

### Post by /usr/bin/hacked? on 2008-09-05
I am having major problems with the nVidia drivers that are included with Ubuntu, and from the nVidia website. I want to run two LCDs, @ 1280x1024, and I got it working once, perfectly and it was gorgeous (compiz, cube, squiggly windows, everything). Then I restarted, and it went away, and I haven't gotten it back yet. I've used envyng (each of the 3 drivers it offers) all 3 of the drivers from the nvidia website, and the nvidia-glx, -legacy, and -new drivers from synaptic. none of them have worked, although I was able to get dual screen once, I forget how (no effects though). I now am not using the "Hardware Drivers" driver, or the official ones, and I haven't installed any from synaptic. I'm running at 1280x1024, but it's kind of slow, and absolutely no graphics support. I was wondering if there is a special fix for this, I was unable to find anything, and it really bugs me that I had it working fine, so I know the card can do it, but not being able to get it going again is frustrating. *sigh*

---

### Post by overdrank on 2008-09-05
> **/usr/bin/hacked? said:**
> I am having major problems with the nVidia drivers that are included with Ubuntu, and from the nVidia website. I want to run two LCDs, @ 1280x1024, and I got it working once, perfectly and it was gorgeous (compiz, cube, squiggly windows, everything). Then I restarted, and it went away, and I haven't gotten it back yet. I've used envyng (each of the 3 drivers it offers) all 3 of the drivers from the nvidia website, and the nvidia-glx, -legacy, and -new drivers from synaptic. none of them have worked, although I was able to get dual screen once, I forget how (no effects though). I now am not using the "Hardware Drivers" driver, or the official ones, and I haven't installed any from synaptic. I'm running at 1280x1024, but it's kind of slow, and absolutely no graphics support. I was wondering if there is a special fix for this, I was unable to find anything, and it really bugs me that I had it working fine, so I know the card can do it, but not being able to get it going again is frustrating. *sigh*

Hi and if the drivers are failing after restart you may try what PmDematagoda suggest here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by /usr/bin/hacked? on 2008-09-11
I tried that, and I got the dual screen working, but the compiz and all the cool effects are not working. I also have to start metacity manually each time I log in. (I have it set to a startup service (metacity --replace)). While the computer is usable in this configuration, I would like it to be more "uber". Do you need the outputs of any commands or files like xorg.conf?

---

### Post by overdrank on 2008-09-11
> **/usr/bin/hacked? said:**
> I tried that, and I got the dual screen working, but the compiz and all the cool effects are not working. I also have to start metacity manually each time I log in. (I have it set to a startup service (metacity --replace)). While the computer is usable in this configuration, I would like it to be more "uber". Do you need the outputs of any commands or files like xorg.conf?

Ok could you explain why you have to use metacity replace command?
Can you use the nvidia settings as I assume yes due to the dual monitors?
You may also look at compiz-check
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by /usr/bin/hacked? on 2008-09-11
I have to use "metacity --replace" because when I log in, there is no window manager running. There are no title bars on the windows, but I can still open and close some programs, I just can't move them around, and the "X" in the corner isn't there, so I have to choose file > quit.
I can use nvidia-settings, and it seems to work fine, except that there are no effects.
As soon as I get back to my desktop computer I will run that compiz-check script.

---

### Post by overdrank on 2008-09-11
> **/usr/bin/hacked? said:**
> I have to use "metacity --replace" because when I log in, there is no window manager running. There are no title bars on the windows, but I can still open and close some programs, I just can't move them around, and the "X" in the corner isn't there, so I have to choose file > quit.
I can use nvidia-settings, and it seems to work fine, except that there are no effects.
As soon as I get back to my desktop computer I will run that compiz-check script.

Ok that is odd as you usually only loose the title bars when compiz is running. If you have CCSM installed then you may want to make sure the window decorator is checked.

---

### Post by /usr/bin/hacked? on 2008-09-11
I'm not finding anything under CCSM that says window decorator. Is it listed as something else?

---

### Post by overdrank on 2008-09-11
> **/usr/bin/hacked? said:**
> I'm not finding anything under CCSM that says window decorator. Is it listed as something else?

Hi and my error it is window decoration.

---

### Post by /usr/bin/hacked? on 2008-09-12
it still did not work. And something I did (perhaps restarting x) caused my screens to not work right. I used to have the top and bottom panels go all the way across both screens, but now they are only on the primary screen. Do you know a way to go back to having the panels all the way across the screen?

---

