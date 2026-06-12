---
title: "How do I use TwinView with a 1024x768 projector with a widescreen laptop?"
date: 2010-07-07
forum: Hardware
---

### Post by jdholman on 2010-07-07
Hello All:

I have a Dell Precision M6400 laptop running Lucid 64-bit with the 195.36.24 nVidia driver.  I run my laptop at 1920x1200 and it looks awesome.

At home, I also use an additional display plugged into the VGA port on the laptop running at 1680x1050 configured with TwinView and it similarly looks awesome.

The issue I have is when I travel to a client facility and I have the need to hook up a “low res” projector.  I just can't get these things to work.  These projectors are from various manufacturers from Samsung, to Dell, to Epson and inevitably run at 1024x768.

I can plug in the projector, run the nVidia application, detect the projector, select TwinView, move the projector in the “Layout” panel to the left of the laptop display (which is where I usually position my secondary display), and click “Apply”.  When I do this, the displays go blank as the laptop tries to configure the projector and I always get nothing on the projector.  I must then wait for the 15 second timeout so my native laptop display returns to normal.

I never know what make and model projector a client will have, but it is always 1024x768 and I have had zero success in getting my laptop to work with these.  I REALLY need to get this sorted out.

Any success stories or ideas out there?

Thanks,

Jim

---

### Post by bazzal1941 on 2010-07-07
I'm only getting involved here because I use TwinView but I am not sure I can be much help. I don't know if this helps although you have probably read it.

[http://www.theirishpenguin.com/2010/03/29/hooking-up-a-laptop-to-a-projector-using-nvidia-twinview-on-kubuntu/](http://www.theirishpenguin.com/2010/03/29/hooking-up-a-laptop-to-a-projector-using-nvidia-twinview-on-kubuntu/)

---

### Post by jdholman on 2010-07-07
I read the article you provided which indicates that I need to set my laptop display to 1024x768 before connecting the projector and then overlaying the laptop display with the projector display in the nVidia tool "Layout" window.

I'll try this when I get a chance.  I was hoping to leave the laptop resolution 1920x1200 and only drop down the projector resolution.  My laptop display looks terrible at 1024x768.

Jim

---

### Post by jdholman on 2010-07-12
I hate replying to my own posts...

I can't set any resolution at all other than "Auto" in nVidia.  Setting the resolution to any other resolution results in a black screen although I can see my mouse pointer.  Even waiting 15 seconds doesn't return to the original resolution.  My only alternative is to restart X.

My xorg.conf is attached.  Any way to set this so I can change my resolution on my laptop display panel?

Thanks,

Jim

---

