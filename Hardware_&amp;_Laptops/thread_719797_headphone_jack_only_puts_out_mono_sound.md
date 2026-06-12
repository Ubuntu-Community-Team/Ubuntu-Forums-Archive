---
title: "headphone jack only puts out mono sound"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by skydiver|goose on 2008-03-09
I have a HP Pavilion ZV5000. I'm in the airport right now and my flight was delayed 2 hours, so I pulled out the Family Guy and stuck it in and plugged in my headphones, but I'm not getting stereo sound; only mono. They're Sony Noise-Cancelling headphones ( [link]("http://www.radioshack.com/product/index.jsp?productId=2429419") ) and only the right channel works. When I pull the plug out and then barely put it back in, I get sound through the left channel only. Is that my headphone jack? Or is it an driver/hardware issue?

---

### Post by skydiver|goose on 2008-03-09
bump?

---

### Post by genus_001 on 2008-03-09
If it is pushing through the left channel when you half plug it in, it isn't your headphones.  Do you have ALSA mixer installed?
If you run ALSA mixer, ther are two sections that you should note: the Master volume and the Headphone volume.  Underneath each, there is a fader that goes left and right... this is for your balance, if either on of them is not directly in the center, put them in the middle.
If this doesn't work, it may be the balance control in the actual program that you are using to view your video.  What program are you using?

---

