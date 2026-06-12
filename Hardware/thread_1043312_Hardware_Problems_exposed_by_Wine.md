---
title: "Hardware Problems exposed by Wine"
date: 2009-01-18
forum: Hardware
---

### Post by msbealo on 2009-01-18
Hi,

I'm trying to get Red Alert 2 working with Wine, but wine is only interested in crashing and freezing my computer.

I have an Acer Aspire 1350. If I do something as simple as edit an entry in regedit or open taskmgr then my system freezes. 

I read in the Wine FAQ (Section 6.3) that a complete system freeze is most likely due to hardware drivers, but I'm struggling to figure out which ones. 

As suggested in the FAQ, I ran glxgears with no problem.

Does anyone have any suggestions of tests that I do to pin this down?

I'm using the openchrome video drivers with Mesa. If I turn off DRI as suggested somewhere, the problem persists. 

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SS
```

I'm thinking that it might not be a graphics driver problem, but I don't know.

If anyone would like me to post some output then I'd be pleased to.

Thanks.

P.S. That list of problems in the Troubleshooting Section of the Wine FAQ looks quite worrying.

---

