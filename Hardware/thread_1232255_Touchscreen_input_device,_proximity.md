---
title: "Touchscreen input device, proximity"
date: 2009-08-05
forum: Hardware
---

### Post by ChrisJC on 2009-08-05
All,
 I'm working on a little app using GTK, with a resistive touchscreen on my 9.04 Netbook.
I think that the X-input extension which supports proximity detection is not working, somewhere in the driver.....

Why do I think this:
1.   g_signal_connect (G_OBJECT (drawing_area), "proximity_notify_event", G_CALLBACK (proximity_notify_event), NULL); never fires, (yes I have enabled it with GDK_PROXIMITY_IN_MASK). So GTK doesn't realise when I touch the touchscreen.

2. xinput query-state 7 always returns  Proximity=In (amongst other things) irrespective of whether I am touching the touchscreen or not. I would expect Proximity=Out normally.

I am using an eGalax touch sensor.

If I run gpaint, I cannot 'sketch'. The cursor moves, but no drawing takes place.

Has anybody used a touchscreen for anything like this? Is it a limitation of the HID implementation? Any clues?

Thanks,

Chris.

---

### Post by ChrisJC on 2009-08-17
Bump ?

---

