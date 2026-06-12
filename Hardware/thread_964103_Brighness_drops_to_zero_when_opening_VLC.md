---
title: "Brighness drops to zero when opening VLC"
date: 2008-10-30
forum: Hardware
---

### Post by euchrid33 on 2008-10-30
I'm running Ubuntu Intrepid, 8.10, on an Advent laptop.  Whenever I start playing a video on VLC or running an application like VBA, the brightness of the screen goes way down.  When I open the brightness applet (Power Manager Brightness Applet 2.24.0) it's still set at maximum, and I have to twiddle the slider down and back up to get the screen bright again.  Very annoying.

Any idea what is causing this, and how I can go about fixing it?  I just want the brightness to remain unchanged when I start running these things.

---

### Post by DanTheFlyingMan on 2008-10-30
I had the exact same problem. Try entering this in the terminal:

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add to the bottom of the file:

```
# horrible brightness adjustment thing
blacklist video
```

Then save and restart.

---

### Post by euchrid33 on 2008-10-31
> **DanTheFlyingMan said:**
> I had the exact same problem. Try entering this in the terminal:

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add to the bottom of the file:

```
# horrible brightness adjustment thing
blacklist video
```

Then save and restart.

I saw you suggest that in another thread and gave it a try.  When I restarted brightness was at zero, and moving the slider did nothing.  I'd still like to be able to adjust the brightness, I just don't want it to adjust itself.

---

### Post by DanTheFlyingMan on 2008-10-31
Can you change your brightness using whatever Fn key combo your laptop uses after doing what I told you before?

---

### Post by euchrid33 on 2008-11-02
> **DanTheFlyingMan said:**
> Can you change your brightness using whatever Fn key combo your laptop uses after doing what I told you before?

On my laptop it's Fn and F7 / F8, bu tthey haven't worked since I moved to Ubuntu.

---

### Post by antoniompereira on 2009-03-18
Hello,
Any solution for this thread?

I have de same problem... Vlc, VirtualBOX and other (may be 3d applications) make the screan darkness.

thanks.

---

### Post by euchrid33 on 2009-04-27
Okay, problem solved.  I don't know what was causing it originally, or if it would work for everyone, but upgrading to Jaunty fixed it completely for me.

---

