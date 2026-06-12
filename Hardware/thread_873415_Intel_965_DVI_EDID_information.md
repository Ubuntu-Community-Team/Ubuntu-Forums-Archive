---
title: "Intel 965 DVI EDID information"
date: 2008-07-29
forum: Hardware
---

### Post by cnolanAU on 2008-07-29
I've got a Dell Optiplex 745 here with two Dell monitors, one a 2407WFP and the other is a 17" Dell.  The graphics card is appearing as:

```
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
```

It seems that either monitor plugged in to the VGA port is detected with the appropriate EDID information, but using the DVI port the EDID isn't queried, and the appropriate modes don't appear (xrandr --verbose shows up an EDID_DATA section for the VGA, but none for the DVI).  Attempting to add the appropriate modelines for the monitor plugged directly to the DVI port doesn't work either; I get errors when I try to use xrandr to switch to the added modes.

Does anyone have any thoughts?  I can't seem to find an existing bug for this problem.

---

