---
title: "[SOLVED] Transparent, black terminal with opaque, white text? Blurred background behi"
date: 2008-07-11
forum: General Help
---

### Post by hung0702 on 2008-07-11
(1) I've seen a few attached pictures of people who have terminals with transparent, black backgrounds and white, opaque text. I can make the terminal transparent, but I can't change the colors and make the text opaque. Black-on-white text makes transparent terminals difficult to see. Anyone got a useful thread/link/advice I can follow?

(2) I use emerald as my windows manager and use a theme that has a Vista-like frame. The problem is that unlike Vista, the frame is fully transparent and not translucent. Instead of blurring out everything behind the frame, it shows through clear as day and makes it difficult to read the name of the window sometimes. Yeah, looking at what's in the window would probably tell me what program it is, but I want my desktop to look amazing. Also, that's usually the first thing people point out when they criticize my preference of Ubuntu over Vista (dual-booting). Does anyone know of a theme that already has blurring built-in, or an emerald plug-in that would achieve this effect?

---

### Post by mgmiller on 2008-07-12
Try this:

First turn on blur effects:
in Compiz Config Settings Manager (Advanced Desktop Effects Settings)
Turn on the "Blur Windows" effect.
In the General tab set the Blur Filter to Mipmap for maximum blur or gaussian for less blur.

Finally, enable it for emerald themes:
in emerald theme manager
go to emerald settings tab 
go to compiz decoration blur type 
select either "title bar only" to just blur behind the title bar
or "all decorations" to make everything behind the window border also blur.


To change the terminal:

Open a terminal window.

Click on Edit > Profiles.

Click on Default to select it and then click on "Edit".

Go to the Colors tab and uncheck "Use colors from system theme"

Now you can change the text color and background color to anything you want by clicking on the colored squares next to "Text color:" and "Background color:"

---

### Post by hung0702 on 2008-07-13
Thanks a heap! I can't believe it was right under my nose the whole time!

---

### Post by sayakb on 2008-07-13
Please mark the thread as solved.

---

### Post by hung0702 on 2008-07-13
solved

---

