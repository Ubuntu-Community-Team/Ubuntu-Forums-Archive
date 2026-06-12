---
title: "black screen after kernel upgrade in Jaunty"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-06-09
Hey guys 
i did install jaunty and after i upgraded the kernel and did apt-get update. asked to reboot. I did that, 
then it opens but after being installed Compiz and configured it, then i rebooted and BUM
no logging screen, 
the boot screen i see it but doesn't get to the logging screen

Any help please, 

i have my emails and firefox all configured.

Thanks beforehand

---

### Post by doas777 on 2009-06-09
I had a simmilar issue recently. the fix, amazingly enough, was to unplug the monitor from the wall for 30 secs and try again.

also can you login blind? if so does the display "wake up"?

---

### Post by Will4 on 2009-06-09
I tried to log in blind but nothing happen
The PC seams to be on, so the monitor but black screen
i can't even do Ctrl+Alt+F1,2,3,4 any shell. 
I even tried starting it from recovery mode but the same
I can't tell what could it be

Any idea??

---

### Post by doas777 on 2009-06-09
did you try rebooting your monitor? I know, I would have looked askance at anyone asking me that question, but it has worked for me. no idea whether ti's the key for you, but worth a try.

---

### Post by Will4 on 2009-06-09
Thanks man,
I did all that but nothing. Still the same black screen

any help?? other ideas??

Thanks

---

### Post by doas777 on 2009-06-09
well, I would reboot in single-user mode ("Recovery mode") in grub, and then issue this command to reset your xorg:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

then reboot, and see if you get signal using a generic driver. then you can reinstall the restricted driver for your card, and cross your fingers.

good luck

---

