---
title: "Cannot change mode of Wacom Intuos Draw"
date: 2017-02-27
forum: Hardware
---

### Post by bhilmers2 on 2017-02-27
This is my fourth Wacom tablet I've used with Ubuntu, but this model is stuck in absolute mode. I've even compiled and installed the newest input-wacom driver from the linuxwacom project. This one's got me stumped! Any Linux Wacom experts want to give it a shot?

OS: Ubuntu Mate 16.04
Device: Wacom Intuos Draw CTL-490

```
$ modinfo wacom | grep version
version:        v2.00
srcversion:     464D4A2AF73ACF93E0BCEC0
vermagic:       4.4.0-64-lowlatency SMP preempt mod_unload modversions
```

Thanks in advance!

---

### Post by pdc on 2017-02-28
so where this thread [http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom)

suggests that "*[COLOR="#0000CD"]If you want to change Stylus's mode from absolute (default) to relative[/COLOR]*," then the command is  > [COLOR="#FF0000"]xsetwacom set Stylus mode relative[/COLOR]

........ that doesn't work for you?

---

### Post by Irihapeti on 2017-02-28
That sounds like the same model tablet that I have. (CTL-490/W0)

The correct command appears to be:
```
xsetwacom set "Wacom Intuos S 2 Pen stylus" Mode relative
```

I say "appears to be" because I've only learned about the command to set relative mode recently, and haven't had much time to play with it since.

---

### Post by pdc on 2017-02-28
thanks very much Irihapeti

"The correct command appears to be:"      ............where did you get the advice from: I was just curious, as I had used the xsetwacom project page; it is always interesting to learn new things

---

### Post by Irihapeti on 2017-02-28
From memory, I think it was the xsetwacom page.

I had to do some experimenting before I got it to work.

```
xsetwacom list
```

gave me
```
Wacom Intuos S 2 Pad pad        	id: 12	type: PAD       
Wacom Intuos S 2 Pen stylus     	id: 13	type: STYLUS    

```

I then had to figure out what part of the results needed to be input. The command in my previous post turned out to be it. The quote characters are essential.

I played with it a bit after I'd left the previous post last night, and it does seem to be working.

At present, it needs to be repeated, with the table plugged in, every time I want to use it. I've not yet worked out how to get around that.

---

### Post by bhilmers2 on 2017-02-28
> **pdc said:**
> ........ that doesn't work for you?
No, that's why I'm looking for a Linux Wacom expert to jump in and give me a hand. I ran xsetwacom in debug mode but the log didn't give me anything meaningful to look at. I haven't seen that page you linked to and I'll give it a look over, thanks.

> **Irihapeti said:**
> At present, it needs to be repeated, with the table plugged in, every  time I want to use it. I've not yet worked out how to get around  that.You can run the command automatically at startup. Look in your Ubuntu control center for "Startup Applications", add a new entry (give it a name), then drop in the command you use above. Of course, you are still left with Ubuntu forgetting this command when the table gets hot-plugged, but there is a wacom daemon available to will listen for it. I've personally never used the daemon but it is listed on the linuxwacom site. Hope that helps.

---

### Post by Irihapeti on 2017-02-28
> **bhilmers2 said:**
> 
You can run the command automatically at startup. Look in your Ubuntu control center for "Startup Applications", add a new entry (give it a name), then drop in the command you use above. Of course, you are still left with Ubuntu forgetting this command when the table gets hot-plugged, but there is a wacom daemon available to will listen for it. I've personally never used the daemon but it is listed on the linuxwacom site. Hope that helps.

Thanks. I'll look into that.

---

