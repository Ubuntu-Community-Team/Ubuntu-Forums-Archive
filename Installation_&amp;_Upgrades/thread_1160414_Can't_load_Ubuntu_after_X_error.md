---
title: "Can't load Ubuntu after X error"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Bearly Able on 2009-05-15
Hi,

I upgraded from 8.04 to 9.04 (via 8.10) a week ago, and everything seemed to be fine.  Yesterday, I had a couple of problems with application becoming sluggish or freezing.  Today, my husband a similar problem, and when he logged out, he got an error message saying that there was a problem with the X System and the GUI had been disabled until it was fixed.

I was unable to restart X from the terminal (various errors listed, including nos. 111 and 3), and decided to reboot.  However, I can't boot into Jaunty in either normal or recovery mode.  Ubuntu starts to load, then I get a screen showing the message
```
[ linearly increasing number e.g. 85.023546] hub 1-0:1.0: unable to enumerate USB device on port 4 
```
repeated apparently endlessly.  (It starts with 2 digits before the point, and left alone will continue into 5 digits.)  I can't find any way to interrupt the process; Ctrl+Alt+F1 just shows the ongoing process, and in any case, I have no idea what's going on or what I should be trying to do about it.

At the moment, I'm running from a live CD to access the Forums.  We had no problems at all until the upgrade.  Can someone please advise me where to start to fix this?  I'm not sure what other information I need to give - please be patient, as I'm pretty new to Linux.

There are two other kernels listed in my GRUB menu, but they look like earlier versions (i.e. Hardy & Intrepid), so I wasn't sure whether trying to boot into them would help in any way.

Thanks in advance for any assistance you can offer.

---

### Post by Bearly Able on 2009-05-16
I've just booted up again using the Jaunty Live CD, and noticed the same message appears briefly (i.e. 6 or 8 times) during start-up.  The first time I loaded Jaunty after the update, I saw the same thing, but it didn't happen on subsequent occasions.

I'm wondering if disconnecting the device on Port 4 would stop the messages and perhaps enable me to access the recovery mode?  Unfortunately, I don't know how to find out which device it refers to.  I have a scanner and printer, both connected via USB but neither of them turned on at the moment.  I also have a faulty internal card reader, to which I attributed the problem when I first saw the message.  I would just try disconnecting this to see what happens, but it includes the only functioning USB port on the front of the computer; disabling it would be a real pain.

I really don't want to re-install if there's another way to fix this, but I'm still a Linux newbie and don't know where to go from here.  Any help would be much appreciated.

---

