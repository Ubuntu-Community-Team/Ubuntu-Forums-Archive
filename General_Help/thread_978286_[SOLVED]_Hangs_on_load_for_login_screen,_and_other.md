---
title: "[SOLVED] Hangs on load for login screen, and other issues."
date: 2008-11-11
forum: General Help
---

### Post by CMR_98823 on 2008-11-11
Hello, I saw a couple other threads concerning this, but none were just what I was looking for.

First things first, I'm running Ubuntu 8.10.

Now, here's the scenario. I installed a login screen, and not sure, but I think I might have missed something. Anyway, I selected the new screen and proceeded to logout. We'll now it hangs during my load to get to login. 

I used something I saw in another thread:

```
sudo /etc.init.d/gdm stop
startx
```

The first code line works, I guess it's a command to stop GDM, which is a start. But then when I input "startx", it'll load, but then it's back to the infinite loading screen...

I'm currently in the LiveCD writing this as I can't login...I've tried recovery mode and whatnot and I'm pretty lost right now as to how to approach this.

Any help much appreciated!


Now for the other issue, when I was able to mess around on my actual Ubuntu, my sound doesn't work, and Rhythm Box and Movie Player will freeze up if I try to play a file.

---

### Post by CMR_98823 on 2008-11-11
Tried a couple other different things now...and none of them worked.

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

And,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


Like I said, supposedly from what I read these were either supposed to fix or "reset", and none of these were able to get me to access my login screen.

Am I applying incorrect commands pertaining to the situation?


[EDIT]

Also tried ```
 dpkg --configure -a
``` ...




Is my only option?

```
 sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

And then just reinstall once I'm back in?

---

### Post by CMR_98823 on 2008-11-11
Okay, not sure what exactly I did...but I got it to load after about the unth time...and after about 2 hours of researching similar problems. None really helped.

One thing I did that I'm not even sure if it's the reason I got back in, was:

```
sudo /etc/init.d/gdm force-reload
```

Does this usually make it load no matter?

---

### Post by CMR_98823 on 2008-11-11
Now, my other issue, concerning sound...I keep getting sound issues with various programs...the only one that is stable is Limewire.

Rhythm Box and every other program seem to have intermittent sound...or just plain none...

here's a screenshot of my error.


[IMG]http://img411.imageshack.us/img411/1872/screenshotxm4.png[/IMG]




It actually gives that error on any sound setting. FYI


[EDIT] Limewire isn't working now either... :S




I'll add, that I do have an onboard audio system, on an Asus P5WD2-Premium Mobo. ALC882 is the driver.



I'm gonna consider this solved here to save the clutterness...and I'll post this in a different forum...

---

