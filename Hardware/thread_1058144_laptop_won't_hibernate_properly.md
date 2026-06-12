---
title: "laptop won't hibernate properly"
date: 2009-02-02
forum: Hardware
---

### Post by Sarai the Geek on 2009-02-02
I have an HP Pavillion tx2000z. I really enjoy using ubuntu, but getting it to work properly has been something of a struggle.
The computer doesn't go to sleep or hibernate when I close the lid, so it's left running while I'm on the go. This poses several problems: the battery continues to be drained even when I'm not using the computer, and the it continues producing heat, which is usually dispelled by the cpu fan but when it is stuffed in my bag air movement isn't optimal and it overheats.
I've tried setting it to hibernate manually before I close the lid, but odd things happen when I reawaken it- the gui gets messed up and looks like I got too close to it with a magnet. I have to restart the computer to get it back to normal.

Any ideas about how I might fix this?

---

### Post by jbrown96 on 2009-02-02
What kind of graphics card do you have? Post the output of ```
lspci | grep VGA
```

---

### Post by Sarai the Geek on 2009-02-02
```
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
```

:)

---

### Post by Sarai the Geek on 2009-02-02
Oh, one more thing. I didn't think it was related, but if this is a problem with my graphics card, I've been having other troubles with it. When I try to turn on desktop effects, strange things happen. Let me see if I can get a screenshot.

[img]http://farm4.static.flickr.com/3440/3249206828_ef71dd5966_o.png[/img]

The problem is with the window title bars, see it?

---

### Post by jbrown96 on 2009-02-03
This will probably fix your suspend issue [http://https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("http://https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") I've had some trouble with the new 180.xx drivers, but if you used the automated Hardware Drivers installer, then you should be fine. 

The other problem is that your window manager is crashing; at least, that's what it looks like in KDE. I'm not sure how to restart it, but if you're going to use Compiz, then you should try emerald. It's a window manager for Compiz; it does look a little different and behaves a little strange by default, but it works better. Install it with ```
sudo apt-get install emerald
```

---

### Post by Sarai the Geek on 2009-02-03
Wow, those instructions are *not* aimed at newbies. I don't even know how to do the "first" instruction...

I will try the emerald thing, though. Thanks!

---

### Post by Sarai the Geek on 2009-02-03
Wow, using emerald completely fixed the problem! It took some fiddling around but now it works quite well. The control panel for emerald is a bit unstable, prone to freezing. But if you just let it sit when it freezes it seems to unfreeze after a few seconds.
Thanks so much!

---

