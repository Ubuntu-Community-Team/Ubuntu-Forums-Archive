---
title: "Ubuntu problem, hard to explain"
date: 2010-06-27
forum: Hardware
---

### Post by SekiTimewalker on 2010-06-27
Ok, this is a weird problem I have. It's with Ubuntu 10.04, Lucid Lynx. Took over eight hours to do a basic fix, but it is still a problem. I downloaded Ubuntu last night, and the right side continued past the end of my screen. Same with the bottom. I found out it had to do with the basic Linux drivers. So I, then, tried installing the new Nvidia drivers. I managed to get it to work, but it would only start in low graphics mode which would switch everything so right was on the left part of the screen, there was a small line down the screen, and then the left side was on the right (though I had to scroll my mouse off the left/right end to get to the right/left side). Confusing, I know. Anyways, I finally found a way to fix it by deleting the xorg.conf file. This would allow me to load ubuntu, but only in either 800x600 or 640x480 resolution. It should allow me to load all the way up to 1920x1080. Any fix I could find made me go through xorg.conf, which would cause the low graphics problem I had before, until I delete the file again. Is there any help for this? My computer is a Sony Vaio F series and the graphics card is GeForce GTX 480.

From what I can tell, this problem is also preventing wine from running well, I get an error no matter what I try to run.

A few more things I felt should be said. According to the NVIDIA panel, I don't have a NVIDIA driver active. According to the Monitors area, I do as it brings me straight to the NVIDIA panel. And according to the Hardware Drivers, I have the recommended NVIDIA driver.

---

### Post by hansdown on 2010-06-27
Welcome to the forum, SekiTimewalker.

Click system> administration> hardware drivers.

It should find the drivers that are available.

---

### Post by SekiTimewalker on 2010-06-27
I did. Whenever I do that, I get the same low quality error and the same stuff happens with it switching sides. And thanks for the welcome.

---

### Post by macgeek417 on 2010-06-27
You mentioned Nvidia drivers? IIRC, the Nvidia settings panel has a spot to change the resolution. Though you might need to revert your xorg.conf file.
Just change your screen resolution to the max - On mt laptop if the resolution is changed I get this exact same problem.

:)

---

### Post by SekiTimewalker on 2010-06-27
Well, a new problem just popped up where I have 0 sound whatsoever coming even when everything is maxed in sound. But, as for the nvidia panel, I get 

"You do not appear to be using the NVIDIA x driver. Please edit your x configuration file (just run 'nvidia-xconfig' as root) and restart the x server."

However, once again, anything to do with the xconfig causes the low graphics/screen problem I have to begin with.

---

### Post by macgeek417 on 2010-06-27
I know, the graphics problem you referred to should be fixed by enabling the driver and switching the resolution like I said earlier - it does for me.

Besides, if it doesnt work just revert it.

:)

---

### Post by SekiTimewalker on 2010-06-27
All that happened is that I typed "sudo nvidia-xconfig" restarted, and the low graphics/screen issue happened again. So, I went back into the panel, and it still said that I had to type that again.

---

### Post by Rasa1111 on 2010-06-27
are you sure you dont just need to adjust the monitor itself?

When I installed Ubuntu on my moms PC, 
the whole bottom of the screen, and both sides were "off/past the screen.

I wasnt sure what to do..
but turns out I only had to press a couple buttons on the monitor to set it correctly.

Sorry if Im confusing your problem and this has nothing to do with what you need. lol

---

### Post by SekiTimewalker on 2010-06-27
This is a laptop and doesn't have any buttons like that. But, thanks for trying.

A few more things I felt should be said. According to the NVIDIA panel, I don't have a NVIDIA driver active. According to the Monitors area, I do as it brings me straight to the NVIDIA panel. And according to the Hardware Drivers, I have the recommended NVIDIA driver.

---

### Post by Rasa1111 on 2010-06-28
oops. doh!
mybad. 
good luck mate.

---

### Post by Soulmaster on 2010-06-29
I had the same problem with my VAIO VPCF115FM.  It came from the monitor not putting out its extended display identification data (EDID) such that Ubuntu could read it.  Ubuntu doesn't know how big the screen is so it guesses on the large side.

My buddy found a work around if you're dual-booting Windows (which had the appropriate screen size for me).  The basic idea is to scrape the EDID info from Windows and create a custom EDID file from this in Ubuntu.  Details in this post: [http://ubuntuforums.org/archive/index.php/t-316985.html](http://ubuntuforums.org/archive/index.php/t-316985.html)  which was derived from: [http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26](http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26).

---

### Post by Soulmaster on 2010-06-29
As for the sound issue I had that as well.  Check out: [http://ubuntuforums.org/showthread.php?t=1452089](http://ubuntuforums.org/showthread.php?t=1452089).  Worked for me.

---

### Post by mr clark25 on 2010-06-29
taking a stab in the dark here...

have you tried playing with the "font" or "CRT/LCD" buttons? (on my laptop, you must hold the "fn" key)

i had a similar issue with my dell latitude c800, and i was able to make the screen small and then big again using the "font" key. this then fixed the odd display.

---

### Post by SekiTimewalker on 2010-06-29
I figured it out. My friend sent me his friends xorg.conf file, as we have the same computer, and then I disable the splash screen and everything works perfectly in 1920x1080 res.

---

