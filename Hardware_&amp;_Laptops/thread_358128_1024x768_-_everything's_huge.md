---
title: "1024x768 - everything's huge"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Cloudane on 2007-02-10
Compared to my Windows installation (sorry... EX Windows installation) the 1024x768 resolution (which I prefer on this monitor) is absolutely massive.  Everything's big and in-your-face - fonts, toolbars, buttons etc.  But especially the fonts e.g. the top few rows of Mozilla Firefox take up like 1/5th of the screen because of the huge fonts.

Is there any way to scale things down a bit, I'm guessing a DPI setting somewhere or...?

---

### Post by rucadulu on 2007-02-10
Can you please post a screen shot, because what you described does not make since. There should not be any major difference between Windows and Linux if the resoultion is set the same. 

Russell

---

### Post by voided3 on 2007-02-10
Hello. In my opinion, the Ubuntu desktop likes to see at least a 1280x1024 resolution with stock font sizes since off the bat and I have noticed, too, that they are quite large when running 1024x768 especially. Reducing the font sizes, choosing a slimmer window manager theme, and making the toolbars smaller are a big help. I have an lcd on one of my comps that only does 1024x768, so i do all of the above and set up the bottom toolbar to look like a Mac OS X dock  (i.e. a non-expanded, translucent bar with only app shortcuts, a divider, and the trash) and then I make it so that it has the hide buttons, but without the arrows. That way you can move it out of the way for more space. In addition, I set the icons to a 75% zoom and the list views at the smallest 25% to make some space. Also, firefox has a fullscreen mode that really makes some room for browsing. Hope this helps!

---

### Post by RandomJoe on 2007-02-10
I haven't tried this with Ubuntu, but on my Slack installs (KDE) on my C840 laptop I had the same issue - KDE was using some HUGE fonts eating up screen space.  The issue, though, was a little different from yours - the C840 screen had an extremely high resolution for the small size, 1600x1200 in a 15" FP.  X or KDE was taking that and trying to meet some minimum physical font size by scaling things up.

To fix it, I added the following line to the Monitor section of the xorg.conf file:
```

DisplaySize 388 291

```
The sizes are width and height in millimeters.  Basically, I told X that the monitor was really bigger than the FP reported itself.  So X/KDE scaled the font sizes down.  I think the only thing to watch is make sure you keep the X/Y proportions the same as your actual monitor - things may get weird looking if they're not right.

Not sure that'll help in your particular application, though...

---

### Post by Cloudane on 2007-02-10
Here's the screenshot.  It reminds me of being stuck in 640x480 in Windows 95.  As ever a screenshot doesn't really do justice to how bad it is.

Thanks for the suggestion RandomJoe  but it didn't make any difference.

Guess I'll just run in a higher resolution - for now - but I don't consider it a valid answer.  I'd like to see a *proper* answer to reinforce my faith in Linux, but as ever... a kludge will do!

Edit: running at 1280x1024 where it looks great.  Perhaps a little wide, as expected as it's a different aspect ratio.  I'd definitely prefer to run at 1024x768.

Edit2: 1152x864.  That looks quite good, it looks just like 1024 on Windows.  The fonts are still a bit large but much better than 1024 and the aspect ratio doesn't make my eyes bleed.

---

### Post by neji on 2007-02-11
You can try changing the font settings from 96dpi to something like 72dpi, see if that helps you

---

### Post by Poman on 2007-02-12
I'm having this same issue with the same size LCD screen. Is there some guide to setting the best resolution and fonts?

Thanks,

---

