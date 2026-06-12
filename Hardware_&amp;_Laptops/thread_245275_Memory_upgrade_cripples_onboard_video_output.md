---
title: "Memory upgrade cripples onboard video output?"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by K.Mandla on 2006-08-27
I had been pulling my hair out over this one for a day or two. I have a Dell Optiplex GX150 with onboard Intel i810 video that was acting strange.

I put 512Mb (that's 2x256Mb) of Viking PC133 in, and suddenly my video output was laced with vertical streaks. I didn't take a screenshot but I don't know they would have shown up anyway, since they seemed independent of the actual desktop itself.

Switching to a resolution of 1024x768~60 or lower erased the problem, but anything above that (my panel is native at 1280x1024~60) was streaky.

Nothing else changed. Same monitor, cables, power supply, etc. The machine is rated to take PC133, with a maximum of 512Mb. The BIOS is the latest (and last, probably) release, and I don't have any funky hardware attached.

I tried Xubuntu, Arch linux and even Zenwalk, but everything showed the same problem. I would have consigned the issue to defective video, but ... the Dreamlinux liveCD didn't have that problem.

To make what is turning into a long story short, it seems Dreamlinux boots to a color depth of 16 for i810 machines, whereas the others go straight to 24. I've tested it by bumping up the color depth in Dreamlinux, and sure enough, the streaks came back.

So in this instance, a lower color depth solved the issue. I'm not sure why improving the memory would cause that (this onboard video has only 1Mb of video memory), but it's probably some sort of memory access bug that is beyond my technical expertise. ;)

Cheers, all.

---

