---
title: "GeForce Go 7400 driver (Jaunty)"
date: 2009-05-06
forum: Hardware
---

### Post by nexus_2006 on 2009-05-06
OK, so I know that it has to have been asked 10000000 times by now, but can someone point me in the right direction to get my video chip cooperating with X.org 7 that came with jaunty so that I can enable compiz and AWN, etc.?

The last version of Ubuntu I tried was 8.04, and the restricted hardware dialog made it work easy peasy, but its not in that dialog for 9.04.  There are several packages installed when I search synaptic for "nvidia", but none of then seem to do the trick, I get 60-ish FPS in glxgears.

I'm not opposed to using the nvidia drivers, I just want 3D accel.

---

### Post by nexus_2006 on 2009-05-06
Sorry for the bump, but can someone at least limnk me to a tutorial or howto?

---

### Post by nexus_2006 on 2009-05-07
If I just download and install the closed-source drivers from nVidia's website, will that help?

---

### Post by Kareeser on 2009-05-07
Hi nexus, take a look here:
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44)

Substitute this link for the 32-bit driver:
[http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run)

---

### Post by nexus_2006 on 2009-05-07
Ah, thanks, exactly what I was looking for.  I'll let you know how it goes.

---

### Post by nexus_2006 on 2009-05-07
Excellent, thanks, its working now.  I still have to figure out how to disable vertical refresh, but I'm getting 3D accel, and everything is cool.

---

### Post by Kareeser on 2009-05-07
Have you tried looking at nvidia-settings?

---

### Post by nexus_2006 on 2009-05-07
Yes, but I don't see one called vsync.  I found a few "VBlank"s, and unclicked them...

I'm not this big of a moron, I promise :)

---

### Post by Kareeser on 2009-05-07
Hello again, nexus. You were onto something with VBlank.

Please see the following: [http://us.download.nvidia.com/XFree86/Linux-x86/180.51/README/chapter-11.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.51/README/chapter-11.html)

---

### Post by nexus_2006 on 2009-05-07
Thanks for the link and all the help.  I do have one other quick question though.  Ctrl+alt+backspace doesn't seem to want to cycle the X server like it used to.  I'm guessing there is a line I need to uncomment somewhere or a value to change from 0 to 1 or something?

---

### Post by Miljet on 2009-05-07
I can't remember where I read it, but I seem to remember that it was disabled in Jaunty. But it can be turned back on. Sorry my memory is so bad so you will have to Google for it.

---

### Post by Kareeser on 2009-05-07
Correct.

You can install a nice little helper app to re-enable Ctrl-Alt-Bksp.

```
sudo apt-get install dontzap
dontzap -d
```

Restart X server (log off and log on), and it'll be back.

---

### Post by nexus_2006 on 2009-05-08
Ah, nice.  I googled it, installed don't zap, turned the reboot ability on, and tried it.  Haven't rebooted until just now, and it works.  Thanks guys.  My Jaunty install is pretty much 100% done, and works great.  It feels a lot snappier and I like what I've seen so far a lot.  We've come a long way since Dapper Drake, huh?

---

### Post by Kareeser on 2009-05-08
Indeed!

I'm glad everything worked out, for you... and now, if you run into others with the same problem, you can help them with your own experience! :)

Congratulations!

---

