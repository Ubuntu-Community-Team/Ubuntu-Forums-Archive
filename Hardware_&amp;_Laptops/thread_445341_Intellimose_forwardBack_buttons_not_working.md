---
title: "Intellimose forward/Back buttons not working"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by sassinak on 2007-05-15
I did the standard editing in xorg.conf to add my IM Explorer as a 7 button mouse with the Z Axis mapping and it worked great in 6.06 - 6.10.  After upgrading to 7.04 however, I lost the functionality of my forward and back buttons.  I ran xev and it completely fails to read any button presses from the side buttons 6 and 7.  If I define the mouse to have 7 buttons then my scroll wheel becomes buttons 4 and 6 in one direction and 5 and 7 in the other.  This causes scrolling with the scrollwheel to also take me back a page in Firefox.  Not really what I want.

My xorg.conf currently has the mouse defined as a 5 button mouse and this has both directions of my scrollwheel working, so now all I am missing is the side buttons.  My main concern is that it's not showing up as an button press in xev, so it's like they completely don't exist.  Once I can clear that up I can handle mapping them correctly in xorg.conf.

I'm also going through a DLINK 4 port KVM, but this hasn't been a problem in the past, only once I upgraded to 7.04.

Any ideas?

---

### Post by knightnet on 2007-05-16
Here is what worked for me:
```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse_MS"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option                 "Resolution" "800"
    Option         "Emulate3Buttons" "no"
        # 1st two entries are for up/down scroll, 2nd two are for left/right scroll
    Option         "ZAxisMapping" "4 5"
        # MS Intellimouse Explorer 4.0A USB has 9 "buttons" (which includes the scroll wheel)
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

---

### Post by sassinak on 2007-05-30
This is a really really late reply, but I finally got around to implementing this fix and I am glad to say that this has successfully fixed the problem!  Thanks!

---

### Post by knightnet on 2007-05-31
Glad to hear that it helped.

J.

---

