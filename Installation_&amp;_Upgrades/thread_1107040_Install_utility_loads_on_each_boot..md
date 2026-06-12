---
title: "Install utility loads on each boot."
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Temporalis on 2009-03-26
Greetings!
I have recently purchased an eeePC 900 and loaded easypeasy in the hopes that my wife will use it.  Whilst setting it up and getting the latest software updates, I noticed that the ubuntu installation utility keeps popping up every time I reboot the system.  It's the one that you can get to from home > administration > install, that says "Welcome.  Ready to install?  Once you answer a few questions...."
I have run 'ps -eaf' and looked through the results, but I am unable to find a process that looks even remotely related to the installer.  There is nothing in my .profile that indicates that it should load on boot.  There are no crontab entries either for root or my user.
Does anyone know what the path or process name are for this utility?  And better yet, does anyone know how I can get it to stop loading on boot?  Please let me know if I need to provide any further information.

Thanks,
Ben

---

### Post by Temporalis on 2009-03-26
OK, so I have figured out that it is the localechooser that is being loaded at boot, but I still cannot figure out where it is being loaded from.  Anyone have any ideas?

TIA,
Ben

---

### Post by spcwingo on 2009-03-26
Check under /home/your_username/.config/autostart

---

### Post by Temporalis on 2009-03-26
Nope.  There's not even an autostart there.

---

### Post by Temporalis on 2009-03-26
Well, I found it by blindly removing items from preferences > sessions.  Once I removed Ubiquity and restarted, it works like a charm.  After reading a little bit, I found that Ubiquity is the live-cd installation automator.  I guess it makes sense now, huh?  Anyways, thanks for those who read the post, and especially for those who gave input.

Ben

---

