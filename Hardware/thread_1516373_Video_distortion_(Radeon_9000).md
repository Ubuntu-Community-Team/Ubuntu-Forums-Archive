---
title: "Video distortion (Radeon 9000)"
date: 2010-06-23
forum: Hardware
---

### Post by sam.turton on 2010-06-23
I've recently installed 10.4 on my Thinkpad T41, and it's great apart from an issue with the graphics.

The card is a ATI Radeon Mobility 9000 (32 meg).

When doing anything graphically intensive - flash video, screensaver, divx video - after about 3 minutes, small random patches of distortion start to appear all over the screen.  Kind of looks like a scrambled cable channel, but only in small patches.  Not just restricted to the window which is doing the activity (like a video), but across the whole screen.

The distortion disappears again once the computer has returned to idle - e.g. swapping back to an internet tab which isn't doing any flash video.  The problem is definitely not program specific - seems to happen with anything graphic.

I've tried reinstalling ati and radeon ubuntu drivers - no change.  I've tried specifying "nomodeset" in the grub kernel, which made things much worse - distortion appeared a lot more, even when just moving windows.  I know I can't use the proprietary drivers because of the legacy card.

Other than performing updates and installing vlc, I've not altered Ubuntu at all since a fresh install of 10.4.

Any suggestions would be much appreciated, as I'm pretty stuck, and really want to watch video on my machine.

Thanks in advance.

---

### Post by sam.turton on 2010-06-27
Bump.

Any ideas anyone?

---

### Post by waynefoutz on 2010-06-27
Do you have desktop effects turned on? Kill them if you do. My old laptop had that card, it wouldn't play video with the effects turned on.

---

### Post by sam.turton on 2010-06-28
Thanks for the heads-up -  I've turned off desktop effects, but the problem's still there. think I might need to make a custom Xorg config, but I don't really know where to start.

---

