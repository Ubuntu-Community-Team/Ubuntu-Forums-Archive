---
title: "Small squares of random pixels static artifact on video card"
date: 2012-04-21
forum: Hardware
---

### Post by nvartifact on 2012-04-21
Is this card defective, or am I only seeing a power supply, driver or other issue? Generally, how do you diagnose or reproduce such an issue (under Windows) for the repair technicians?

I'm using a compositing window manager (KWin) for my desktop (i.e., one which renders all windows to a texture and displaying that with optional zooming and panning effects). Block artifacts eventually appear on the desktop (actually on the texture, as they seem to 'stick' to a certain area of the desktop even when zooming out). Each appears to be a random bitmap of about 16x16 pixels large and each has a single color with transparency (i.e., each pixel is either lit 100% to the color for the block or transparent). Each block seems strictly aligned to a grid that has the same cell size as a single block. A block disappears after window content is refreshed (screen part gets overwritten).

The card is new and has never been overclocked. It has started to show these artifacts after the first or second week. It has not been used interactively in the first week (i.e., I have no data whether it produced these signs out of the box) as the computer was running burn-in tests.

As a quick test, replacing the card with an nVidia 9500 GT does make the artifacts disappear, but of course it is not a solution.

Using openSUSE 12.1 (x86_64) Asparagus;
Linux 3.1.9-1.4-desktop #1 SMP PREEMPT Fri Jan 27 08:55:10 UTC 2012 (efb5ff4) x86_64 x86_64 x86_64 GNU/Linux;
nvidia NVIDIA-SMI 2.285.05, Driver Version: 285.05.33;
GPU card: Gainward nVidia GTX-580 3GB. (not GTX-280)

[http://postimage.org/image/9vdsiin0b/](http://postimage.org/image/9vdsiin0b/)

[IMG]http://i41.tinypic.com/2afbwns.jpg[/IMG]

[[IMG]http://imageupload.org/thumb/thumb_219718.jpg[/IMG]]("http://imageupload.org/en/file/219718/gpu-artifact-zoom.jpg.html")

---

### Post by nvartifact on 2012-04-26
The card is on the way back. I'll keep you posted on the resolution.

> **nvartifact said:**
> Is this card defective, or am I only seeing a power supply, driver or other issue? Generally, how do you diagnose or reproduce such an issue (under Windows) for the repair technicians?

I'm using a compositing window manager (KWin) for my desktop (i.e., one which renders all windows to a texture and displaying that with optional zooming and panning effects). Block artifacts eventually appear on the desktop (actually on the texture, as they seem to 'stick' to a certain area of the desktop even when zooming out). Each appears to be a random bitmap of about 16x16 pixels large and each has a single color with transparency (i.e., each pixel is either lit 100% to the color for the block or transparent). Each block seems strictly aligned to a grid that has the same cell size as a single block. A block disappears after window content is refreshed (screen part gets overwritten).

The card is new and has never been overclocked. It has started to show these artifacts after the first or second week. It has not been used interactively in the first week (i.e., I have no data whether it produced these signs out of the box) as the computer was running burn-in tests.

As a quick test, replacing the card with an nVidia 9500 GT does make the artifacts disappear, but of course it is not a solution.

Using openSUSE 12.1 (x86_64) Asparagus;
Linux 3.1.9-1.4-desktop #1 SMP PREEMPT Fri Jan 27 08:55:10 UTC 2012 (efb5ff4) x86_64 x86_64 x86_64 GNU/Linux;
nvidia NVIDIA-SMI 2.285.05, Driver Version: 285.05.33;
GPU card: Gainward nVidia GTX-580 3GB. (not GTX-280)

[http://postimage.org/image/9vdsiin0b/](http://postimage.org/image/9vdsiin0b/)

[IMG]http://i41.tinypic.com/2afbwns.jpg[/IMG]

[[IMG]http://imageupload.org/thumb/thumb_219718.jpg[/IMG]]("http://imageupload.org/en/file/219718/gpu-artifact-zoom.jpg.html")

---

### Post by nvartifact on 2012-06-04
Sorry for the late reply, we've just received the replacement card from far away (or at least we hope it's a new one). I'll examine the relevant new posts and links on the OpenSUSE forums and try to reflect on each one and start new guided research. I'll be still watching this place if you have any ideas.

Standard ESD handling precautions have been again followed when inserting the card.

The computer has just been started, was running mostly idle on a desktop - basically clicking on windows and doing text editing produced the artifact again on this new card in less than half an hour. Room HVAC was running. Overheating is thus not probable.

Chassis: Supermicro sc743tq-865b-sq black 4u rack
(from text: PSU 865W, AC cooling redundant, 80+ certified)
[http://www.avadirect.com/product_details_parts.asp?PRID=14077](http://www.avadirect.com/product_details_parts.asp?PRID=14077)

All 3 power cables inserted into the GPU.

We have ECC memory, so no memory errors are possible.

If nothing helps, we'll write OpenCL tests for memory and processing consistency.

---

### Post by nvartifact on 2012-06-05
Verdict: driver bug. The problem has been silently fixed in the new Nvidia beta driver version 302.07 released on the 2nd of May - a week after detecting and RMA'ing the card!

Do look out for that the regular download pages do not list this, so you need to click either the Unix archive or the "beta or older downloads" page to fetch it.

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

Can I mark this topic solved?

---

