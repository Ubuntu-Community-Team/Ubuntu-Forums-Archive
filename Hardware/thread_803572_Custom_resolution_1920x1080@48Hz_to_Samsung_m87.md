---
title: "Custom resolution 1920x1080@48Hz to Samsung m87"
date: 2008-05-22
forum: Hardware
---

### Post by yellowman on 2008-05-22
Hi,

I´m trying to get my htpc(running Ubuntu 8.04 with a 8500gt) to use 1920x1080 at 48Hz. That resolution is not available in nvidia x-server settings, I can however choose others like: 1920x1080@60Hz, 1920x1080@24Hz and so on. The idea is to get the tv thinking it´s beeing fed 24Hz.

But when I choose 24Hz the picture jumps a little.
I have had the exact problem when I connected a Mac to the tv, the solution then was to use an application called switchResX, where I could create a custom resolution(at 48Hz since the tv does a 2:2 pulldown) and that worked fine. The tv took it as 24Hz and the picture didn´t jump.

So how do I do this in Ubuntu?

I have tried to generate my own ModeLines through some webpages, adding them to my xorg.conf and also stuff like:
```
Option "ExactModeTimingsDVI" "true"
Option "UseEDID" "FALSE"
Option "ModeValidation" "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"
```

But when EDID is disabled it always seems to default to 640x480 and disregard any ModeLines.

I´m a bit of newb, so all this EDID, modelines and xorg stuff is new to me. I have searched a lot for a solution the past days, so any help is highly appreciated.

Thanks in advance!

---

