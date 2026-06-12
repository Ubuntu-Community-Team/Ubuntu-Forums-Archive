---
title: "free radeon driver hangs"
date: 2009-03-14
forum: Hardware
---

### Post by Rommidze on 2009-03-14
I am trying to use open source radeon driver but it hangs when X starts. I see that ubuntu tries different modes but hangs on the fourth attempt. My card is ATI Mobility Radeon X600. Ubuntu is 8.10.

My Current config is very trivial:
```
Section "Device"
        Identifier  "Configured Video Device"
        BusID       "PCI:1:0:0"
        Driver      "radeon"
EndSection
```

That is all what I have changed from the default xorg.conf.

And btw, it works almost fine with fglrx, except some bugs with compiz.

---

