---
title: "Shut down problem on Fujitsu Siemens notebook"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by rem on 2008-01-06
Hello,

My desktop got broken few days ago and while I'm having somebody fixing it, I am using the laptop and I thought that it might be a good idea to plug in my wide screen monitor to it. I searched over the related threads on this forum and I learned that this can be achieved by configuring multiple screens so I went to System > Screens and Graphics and attempted to detect the monitor. It didn't worked so I gave up on this idea but now I can't shut off / log-out / switch users properly. The system is freezing and the laptop monitor goes black so each time I want to switch off, I have to force it from the power button.

I also tried to reconfigure xorg but when it attempts to automatically detect the monitor, it's freezing in the same manner as described above.
 
Thank you for your time and looking forward for any piece of advice you might have.


Regards,
Rem.

---

### Post by rem on 2008-01-17
After days of trial and error I finally manged to fix the problem. Just in case somebody else here has the same problem, I'll describe what I did.

The answer is:

```
sudo dpkg-reconfigure xerver-xorg
```

But when it comes to **attempt monitor detection** I instructed to go forward and I said "No". The dialog finally asked me if i want to keep the default monitor settings and go through and of course I choose "YES". After rebooting everything was just like before.


Cheers!

---

