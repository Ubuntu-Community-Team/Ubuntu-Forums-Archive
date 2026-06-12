---
title: "Dual Head Setup"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by MikeBee on 2008-03-23
Hi all,

This one is driving me crazy. I have a Dell D600, currently running Hardy Beta.

The laptop has an internal display of 1400x1050 which is driven from the internal ATi Mobility Radeon 9000. The screen looks great with the 'ati' driver which Hardy popped in there by default. I've switched to the 'radeon' driver and the text now looks very blurry (the resolution is correct for the display before you ask). However, that's not my primary issue.

I sometimes connect the laptop to my 32" Sony LCD TV at a resolution of 1360x768. This worked fine in Windows and I could watch videos at full screen through the external VGA port.

Connecting this up in linux is a no go. Plugging in gives me no display. Restarting X gives me a mirrored display at 1024x768 also resetting the built in display and giving me no hardware acceleration on the external display. I just can't get the thing to work.

This is a show-stopper for me. These things should just work - how many people run linux on laptops and use an external display hot-plugged when they need it? As I've said above, this is a no-brainer in windows and a no-brainer in Mac OS X, it should be a no-brainer in linux but it's not.

Any advice appreciated.

---

### Post by NemoTheLobster on 2008-03-28
Try using xrandr to change the modes.  Or make it easier and 'apt-get install grandr'.

I agree, it should just work.  I tried restarting X and messing with the xorg.conf for a long time before I found out that it's all trivial to do with xrandr.  Mine's all Intel though, donno how it is with ATI.

Also, if you're trying to do Dual-Head, make sure your virtual desktop size is large enough to accommodate both screens, otherwise it forces you to clone.

---

### Post by goldenshale on 2008-04-29
It all does just work on my T42.  Everything.  The only catch I've found so far is that I have to start X with the external monitor connected in order to get the full widescreen resolution.  I can do it once and then disconnect and sleep and reconnect as many times as I want and it all works correctly, but you have to start X initially with the screen connected.  I think it has to allocate the screen buffer, so it just doesn't have the memory for a widescreen unless it knows you have one.  I'm still rying to figure out how to tell it to always allocate the big one though.  Note, you don't have to reboot the machine to get full resolution, just connect the external, logout, login and now in the Screen Resolution control panel you should be able to configure both.

This is a HUGE step forward for those of us who are used to the yearly battle with X.  Word is this problem should be fixed soon as well.

---

### Post by alek01 on 2008-05-09
Also, if you're trying to do Dual-Head, make sure your virtual desktop size is large enough to accommodate both screens, otherwise it forces you to clone.[/QUOTE]

Could you please explain the "size of the virtual desktop"? after disastrous upgrade from 7.1 to Hardy I have made a fresh install of Hardy and it does see the 2 screens but I cannot change the "Clone screen" option. It used to work perfectly as I had adjusted manually in previous version.
Thks.

---

### Post by rjp-lapama on 2008-05-18
Hi NemoTheLobster,
You're a star with this tip. I installed 'grandr' and could setup my external monitor with no sweat!!! Now I have to figure out how to set it up as a virtual screen, which is sometimes more usefull then just a clone of the laptop screen..

Renee

---

