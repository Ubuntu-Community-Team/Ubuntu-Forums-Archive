---
title: "Getting S-Video to Work"
date: 2011-08-21
forum: Hardware
---

### Post by nkcrpn on 2011-08-21
I'm on an Inspiron 1525 (installed Ubuntu myself) and am quite inexperienced when it comes to Linux. The laptop has an Intel Graphics Media Accelerator X3100 card if that's important.

When I hook it up to the TV, go into Hardware > Monitors and Detect Monitors, it finds actually finds something. It's dubbed "unknown" and doesn't seem to work but at least it's there, right? The TV just stays black no matter what I do. It's on the correct Input but it does nothing. I've restarted my computer while hooked up like a dozen times to no effect. 

I'm not really sure what to do. Does it possibly maybe work already and I just don't know what I'm doing?

---

### Post by realzippy on 2011-08-21
Welcome to this forum.
you could run

```
xrandr -q
```

to see if s-video is detected

---

### Post by SeijiSensei on 2011-08-21
Have you tried switching between the laptop display and the TV with the appropriate Fn key combination?  From the [manual]("http://support.dell.com/support/edocs/systems/ins1526/en/OM/keyboard.htm#wp1056023") it appears to be Fn-F8, the key labelled CRT/LCD.  Holding down Fn and hitting that key should switch the image between displays.  That's what I've used with Inspirons in the past.

I think the S-Video jack is active whenever the VGA port is enabled.

---

