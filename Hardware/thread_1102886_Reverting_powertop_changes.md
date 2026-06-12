---
title: "Reverting powertop changes"
date: 2009-03-22
forum: Hardware
---

### Post by LastHunter on 2009-03-22
Hi,
I have been trying using Jaunty Jackalope recently and because of my laptop (HP Compaq 6510b) has been warmer and its battery has got lower capacity than usual (with WinXP), i tried several utilities for lowering the system requirements.

But after using them, my wireless adapter has been weaker in some way, it transfers data really slowly (and it's not problem of my router or something - my desktop PC works OK).

I suspect **powertop** utility, it asked me if I want to lower wireless adapter battery consumption. But I cannot find where I can revert this, excluding reinstalling the system :)

Thank you for any ideas!

---

### Post by sdennie on 2009-03-22
Unless you've done something to explicitly make powertops settings permanent, they are completely lost after a reboot.  Some are even lost after a suspend/resume.

---

### Post by LastHunter on 2009-03-22
That's weird - I think that users expect powertop changes to be permanent - if not, they are supposed to run this utility everytime they reboot and so on - and that's not very comfortable.

So, if you are right, my problem is caused by something else. Any suggestions?

---

### Post by LastHunter on 2009-03-22
Oh my god, I am so lame :D It was caused by bad DNS settings :)

---

### Post by sdennie on 2009-03-22
> **LastHunter said:**
> That's weird - I think that users expect powertop changes to be permanent - if not, they are supposed to run this utility everytime they reboot and so on - and that's not very comfortable.


It would be hard or impossible for powertop to do this only on battery in a disto-neutral way.  It's really just giving you suggestions that you can try within the gui and see if they have any effect on power usage.  If they do and you like them, you can use your distro specific way to make them permanent manner.

> **LastHunter said:**
> Oh my god, I am so lame :D It was caused by bad DNS settings :)

Glad you found your solution.  :)

---

