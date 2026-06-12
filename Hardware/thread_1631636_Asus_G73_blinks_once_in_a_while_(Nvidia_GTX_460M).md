---
title: "Asus G73 blinks once in a while (Nvidia GTX 460M)"
date: 2010-11-26
forum: Hardware
---

### Post by Mobidoy on 2010-11-26
I got a new laptop Asus G73JW which has a Nvidia GTX 460M. I have installed the latest Nvidia driver to see if it would prevent it fron blinking only once, once in a while but, no luck, I have also tried to disable Desktop effects but still no luck.

Anyone has an idea of what should I look at or try ?

---

### Post by Mobidoy on 2010-11-27
it is getting on  my verves lol, anyone has an idea ?

---

### Post by Mobidoy on 2010-11-27
Anything ?

---

### Post by delca85 on 2010-11-28
I have the same notebook and the same problem. 
Nobody can help us?

---

### Post by Mobidoy on 2010-11-29
Lets give it some visibility AKA shameless bump

---

### Post by 0_irishboy_0 on 2010-12-14
I just purchased the same laptop.  Disabling PowerMizer Monitor corrected the issue for me. 

System - Administration - NVIDIA X Server Settings

Then on the left hand menu, click nvidia-settings Configuration and uncheck "PowerMizer Monitor".

---

### Post by delca85 on 2010-12-15
I have tried your way but my screen keep on flickering!

---

### Post by Mobidoy on 2010-12-15
Tried it too, issue still present... 

easy to see, after you change it, scroll a webpage pretty fast and it will blink, just stay put for about 10 second and you will see it again.

Edit: But still, it is one heck of a Laptop :)

---

### Post by annemendez on 2010-12-15
it's still under warranty i guess. you can have it checked by someone who's authorized. ;) they might be able to help you.

---

### Post by Mobidoy on 2010-12-15
> **annemendez said:**
> it's still under warranty i guess. you can have it checked by someone who's authorized. ;) they might be able to help you.

Naaah no need to get it check, the problem is with the Nvidia driver. It works without a glitch under Win 7 or under Ubuntu with other drivers other than proprietary...

---

### Post by lrgmmc on 2010-12-22
When you say the latest driver are you talking about the one from ubuntu repo's or the nvidia site?

---

### Post by delca85 on 2010-12-23
@Mobidoy are you able to make 3d effects working without nvidia proprietary drivers?

---

### Post by Mobidoy on 2010-12-23
I am talking about the proprietary drivers, Nvidia, 260.19.29

I have not tried using the repo drivers so I cannot tell you if 3d effets works with them. SOrry

---

### Post by delca85 on 2010-12-23
> **Mobidoy said:**
> Naaah no need to get it check, the problem is with the Nvidia driver. It works without a glitch under Win 7 or under Ubuntu with other drivers other than proprietary...

I was referring about this. You have told that your pc works without a glitch under Ubuntu with no proprietary drivers. But are you able to make 3d effects working with these no proprietary drivers?

I hope I have understood well.

---

### Post by Mobidoy on 2010-12-23
> **delca85 said:**
> I was referring about this. You have told that your pc works without a glitch under Ubuntu with no proprietary drivers. But are you able to make 3d effects working with these no proprietary drivers?

I hope I have understood well.


When I installed Ubuntu, I did not intall the proprietary drivers for a while and, never noticed the flickering. But I have not try to run the 3d settings. I only did it after I installed the drivers from Nvidia. 

So yeah, I had no problems with the repo drivers (not that I noticed) but, no I have not gave 3d settings a try while I was on those drivers... :)

---

### Post by delca85 on 2010-12-24
Ok, I have understood and I have been in the dame situation. 
Thanks for the reply!

---

### Post by Mobidoy on 2010-12-24
> **delca85 said:**
> Ok, I have understood and I have been in the dame situation. 
Thanks for the reply!

I may be in error but I think that this issue can only be solved by Nvidia.

---

### Post by delca85 on 2010-12-24
Unfotunately, I think you are right.

---

### Post by efflandt on 2010-12-25
> **Mobidoy said:**
> I am talking about the proprietary drivers, Nvidia, 260.19.29

I have not tried using the repo drivers so I cannot tell you if 3d effets works with them. SOrry

Actually nvidia 260.19.29 drivers **are** in the repos for Lucid or Maverick if you add x-swat to your repositories.  So you are apparently using 260.19.29 from nvidia.com website instead of from the repos.  I don't know if video works any better for that card with same drivers from the repos, but kernel updates would certainly go smoother with repo drivers, because they would automatically include the necessary modules for the nvidia version.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Or if default nouveau drivers work OK, you might want to try libgl1-mesa-dri-experimental to see if that allows you to do desktop effects (although, it is likely to be much slower than nvidia drivers).

---

### Post by airjaguar on 2010-12-27
Hey guys! I just bought G73JW last week, and I had the same problem, but I found some method seems working for me. At least I haven't had that problem since I did it.
 
Its similar to what "0_irishboy_0" mentioned. but instead of go to graphical setting.

I edited  /etc/X11/xorg.conf directly

just put

Option "RegistryDwords" "PowerMizerEnable=0×1; PerfLevelSrc=0×3322; PowerMizerDefaultAC=0×1"


between "Section Device" and "EndSection" 

save it, then problem solved!
hope its helpful!!

regards,
Hao

---

### Post by delca85 on 2010-12-29
@airjaguar Yours is just one way to set gpu always at maximum performance. Indeed the gpu temperature go up immediately.
The flickering problem is solved, but I don't know it is very good for notebook health.

---

