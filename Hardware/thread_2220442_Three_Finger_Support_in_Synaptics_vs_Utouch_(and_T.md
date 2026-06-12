---
title: "Three Finger Support in Synaptics vs Utouch (and Touchegg)"
date: 2014-04-28
forum: Hardware
---

### Post by dubz2 on 2014-04-28
So I have been trying to find a way to get three finger support working with my synaptics touchpad for a while (I have a Sony Vaio S 15 inch). The most popular option seemed to be using Touchegg, but I could only get it to recognize two finger touch. With more research I learned that Touchegg receives gestures from Utouch (running 12.04 still, but had the same issues in a 14.04 LiveCD). Then I tested with geistest and got the following result:
```

Device 16000 added
    attr "device name" = "SynPS/2 Synaptics TouchPad"
    attr "device id" = 16000
    attr "device touches" = 2
    attr "direct touch" = false
    attr "independent touch" = false
    attr "device X minimum" = 1472.000000
    attr "device X maximum" = 5638.000000
    attr "device X resolution" = 37000.000000
    attr "device Y minimum" = 1408.000000
    attr "device Y maximum" = 4692.000000
    attr "device Y resolution" = 54000.000000

```
Even after seeing the *attr "device touches" = 2*, I wasn't convinced that there was no option as I had gotten three finger tap and click working using *synclient TapButton3=2*. So after more searching I got to: [http://ubuntuforums.org/showthread.php?t=2117981](http://ubuntuforums.org/showthread.php?t=2117981)
The results here work, but I feel like this is not a very clean solution and does not let me configure the three finger swipe as conviently as Touchegg. Is there anyway to get the three finger support to work properly with Touchegg or Utouch.

---

