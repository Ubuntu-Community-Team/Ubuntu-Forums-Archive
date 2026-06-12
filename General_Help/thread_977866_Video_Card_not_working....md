---
title: "Video Card not working..."
date: 2008-11-10
forum: General Help
---

### Post by firefly02 on 2008-11-10
Hello, I have a comqaq evo nc6000 laptop. When I updated to the latest vertion of Ubuntu, the graphics card stopped working. I get a message saying that ubuntu is running in low graphics mode. By reconfiguring xorg I have been able to get the message to go away. I still can't enable desktops effects however. Does anyone know which driver I should be using, or how to get it working?
Thanks, Chase

---

### Post by firefly02 on 2008-11-10
I have a ATI Technologies Inc RV350 [MOBILITY RADEON 9100 M10] card.

---

### Post by skralljt on 2008-11-23
i have the same problem with the nc6000 and the ati rv350 chip.  Before I upgraded to 8.10 xubuntu I received a warning that there was no graphics acceleration or something, but I ignored it and continued.  Now there are no proprietary drivers offered, and when I install the proprietary drivers from ati.com it changes nothing.  When i try aticonfig --initial -f I get a segmentation fault.  When I try fglrxinfo I get "failed request" and a bunch of gibberish.  At least I finally got the atheros card working on this by installing wicd and selecting wext for the wpa supplicant driver.  The graphics look normal once you get past all the nagging about reconfiguring x servers.  Just keep accepting the low graphics mode and it looks fine to me.  Now I have to figure out how to get those nag screens to leave.

---

### Post by loomsen on 2008-11-23
You're probably both just not allowed to use your 3d accel.

Add yourself, your user accounts of course, to the group video.

To be able to save/reconfigure your xorg.conf you gotta be root, so invoke your command, whichever it was, with a sudo.

Gl guys

Btw, I didn't ever own a ATI myself, but envyng should work for you I think...
```

sudo apt-get install envyng-core
```

---

### Post by joeinbend on 2008-11-26
Hi all, did you make any progress with this? I am new to Ubuntu, and I also have the same problem. I was able to use the proprietary drivers in v8.04 just fine, I went ahead and updated to v8.10 last night, and am getting the same messages as the first poster.

I am not good enough with Linux yet to figure out how to fix this on my own, just applying other people's solutions to fix my problems :) if anyone has been able to fix this, please post with the step-by-step, if you wouldnt mind!

Thanks!

---

### Post by joeinbend on 2009-01-06
Bump!

I rolled back to 8.04 after having the previous problem back in November, and have been running great since. Any word on a ATI driver release for 8.10 Intrepid?

---

