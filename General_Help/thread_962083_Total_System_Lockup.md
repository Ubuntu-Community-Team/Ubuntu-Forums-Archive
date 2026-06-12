---
title: "Total System Lockup"
date: 2008-10-28
forum: General Help
---

### Post by ghandi69_ on 2008-10-28
Hey guys, within the last couple of days or so, I have been having a strange occurrence, being that my system will completely freeze(mouse doesn't move, no combination of keyboard commands(ctrl atl backspace, alt anything...)will work, and the clock stays at whatever time it was when it crashed, etc etc.  I have looked through almost all of the log files contained in /var/log, and I can't find anything that seems relevant to anything that would have happened the time of the crash.

I normally have conky running the background, and I would say half the time I have eclipse, firefox, and streamtuner/vlc running as well.  I am running ubuntu 8.04 with a typical gnome-desktop setup.

My first question I guess would be..

Where do I look to find out whats wrong?

Thanks

---

### Post by alienprdkt on 2008-10-28
check your performance monitor.

see if there is any processes that may be over using the cpu, and or ram.

---

### Post by ghandi69_ on 2008-10-28
> **alienprdkt said:**
> check your performance monitor.

see if there is any processes that may be over using the cpu, and or ram.

Well, as mentioned, I do have conky running in the background, which is showing how much my CPU and RAM are being used at all times.  When the screen freezes, there was nothing out of the ordinary, about 20% of CPU, and about 40% of my ram is being used.

---

### Post by mikeize on 2008-10-30
I've had this same problem through multiple fresh installs since Feisty (now running Intrepid).  There are some huge threads about this, but I don't think anyone has found the solution unfortunately.  My logs show nothing either, and the freezes can occur no matter what the cpu load is, or what if any programs are running.  Quite annoying.  Good luck, and let us all know if you figure it out.

---

