---
title: "Synaptic trackpad clicking doesn't always work."
date: 2011-01-25
forum: Hardware
---

### Post by Jackie_Treehorn on 2011-01-25
Hello all.  I have an old Acer Aspire 3100 that I've been running 10.10 on for a while now.  I love it.

I have an annoying problem however.  Often tapping the touchpad to click doesn't click.  Many times I have to double click a like or browser button to make the magic happen.  The hard click buttons below the track pad always work.

Any thoughts as to why this might be and how to correct it?  It's not a deal breaker, but it does get pretty old pretty fast.

Thanks all!

---

### Post by pi/roman on 2011-01-26
Check your tap settings
```
synclient -l | grep -i tap
```If fasttaps is 1 it could cause that. Here are mine for reference:
    MaxTapTime              = 180
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    FastTaps                = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    TapAndDragGesture       = 1

---

### Post by Jackie_Treehorn on 2011-01-26
> **pi/roman said:**
> Check your tap settings
```
synclient -l | grep -i tap
```If fasttaps is 1 it could cause that. Here are mine for reference:
    MaxTapTime              = 180
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    FastTaps                = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    TapAndDragGesture       = 1

Here are my settings:

    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    FastTaps                = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    TapAndDragGesture       = 1

---

