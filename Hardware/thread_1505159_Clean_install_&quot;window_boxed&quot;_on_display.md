---
title: "Clean install &quot;window boxed&quot; on display"
date: 2010-06-08
forum: Hardware
---

### Post by KA8WTK on 2010-06-08
All,
  I have a clean install of 9.10 with all up-dates. Ubuntu is the only operating system. The display is window boxed all the way around with a wide black border and will only allow 800 x 600 resolution. It appears that 9.10 is only using the middle 800x600 area of my 1024x768 screen.
  The graphics are Intel 82845G. Xorg.conf says it is using the "vesa" driver. (should be intel?) AMI bios are used. The manual for the computer does state that it is not "fully DOS compatible" and will display DOS in a box just like Ubuntu is displaying in. But, Ubuntu isn't DOS so I don't know why this is happening.
  Of course I would like to get back to 1024x768 on this machine. Any help is appreciated.

Thanks,
       Bill

---

### Post by quixote on 2010-06-09
vesa is the generic graphics driver that only goes up to 800x600.  I don't have the time right now, but the procedure would be to search the forums for 82845G and xorg (both in the search box) and see what comes up.  There should be recommendations for better drivers and how to get 9.10 to use them.  I'll check back by in a day or so and try to find something for you.

---

### Post by KA8WTK on 2010-06-10
Thanks in advance for any help!
I have tried the "intel" and the "i845" driver in xorg.conf, but I get the message that they don't exist even though the xorg packages that contain the drivers are loaded. I feel like I am missing a step.

Bill

---

### Post by quixote on 2010-06-14
I really tried to find something useful, but I don't see an xorg.conf posted for this specific situation anywhere. :(  It's going to be an easter egg hunt for the best driver for your situation, and the right way to edit xorg.conf, unless an expert jumps in!

Maybe post your xorg.conf?

---

