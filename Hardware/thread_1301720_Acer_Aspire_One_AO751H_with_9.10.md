---
title: "Acer Aspire One AO751H with 9.10"
date: 2009-10-26
forum: Hardware
---

### Post by apsalyers on 2009-10-26
This is more of a preemptive strike.  I have been running 9.04 on my Aspire One using this guide to setup the video resolution.

[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

I have been playing with 9.10 and noticing that the guide is no longer valid due to the change in the X Windows system used.  

Has anyone previewing 9.10 had any luck with this model netbook or similar graphical resolution issues?

Thanks!

---

### Post by Gavagai80 on 2009-10-27
I haven't tried it myself yet (haven't even done 9.04 yet), but I've read that the 9.10 kernel doesn't work with the proprietary 3D driver for the aspire one's graphics card, and Intel doesn't plan to ever support it. It seems VESA will be the only way to use 9.10 unless somebody hacks together something to make it compatible with the driver that Intel made for 9.04.

Or maybe there's a way to use an old kernel with a new distro?

---

### Post by apsalyers on 2009-10-27
> **Gavagai80 said:**
> I haven't tried it myself yet (haven't even done 9.04 yet), but I've read that the 9.10 kernel doesn't work with the proprietary 3D driver for the aspire one's graphics card, and Intel doesn't plan to ever support it. It seems VESA will be the only way to use 9.10 unless somebody hacks together something to make it compatible with the driver that Intel made for 9.04.

Or maybe there's a way to use an old kernel with a new distro?

Using VESA will be against the whole point of why I spent more cash to get a better display on a netbook.  Which is par for course an example of why I use linux mainly on a appliance level.

---

### Post by danstoner on 2009-11-05
I have been frustrated with linux compatibility on the ao751h.  I think some of the web posts I saw before buying were being optimistic.  The situation is a bit worse than indicated on that wiki page (I have suspend/resume issues, occasional lockups, etc.).  Short writeup:

[http://thatlinuxbox.com/blog/article.php/20091019102548111](http://thatlinuxbox.com/blog/article.php/20091019102548111)

9.04 works better than 9.10 on this hardware.



I now sometimes run Ubuntu inside VirtualBox on my netbook (I have the 2 GB model and it works ok).  Silly perhaps, but more reliable than running ubuntu natively on the ao751h.

---

### Post by Reverend G on 2009-11-11
I've taken the plunge with 9.10 and it's been well worth the minimal time required. Jaunty wasn't terribly impressive on my Ao751h with slow internet and choppy as heck video playback but a fresh install of 9.10 and some tweaking with the instructions here:
 
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
 
and everything is hunky-dorey.

---

### Post by Ampi on 2009-11-11
I have an AAO ZG5 and started with UNR 9.04 which gave me a lot of problems with the wireless. Eventually it would work but when it choose not to, I could forget. No idea why. Also LED lights wouldn't work
I upgraded to UNR 9.10 and I'm quited pleased. Wireless stopped giving me problems and even the LED lights funtions 90% of the time.
Have had no video problems with both of them.
This is my experience..

---

