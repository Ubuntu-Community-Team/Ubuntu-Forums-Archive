---
title: "Problem with VGA projection display"
date: 2015-10-22
forum: Hardware
---

### Post by arashiko28 on 2015-10-22
Hello,
I haven't been able to find a solution to this problem. I have an Acer Aspire One D-150, laptop. Is the one I use for work.
I'm a science teacher and Ubuntu allows me to use several programs that are extremely useful to teach, like interactive periodic table, molecule designer, among others. Now, this is the main reason why I need Ubuntu to work.

I have a problem with the VGA connection (this is an old laptop, so no HDMI). Whenever i connect to a projector or smartboard with the VGA cable, I loose the laptop screen, it goes black and if I unplug the cable, it doesn't come back, so I have to hard shut down in order to recover my screen. Usually I work with extended display, so that I can project what I'm teaching, and grade on the laptop screen.

How can I get the display to work on both screens at the same time?
I have done every walkaround and installed a million drivers and still no progress. This laptop has an Intel graphics card, so I don't think there's a compatibility issue with the OS.

Please help!!!!

---

### Post by tgalati4 on 2015-10-22
On my Thinkpad, there is Fn-F7 which cycles between laptop, projector, both, none. Does your laptop not have a similar video switch?

What graphics card?

```
lspci | grep VGA
```

---

### Post by TheFu on 2015-10-22
Nice problem description.

Does this setup work with an external monitor connected? Trying to figure out if the issue is projector or system related. Some  MB+CPUs+IGPs support driving different numbers of displays-1,2,3,4....

Also check that the video modes supported by the projector are supported by the laptop screen. Perhaps only 1 size setting works for both, so pre-setting the laptop to the same resolution as the projector before connecting may be necessary.

The tool I find easiest to  enable/disable multi-monitor support is **lxrandr**.

Hope this stuff gives you some ideas to try.

---

### Post by tgalati4 on 2015-10-22
Try a different cable.  If you have a bad VGA cable, that can cause the graphics to shut down.  Check the pins.   A bent or missing pin can cause issues.

---

