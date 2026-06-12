---
title: "Xubuntu 8.10 freezes randomly on old laptop"
date: 2008-11-16
forum: Hardware
---

### Post by Fall_Line on 2008-11-16
I am relatively new to Ubuntu, I have already successfully setup a desktop with Xubuntu 8.10 and was very happy with the result so decided to install on an old laptop that was struggling with Windows XP.

So i have installed Xubuntu 8.10 on the laptop, but it seems to freeze randomly sometimes after a couple of minutes, sometimes after an hour or more.

When the freeze occurs I have to hard reboot, CTRL+ALT+F1 does nothing.

The laptop is:
Toshiba Dynabook V5/410PMEW
P3m 1GHz, 512Mb RAM, Trident Cyberblade graphics, 40Gb hard drive

Does anyone have any suggestions for finding/fixing this issue?

Thanks,
Chris

---

### Post by OrangeCrate on 2008-11-16
Random freezes are hard to diagnose, but out of curiosity, did you check the memory with Memtest on the Live CD to be sure that it's O.K.? That would be the first thing I would do...

---

### Post by Fall_Line on 2008-11-18
Thank you for the reponse, I have been away for a couple of days and only just had a chance to run the test. I did not run the test before doing the install, but I have run though and everything passed without errors. So that seems ok, is there anything else I can check?

---

### Post by OrangeCrate on 2008-11-18
I am far from having extensive knowledge on computer hardware, but I occasionally clean up older computers, install Ubuntu, and then donate them to our local high school.

These are some things I do...

Make sure the inside of the computer is clean, and that the fans are working properly.

Make sure that all the connections are tight.

Check from the manufacturer if there is a bios update.

Check to make sure I have the latest video driver.

Run a Memtest for an extended period of time. I usually run it overnight, to get the complete set of algorithms to put a hard load on the memory.

If I run into a problem, or sometimes, just for the hell of it, since memory is pretty cheap, I just replace all the memory with new sticks, maximizing the amount I can stuff into the machine.

Try a different Ubuntu version, or at least reinstall Xubuntu. With 512 meg of RAM, you could easily run a full Ubuntu install.

That's all I can offer you. Hopefully, someone else will see this thread, and contribute some other ideas for you...

---

