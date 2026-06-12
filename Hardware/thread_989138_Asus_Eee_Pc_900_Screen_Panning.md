---
title: "Asus Eee Pc 900 Screen Panning"
date: 2008-11-21
forum: Hardware
---

### Post by daveerickson on 2008-11-21
Not sure if you would call it a Virtual Resolution, or Screen Panning or what have you...

I have a 900 eee that came with XP, I set it up to dual boot with 8.10 and installed the array.org kernel, life is good.

What I am looking to do is replicate functionality from the XP side, mainly being able to set a 1024x768 resolution on a 1024x600 physical screen. When you move your mouse beyond the physical screen in the vertical direction the virtual screen pans so you application windows that are larger than 600 pixels can be seen.

I have spent the last 2-3 days struggling to get this to work. I have messed with the xorg.conf settings and still no dice. It seems to have something to do with the video driver used. I found a guide that works on 7.10, and 8.04 I think, but nothing for 8.10. The guide installs 915resolution and uses the i810 driver instead of the intel driver. Then you can set Virtual in xorg and away you go.

Now with 8.10 915resolution has been removed from the repositories and from what I can gather you are supposed to use xrandr to make such changes. I have actually been able to increase the framebuffer to 1024x768 and it acts like it really is that long based on mouse movement, I drag it down past where i can see and slowly move it up and it seems to take about the right time to finally be visible again. But no panning. :(

I even tried changing the physical pointer with a virtual pointer via an xorg setting. Still didn't work.

I know that there is a compiz plugin that will allow you to alt click and drag to move a window around, and there are ways to scale the screen, but I can't use compiz with the netbook launcher so that is a no go too.

Anyone out there have the same issue? Anyone solved it? Any ideas are greatly appreciated. Thanks.

Dave

---

### Post by daveerickson on 2008-11-24
Bumping this up. I am sure someone knows the answer. :)

---

### Post by daveerickson on 2008-11-25
Still looking for any kind of solution. Thanks.

---

