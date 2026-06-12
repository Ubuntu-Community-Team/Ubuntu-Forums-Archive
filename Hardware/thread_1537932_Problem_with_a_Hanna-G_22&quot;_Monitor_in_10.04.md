---
title: "Problem with a Hanna-G 22&quot; Monitor in 10.04"
date: 2010-07-24
forum: Hardware
---

### Post by irv on 2010-07-24
I have a Hanna-G 22” external monitor which I used in Ubuntu 9.04. Since I installed 10.04 I have been having some issues with it. I worked on it yesterday and got it to work once, and now this morning I can't get it to work right again. Here is the issue.
Yesterday, when I booted up with the monitor plugged into the laptop, I would get a display, but it would shake. I would keep switching between the laptop LCD and the monitor using the “Fn” and “F8” keys. Once in a while I would get it to stop shaking but it was in a very low Resolution. Other time I would get a “out of range” message. I would go to the System> Preferences> Monitors Preferences, but could not change the resolution or refresh rate. I then try to reboot a few times, and then all of a sudden I got a very nice display with a high resolution and it did not shake. Looked great and I used it the rest of the day.
I shut it down last night and this morning I can't get it to work again. I tried to reboot it about 20 times with no luck. I really feel this is a bug in this version of Ubuntu.
I know in other version of Ubuntu if I had problems like this I would have just edit the xorg.conf file, but I can't remember how I did it.
Anyone have an idea how to fix this problem?

---

### Post by vandorjw on 2010-07-24
suggestion 1. sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
suggestion 2. reboot computer.

New version of X no longer needs xorg.conf (I don't know why everyone insists on keeping it around.) - if i am wrong just remove the .old

suggestion 3. test monitor on different computer..just to be sure.
suggestion 4. try a lower resolution

suggestion 5. try it with a live cd of ubuntu 10.04 (if the live CD works fine, that tells me you configured something wrong, and problem is not with software..)

cheers - CC7

---

### Post by irv on 2010-07-24
> **cc7gir said:**
> suggestion 1. sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
suggestion 2. reboot computer.

New version of X no longer needs xorg.conf (I don't know why everyone insists on keeping it around.) - if i am wrong just remove the .old

suggestion 3. test monitor on different computer..just to be sure.
suggestion 4. try a lower resolution

suggestion 5. try it with a live cd of ubuntu 10.04 (if the live CD works fine, that tells me you configured something wrong, and problem is not with software..)

cheers - CC7
Thanks for the suggestions. First, I don't have a /etc/X11/xorg.conf. So the first two suggestions are out. No 3: works on other computer and OS's. Tried No 4. Did not help. I will have to try No. 5 the Next time I hook up the monitor to the Laptop. I will try it later on today.

Without the xorg.conf file there is no way to set the monitor manually. 
I have another LCD TV that has a RGB connection and I tried it yesterday and it worked great. I am starting to wonder if it is the combination of Ubuntu and the make and model of the monitor.(Hanna-G).
Thanks again for the suggestions.

---

### Post by irv on 2010-07-24
OK, I tried No.5 and it acted the same way with the Live CD. But I discovered the monitor cable came loose on the monitor. After fixing this problem, I can get the monitor and laptop to work together. I need to cycle through the "Fn" and "F8" keys about 6 times before the resolution and refresh rate comes up right. I am going to mark this thread as solved.

---

