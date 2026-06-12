---
title: "Can Riva TNT2 M64 3D?"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by cemy on 2007-06-05
I have old card Riva TNT2 M64 on my sistem. I have tried to install new driver from nvidia. and i have tried to change xorg.conf. but my sistem can't run X after install that new driver. After that i remove that driver and back to X driver original. But with X driver i can't install beryl and can see 3D support on my sistem. anybody can help me? please. Or my card not support GLX? :(

---

### Post by nutz on 2007-06-05
> **cemy said:**
> I have old card Riva TNT2 M64 on my sistem. I have tried to install new driver from nvidia. and i have tried to change xorg.conf. but my sistem can't run X after install that new driver. After that i remove that driver and back to X driver original. But with X driver i can't install beryl and can see 3D support on my sistem. anybody can help me? please. Or my card not support GLX? :(

Looks like you need an older driver. If you go to Nvidia's website and select your card chipset which is TNT/TNT2 and then select Linux x86 for your OS this is the driver it give you. Notice it's not the latest one...

This would lead me to believe they stopped support of your chipset around the time this driver was released. But it looks like it would be worth a try to install this older driver...

[http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html)

You get there by going through these prompts...
[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

In this list you will see mention of legacy drivers. This is what your card may need; you may even be able to use the latest one there and not the one I posted above...


Graphics Drivers

Linux IA32
Latest Version: 1.0-9755
**Latest Legacy GPU version** (1.0-71xx series): 1.0-7185
**Latest Legacy GPU version** (1.0-96xx series): 1.0-9639
Archive

Linux IA64
Latest Version: 1.0-5336
Archive

Linux AMD64/EM64T
Latest Version: 1.0-9755
**Latest Legacy GPU Version** (1.0-71xx series): 1.0-7185
**Latest Legacy GPU Version** (1.0-96xx series): 1.0-9639
Archive

FreeBSD x86
Latest Version: 1.0-9755
**Latest Legacy GPU Version** (1.0-71xx series): 1.0-7185
**Latest Legacy GPU Version** (1.0-96xx series): 1.0-9639
Archive

Solaris x64/x86
Latest Version: 1.0-9755
**Latest Legacy GPU version** (1.0-96xx series): 1.0-9639
Archive


Hope that helps...

---

### Post by adityakavoor on 2007-06-05
I'm struggling from past 3 months to get beryl working on my TNT2 card .. but in wain :(

---

### Post by nutz on 2007-06-05
> **adityakavoor said:**
> I'm struggling from past 3 months to get beryl working on my TNT2 card .. but in wain :(


Perhaps yours is a legacy driver issue as well. Try one of those legacy drivers and see what results you get.

---

### Post by adityakavoor on 2007-06-05
When I install the legacy driver through the restricted driver manager my screen resolution doesnt go above 640 x 480.. 
Now I hav come to a conclusion that TNT 2 doesnt support 3d

---

### Post by nutz on 2007-06-05
> **adityakavoor said:**
> When I install the legacy driver through the restricted driver manager my screen resolution doesnt go above 640 x 480.. 
Now I hav come to a conclusion that TNT 2 doesnt support 3d

That is not true. I know for a fact the TNT2 has full opengl support. I used to game hard on one back in the day. you may have to use a modeline to go above 640x480...

I used to play Quake2 with that card at 1600X1200 and get 100fps or better all night long. If it can do that I don't see any reason why it couldn't display desktop effects in a decent manner. Let's see what some of the other member have to say...

---

### Post by Mike_T on 2007-06-09
> **adityakavoor said:**
> When I install the legacy driver through the restricted driver manager my screen resolution doesnt go above 640 x 480.. 
Now I hav come to a conclusion that TNT 2 doesnt support 3d

I 've jad the same problems. Just like nutz mentioned, the TNT2 does support 3D. And it does actually with your resolution of 800x600.

Probably this is a problem concerning the automatic detection of your monitor. Edit the /etc/X11/xorg.conf and check the section monitor. Figure out the maximum horizontal and vertical frequency and change the section as shown in this example:

Section "Monitor"
    Identifier     "NEW PANDA 17"
    Option         "DPMS"
    HorizSync 	   30-95
    VertRefresh    50-120
EndSection

This solved my (resolution) problem. But be carefull to add only the frequencies of your monitor! Don't copy my settings without verification for your monitor (your monitor could be damaged).

Regards

Mike

---

