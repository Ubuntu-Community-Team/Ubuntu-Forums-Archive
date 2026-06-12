---
title: "Nvidia or ATI for Laptop?"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-06-16
I'm in the market for a laptop and I wanted one with an Nvidia card for the better driver support.

Yet, most machines have an ATI card, so sticking with Nvidia severely limits my choices (not to mention that the machines are often more expensive)

I have never owned an ATI card (on Linux), I read that there are many problems with the drivers.

What are your experiences with this on Laptops?  Would the lower price and more choice outweigh the potential problems?

---

### Post by chrisubuntu on 2005-06-16
I have an ATI x300 on my Dell.. and whilst I have 2d and 3d working nicley, it took a bit of tweaking (thanks to the awesome ubuntu community on this forum).

I've always had Nvidia on my previous linux installs and have found their drivers work out of the box (perhaps I just got lucky)... with comparable FPS's (in 3d games) with the windows drivers. My current ATI card does not perform anywhere near as well under linux as under windows for the same games, and the image quality is lacking (I get weird effects under linux for some reason and my FPS is often halved.. or worse). 

To fix the speed and image quality I need new drivers....  And that leads me to the clincher: The packaged drivers for ATI seem to be released rather infrequently.... and Im too chicken to try the non-packaged versions :) I'm happy with my Hoary install... and dont want to risk total system meltdown for games at this stage.. I just dont have the patience or the time to troubleshoot.

So, 'iffff I had my time agaaaain' I'd do it with Nvidia.

---

### Post by luca_linux on 2005-06-16
I've got an Asus M6N laptop that came with ATI Mobility Radeon 9600.
I'm getting various issues with this video card and I really think my next laptop MUST have a nVidia card.
To get full 3D acceleration you need fglrx that is the ATI proprietary driver. Its performance are quite good but there are some problems:
1) Suspend modes (S3 (Suspend-to-Ram) and S4 (Suspend-to-disk)) don't work, unless playing around with vbetools...but the suspend level is still not really good.
2) TV-out doesn't work at all.
3) Sometimes there's some "flickering" on the screen...it seems to depend on framebuffer, but it seldom happens even if with the framebuffer disabled.

---

### Post by nocturn on 2005-06-17
It is starting to look that I will not be able to get arround this as the only laptop that suited my requirements with an Nvidia card is no longer on the market.
I think I'll have to take my chances on ATI (still very reluctant)

---

### Post by luca_linux on 2005-06-17
What about ordering a laptop from DELL and customize the configuration online, choosing nVidia instead of ATI?

---

