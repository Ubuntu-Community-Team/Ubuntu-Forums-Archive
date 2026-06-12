---
title: "synaps lcd monitor problem"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by ChekhovTheAnton on 2008-04-20
Hello. I dual boot Ubuntu 7.10 and Windows, but recently I had to replace my old monitor with a Synaps 14" LCD monitor (resolution 1024x768).  The monitor works fine for Windows, but whenever I boot with Ubuntu I only get black and white lines across the screen.  I can still sign on (I can type my name and password and hear the startup sounds), but I can't see anything.  I can still boot the terminal and see just fine, but I don't know what to do in the terminal to fix things.  Any help would be greatly appreciated.

---

### Post by Rocket2DMn on 2008-04-20
Here is a guide that can help you reconfigure X (the GUI stuff) - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
In your case, you can probably get away with using the -phigh flag which will autodetect the settings so you won't have to answer any questions
Step 2 would be:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by Riyakuya on 2008-04-21
Probably your old monitor had a higher resolution, which ubuntu had saved.
So now with the new monitor only beeing able to handle 1024 x 768 it is unable to give you a decent display because it is out of range.

I actually dont know if Ubuntu has a safe mode to boot in ( never tried or needed it ) but you should try checking that, and then put to resolution lower to see if it helps.

Hope it works mate :)

---

