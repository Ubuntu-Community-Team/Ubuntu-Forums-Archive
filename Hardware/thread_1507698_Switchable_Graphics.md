---
title: "Switchable Graphics?"
date: 2010-06-11
forum: Hardware
---

### Post by instantepiphany on 2010-06-11
Hey all,
I recently installed ubuntu 10.04 x64 on a brand new hp pavilion dv-6, and was suprised to find that everything works perfectly, apart from the brightness applet not showing the level of brightness(i can still change it though). The first time i installed 10.04, after connecting to my wifi, it told me restricted drivers were available. They were the fglrx prop drivers from ati. The laptop has both an integrated intel gma(not sure on the model) and a radeon mobility hd 5650 1gb discrete. I installed the drivers, rebooted, and got a blank screen. Failsafe/recovery kernel did not work either. I reinstalled, decided not to install the drivers, i installed mesa utils and found it was using the integrated, and getting about 4500 fps on glxgears, with direct rendering enabled. Thats ok for most things, but games and heavy 3d editing are much easier with my discrete. Is there switching built in to ubuntu 10.04?
Just in case your about to say, just change it in the bios, ive had a very thorough look through and cannot find anything at all about graphics...
Is there any program i can install that can switch the graphics for me, preferably without rebooting?

---

### Post by ZebCarnell on 2010-06-12
Dude I have the exact same problem and it's doing my head in.

I have a DV6 with ATI 5650 graphics and Intel GMA.

There is no way to disable at the BIOS level and blank screen appears on boot for me also, I just used the nomodeset option to boot in low graphics but thats not going to cut it as far as Im concerned.


PLEASE HELP

---

### Post by instantepiphany on 2010-06-13
> **ZebCarnell said:**
> Dude I have the exact same problem and it's doing my head in.

I have a DV6 with ATI 5650 graphics and Intel GMA.

There is no way to disable at the BIOS level and blank screen appears on boot for me also, I just used the nomodeset option to boot in low graphics but thats not going to cut it as far as Im concerned.


PLEASE HELP
Dude, to make it work, reinstall(I used 64bit 10.04), and connect to the internet. When it says restricted drivers are available DON"T install them. Then everything should be fine except for not being able to use the 5650, only the intel gma. Good little laptop  :D

EDIT: But, I agree this does not cut it, we should be able to use our 5650's instead of cheap embedded intel gmas...

---

### Post by elvodin on 2010-06-13
Theres a thread in Phoronics that may help you.

