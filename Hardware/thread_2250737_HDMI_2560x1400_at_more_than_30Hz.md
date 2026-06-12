---
title: "HDMI: 2560x1400 at more than 30Hz?"
date: 2014-10-30
forum: Hardware
---

### Post by solars on 2014-10-30
Hi there,

I'm currently playing around with my new monitor and a Sony laptop. It only has a HDMI port and Intel HD Graphics 4400 hardware.
I found this: [http://www.notebookcheck.net/2560x1440-or-2560x1600-via-HDMI.92840.0.html](http://www.notebookcheck.net/2560x1440-or-2560x1600-via-HDMI.92840.0.html)

2560x1440 works successfully at 30Hz

They also got it working with 50Hz - can anyone tell me how I could test if I can also get more than 30Hz?
I don't know how to generate such a modeline..

Thanks a lot,
Christoph

---

### Post by grahammechanical on 2014-10-30
The refresh rate is important. I will give you that but in my view what is more important is running the monitor at the optimum resolution decided by the manufacturer. Monitors are capable of a much higher resolution than can actually be achieved. My monitor can reach a maximum of 8192 x 8192 but I would not dream of trying to get that. I accept the 1920 x 1080 @ 60 Hz as specified by the user manual.

You could run either of these commands to see what you monitor is capable of but do not forget that the video adapter and driver plays a part in all of this

```
xrandr
xrandr -q
xrandr -q --q1
```

Regards.

---

### Post by solars on 2014-10-31
> **grahammechanical said:**
> The refresh rate is important. I will give you that but in my view what is more important is running the monitor at the optimum resolution decided by the manufacturer. Monitors are capable of a much higher resolution than can actually be achieved. My monitor can reach a maximum of 8192 x 8192 but I would not dream of trying to get that. I accept the 1920 x 1080 @ 60 Hz as specified by the user manual.

You could run either of these commands to see what you monitor is capable of but do not forget that the video adapter and driver plays a part in all of this
Regards.

Thanks, but this is not about what the monitor is capable of, the monitor is of course capable of 60hz. This thread is mainly about HDMI and the Intel HD 4400

---

