---
title: "diNovo Mini stopped working"
date: 2008-11-24
forum: Hardware
---

### Post by Daktar on 2008-11-24
I bought a diNovo Mini in may and with 8.04 it worked åretty good, only I had to remove battery after it had been idle. With 8.10 I managed to setup it with the new bluetooth wizard and after that I didn't get the remove battery prob anymore. But now I tried using it again yesterday after it had been idle 2-3 days but no keys get typed when I push the keyboard and mouse doesn't move when touching touchpad, tried removing battery and also delete it from bluetooth list and setup it again, it finds the keyboard asks me to type in four numbers on it I do that and then presses enter on the dinovo and then it changes to setup successfully, switch to opera or gedit but still no change.

---

### Post by neograniceni on 2010-01-10
Well, I experienced the same problem with two versions of mini, and also read on Logitech forum about this problem. And found a workaround, first under Windows, but the same way for Linux/Ubuntu too. The point is that the keyboard disconnects from bluetooth adapter when You close the cover. If you close the cover before system go to shutdown/sleep/hibernation, mini will work and everything will be OK no matter how long Your computer stay off. The problem is that You have not much time to do that before computer goes to sleep/shutdown, and if the cover is closed after that, mini ofter looses it's pairing with BT. So I finally made some .bat script under Windows using third party standby tool to perform standby with some delay (5-8 sec is enough for me). So I did something similar under ubuntu. Since my HTPC work OK with default system shutdown/sleep/hibernate functions, I just wrote a script that executes during sleep/wakeup event since I only use sleep on my HTPC (located in /etc/pm/sleep.d).

```

#!/bin/sh 
# 5 sec pause during sleep/wakeup
case "$1" in
    suspend)
	sleep 5
        ;;
esac 

```

For more than a year I didn't have a single problem using mini in such a way under Windows, and now everything works OK under Ubuntu too for more than three weeks. A script above works fine under Ubuntu 9.10, hope it should work for other versions too if they use pm-utils for sleep/shutdown/hibernation stuff. Sorry, I am really new to Ubuntu/Linux stuff, so don't know about other versions/distros for sure. And sorry for my English :redface:

---