[http://www.phoronix.com/forums/showthread.php?t=21979](http://www.phoronix.com/forums/showthread.php?t=21979)

---

### Post by ZebCarnell on 2010-06-13
Problem is I need the decent 3D graphics for gaming and visual editing. I bought the laptop specifically because of the ATI 5650.

---

### Post by elvodin on 2010-06-13
And if you check the link its for dual card in lap top, i have used it myself.
I can turn of the the intel card in bios on my laptop, but i have tested vgasvitcharo
and it works.

---

### Post by elvodin on 2010-06-13
The tread is for Arh linuxs but you can send the commands in a root shell.

---

### Post by ZebCarnell on 2010-06-13
Cheers for that mate, I'm going through it now.

I was pointing that response to zzcranjo who suggested using GMA only.

:P

---

### Post by elvodin on 2010-06-13
Ahh, np

---

### Post by instantepiphany on 2010-06-13
@zebcarnell could you please let me know if it works? I would rather not do it if it didn't work for you....
Thanks elvodin

---

### Post by ZebCarnell on 2010-06-13
No worries. I might not have it sorted for a while. Got some away business this week. 
Ill post it back here at some future date, so maybe subscribe to the thread. 

Cheers

---

### Post by radicall on 2010-06-29
> **ZebCarnell said:**
> Dude I have the exact same problem and it's doing my head in.
 
I have a DV6 with ATI 5650 graphics and Intel GMA.
 
There is no way to disable at the BIOS level and blank screen appears on boot for me also, I just used the nomodeset option to boot in low graphics but thats not going to cut it as far as Im concerned.
 
 
PLEASE HELP
 
I haven't tested this yet, but if anyone wants to help with experimental stuff
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
 
If you do get this to work succesfully - please post back

---

### Post by RavensKrag on 2010-07-07
I compiled a custom kernel from a vanilla version of 2.6.34, as it has the vgaswitcheroo code included, and the kernel works, and the graphics switch appears to work, but the ATI drivers are not working as of yet.

Using a HP Pavillion dm4 with an intel/ATI combo.

---

### Post by mosär on 2010-07-08
Got the same issue with a Acer Aspire 4810T (Intel /Radeon HD4330).
I'll try compiling a kernel with the mentioned patches applied and post my results.

---

### Post by RavensKrag on 2010-07-12
I can not seem to get the graphics switch and the ATI driver installed at the same time.  If I install the ATI drivers, then the switch is disabled.  However, the switch comes back if the ATI drivers are removed.

Anyone else have better luck?

---

### Post by hsantanna on 2010-07-28
I have the same problem that you have. 

My computer's model is a Pavilion dv4 2080BR, with ATI / Intel switchable graphics.

I bought the notebook announced with ATI graphics, not Intel graphics. I don't want the Intel one, want to disable it. I contacted HP email support, and I suggest to everyone that have the same problem to do so.

[http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-005&h_lang=en&h_cc=us&h_product=82710&h_page=hpcom&l](http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-005&h_lang=en&h_cc=us&h_product=82710&h_page=hpcom&l)...

Ask HP to release a new BIOS version that allow to totally disable Intel integrated graphics.

Without that option we can't even use the fglrx ATI's Linux drivers and are forced to use windows to play 3D games, than we can't use the most updated ATI drivers, having to stay with older driver versions released by HP (the only ones that support this switchable thing).

:?

---

### Post by JeroenJ on 2010-08-12
Hey guys,

I kinda have the same problem with my hp dv3 2350ed. It also has an integrated (intel GMA) and dedicated (ATI) graphics card. Currently I'm using the drivers from Intel, I think, just a clean install out of the box with updates. The problem I have, and I wonder if you have the same, is hooking up an external screen.

I've connected my external screen using the vga port and there is an output but it is vibrating. It seems that there is a problem with the refresh rate, or something. When using Windows 7 it works fine. Check my earlier post [here]("http://ubuntuforums.org/showthread.php?t=1526571"). Its getting really annoying to work on the 13'' screen while the 22'' is doing nothing...

Any advice is welcome!

---

### Post by hsantanna on 2010-09-16
Here is [my post at Phorolix]("http://www.phoronix.com/forums/showthread.php?p=145549#post145549") about my bad experience with HP DV-4 2080BR (ATI Radeon Mobility HD 4550) on Ubuntu:

> 
I have a very similar problem: can't get fglrx to work because I always get into a blank screen. I'm unsuccessful trying to install fglrx since Catalyst 10.3 (now 10.8 ), on my new HP Pavilion DV-4 2080BR.

The problem in my case, and maybe yours, is that the Intel Core CPU (i3/i5/i7) have integrated graphics, and since I bought a notebook model that also have discrete ATI GPU, in a way that I have 2 GPUs at same computer, with the infamous 'switchable' option.

The bad thing is that Linux kernel is just starting to support switchable graphics, and worst, Xorg totally don't support it.

Be best (fast) solution would be to disable the switchable thing at BIOS, enabling only the ATI GPU. But to my bad luck, that's not an option to me, because there is no HP notebook with BIOS option about switchable graphics.

So fglrx detects something that it don't understand, and, so, I get the black screen thing.

I e-mailed HP asking them for a new BIOS version to disable Intel integrated GPU, so I would get only the ATI GPU detected by my favorite OS.
HP replied saying something that seems to be wrote by a bad-programed-robot, with all nonsense phrases, just copying and pasting my own words from the initial message.
So I replied their response asking for someone that understand what BIOS is. Some days later, a guy e-mailed me, he said that HP will not release a new version of BIOS, and if HP does, it will not contain the switch-off integrated graphics feature. dot.

The good thing is that I still can have hardware accelerated graphics from the i5's GPU. Intel have much better linux driver support than ATI. My KDE works beauty with all those transparency and animations.
Sad that I paid/waist $500 more on this notebook model just because of the ATI GPU and I can't use it. 

I will have better luck on the next buying, keeping away from HP and ATI. Maybe a [Dell]("http://www.dell.com/ubuntu") with [Ubuntu]("http://www.ubuntu.com/dell").


---

### Post by hsantanna on 2010-09-16
> **JeroenJ said:**
> Hey guys,

I kinda have the same problem with my hp dv3 2350ed. It also has an integrated (intel GMA) and dedicated (ATI) graphics card. Currently I'm using the drivers from Intel, I think, just a clean install out of the box with updates. The problem I have, and I wonder if you have the same, is hooking up an external screen.

I've connected my external screen using the vga port and there is an output but it is vibrating. It seems that there is a problem with the refresh rate, or something. When using Windows 7 it works fine. Check my earlier post [here]("http://ubuntuforums.org/showthread.php?t=1526571"). Its getting really annoying to work on the 13'' screen while the 22'' is doing nothing...

Any advice is welcome!
Probably because the both GPUs are enabled, and both are trying to output something. That's my guess.

I have the exactly same problem: (ATI+Intel) = (screen vibrating at VGA). The pain to me is that I'm a teacher, and using the vga output to plug a projector on my classes I have (and hate) to boot on Windows7.

The students don't understand why I say they to use Linux if I'm using windows during the class. That's a shame to me :oops:, so I don't say anything about Linux anymore, at least for a while.

---

