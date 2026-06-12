---
title: "no drives in BIOS, can't get in even in safe mode!"
date: 2008-11-22
forum: General Help
---

### Post by gfixler on 2008-11-22
I'm having quite a Friday night here. First, some full disclosure...

I have a Matrox TripleHead2Go Digital Edition which is a splitter box that takes one DVI output from the PC and splits it to 3 DVI outs that go to 3 monitors. I have 3 19" Dells each at 1280x1024 (max rez for them and the MTH2G).

I've been for the past few days coming back to my machine in the morning after waking up, or after work to often find it hung in screensaver mode, sometimes very mildly contorted, but with everything frozen. I can't kick to a shell, move the mouse, escape the frozen ssaver, or do anything but reboot.

Tonight after work it was like this again, so I hit reset. When it came back up, the first BIOS screen - which is always stretched over the three monitors - had vertical columns here and there the full height of the monitors, about 1" wide, and made of a bunch of equal width horizontal white lines spaced evenly. It looked kind of like tire tracks over the BIOS. The next screen they were gone, which would seem to imply the monitors were fine. The rest of the text scroll (white text on black) looked fine.

However, then when the Ubuntu splash/loader screen came up, there were thin vertical lines in groups of 3 or 4, in large collections of maybe 10 or so in a few places. These were all in reds, oranges, and yellows, though not really the Ubuntu logo colors - more saturated.

It kicked from there back out to a text scroll, which might be normal, but seems weird. I have long boot up times, so I don't usually sit there for 5 minutes with it, so maybe the Ubuntu loader with progress bar, and then kicking back out to more scrolling text is normal. However, then when it rapidly went through the last things - starting up services and whatnot - it just all went black suddenly. I should get the NVIDIA splash at that point, but I don't. Even the monitor indicated it wasn't getting a signal (power LED went yellow).

I've rebooted a bunch, disconnected the Matrox splitter box to plug in just one monitor (same vertical bands as before - same everything), so it's not the Matrox box. I powered down, went in and took out the graphics card (NVidia GeForce 8800GTX), checked it (looked fine), vacuumed dust out of everywhere, seated it back in firmly, plugged in just the one monitor, fired it back up - same thing.

I also tried booting up in safe mood. It was basically the same thing then. I ran the safe mode package fixes - it all seemed fine - and the X configuration bit in the safe mode menu, which just immediately said X was up and fine, so I kicked back out, and it finished trying to load, and immediately went all black. When I hook up 3 screens, it all goes black at that point, but then also the two side monitors lose signal (text pops up saying it can't display that mode), and the middle one goes black, and into sleep mode (amber light). I've tried in the darkness to enter my username and password, but it's just frozen. I have to hit reset.

More distressingly, in the BIOS screen there are no drives listed in the IDE Channel section. All the master/slave entries list [NONE], and none will find anything if I autoscan. However, as the machine is booting up, with the text scroll, I can see the names of the drives go by. It's seeing them out there - just not in the BIOS configuration menus. Also, it is running through most of the Linux boot sequence, so I know that drive is working.

I'm running a very long memtest now (no problems so far), and later will try booting through the safe mode into a shell. It might just be an X problem at that point, but that doesn't explain away the full-height screen glitches I'm seeing in the first BIOS screen still, and in the Ubuntu splash/loader screen. It could be the video card, and maybe a glitch in there is conflicting with X just as the NVidia blob should load, and halting everything to a black screen. That seems likely, and I think I will also try a different video card later tonight. However, that doesn't explain the lack of HDDs in the BIOS screen. Hopefully it isn't the mobo. Maybe it's a BIOS battery?

Another thought has occurred to me. Either recent updates were causing the screen freezes, or it was a wonky mobo (Gigabyte, new earlier this year - no problems until now), or I've been getting brownouts I don't know about, causing things to freeze, ultimately borking something in the mobo or video card.

So summing up, a question: Anyone have any idea what's going on here? This seems pretty far reaching.

---

