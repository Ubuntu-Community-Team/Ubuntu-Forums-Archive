---
title: "Can't start Ubuntu after upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by rbaleksandar on 2009-11-03
Hi, guys. :)

  Well, I just upgraded from 9.04 to 9.10. And this made my Ubuntu unusable. :( Didn't see anything like my problem here but sorry if this already occured and is solved.


Information about what happened:

- downloaded the alternate CD and mounted the ISO
- upgraded using the gksu "sh /media/ubuntu-9.10-alternate-CD/cdromupgrade"
- while in Ubuntu and watching the upgrade (I closed all applications I could), no error whatsoever occured. Everything went smooth like a hot knife cutting butter.
- I was prompted to restart.
- I'm running dualboot Ubuntu/WinXp. I chose to boot the new 9.10 Ubuntu with the latest kernel (I updated it a while ago while still with 9.04).
- The well known console-lines appeared on my screen:

```

Boot from hd(0,3) blablabla
Starting up...
```

- The logo appeared followed by the same console-lines (strange)
- And the sh*t happened. The lines started blinking (about 1 blink per second). The light-emitting diode showing the current work of my hard drive started blinking like crazy. Then a login-message appeared. And here's were I got stuck. My keyboard showed almost no response to what keys I hit. I had to hit 3-4 times each key to type one letter of my login-name. Sometimes it appeared after the 1-2 time, sometimes after the 4th time. So you see although it's possible to type in my name (in a very painful manner), to enter my password is impossible since I can't see what I type in (no * appear, nothing).

  This is my first upgrade from alternate CD. I usually reinstall my whole system. And obviously I'll do that from now on. :(

  Can someone help me? I tried booting from previous kernels (I still have last 2 versions). Same result. Tried recovery mode. It works. It's just a terminal of course.


Thanks in advance!

---

### Post by nielsbk on 2009-11-05
Hi, I've the same exact error. Although I upgraded through the update manager. Have you come across a solution?

---

### Post by rbaleksandar on 2009-11-05
Sorry to disappoint you but no. I tried repairing with the LiveCD but it didn't help (good that I have dual boot so that I can burn it). Make a backup with a live CD (better USB so that you'll be able to burn your data on a CD/DVD) and format. A friend of mine had a similar problem. We both looked in the internet for a solution. :( From now on I advice you (I'll do the same) to make a backup before upgrading (if you know how to use Norton Ghost etc. to copy your partition - do it). Even then it's better to make a clean install (like with Windows and other OSs).

Greetings!

---

### Post by RavanH on 2009-11-05
Have you tried some kernel boot switches like "acpi=off noapic nolapic nomodeset" in GRUB?

---

### Post by ratcheer on 2009-11-05
There are lots of threads here about this problem. You do not need to reformat and reinstall. You just need to get switched to a generic display driver so you can get logged in to the point that you can install your proper display driver.

Here are some threads that should help:
[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)
[http://ubuntuforums.org/showthread.php?t=1314152](http://ubuntuforums.org/showthread.php?t=1314152)
[http://ubuntuforums.org/showthread.php?t=1307566](http://ubuntuforums.org/showthread.php?t=1307566)
[http://ubuntuforums.org/showthread.php?t=1305370](http://ubuntuforums.org/showthread.php?t=1305370)

Tim

---

### Post by rbaleksandar on 2009-11-05
Thanks a lot. Hopefully it won't happen in future releases but just in case I'll be prepared now. :)

---

