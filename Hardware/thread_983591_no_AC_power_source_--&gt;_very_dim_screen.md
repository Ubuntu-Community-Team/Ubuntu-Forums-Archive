---
title: "no AC power source --&gt; very dim screen"
date: 2008-11-15
forum: Hardware
---

### Post by Baodehui777 on 2008-11-15
Hi. I just recently bought a Samsung NC10, which I immediately put Intrepid on and love to death. I've got most things working reasonably well, aside from the usual wireless issues, but I'm having one problem that really has me stumped.

If I start the computer up connected to the charger, then the screen is at max brightness and the screen brightness applet works perfectly.

If I start the computer up without the charger, then the screen starts with its brightness at roughly half, maybe lower. The screen brightness app works, but even with it cranked up all the way, I can only get to this half brightness setting.

Basically, it seems like Ubuntu is detecting the lack of an AC source, and setting some kind of maximum brightness. It must do this pretty early in the boot process, as even the Ubuntu boot screen is substantially dimmer than normal.

Is there some way to undo this? I would really like to have full control over the brightness even when I'm on battery power.

[edit] I guess I should note that this happens regardless of the charge state of the battery. Also, I have power management set up not to dim the screen or reduce backlight brightness when on battery power.

---

### Post by i-am-me on 2008-11-15
I know nothing about this issue myself (I use a desktop), but this post might help: [http://ubuntuforums.org/showthread.php?t=568732]("http://ubuntuforums.org/showthread.php?t=568732") Go down to the 7th post (and below).

---

### Post by Baodehui777 on 2008-11-15
Hi!
Post #7 didn't help, but other posts in that thread directed me to a bios setting that was causing the problem. Thanks so much for your help!
I'm guessing you found that by a forum search, which makes me kind of embarrassed. Sorry for the unnecessary thread.

---

### Post by i-am-me on 2008-11-15
A google search and no problem. Happy to help.

---

### Post by Jon Bradbury on 2008-11-18
Try the power settings. When the AC cord is unplugged, by default Intrepid will dim the screen. You can uncheck a box to disable this.

Edit : Sorry, ignore post; I see you have a solution already...

---

