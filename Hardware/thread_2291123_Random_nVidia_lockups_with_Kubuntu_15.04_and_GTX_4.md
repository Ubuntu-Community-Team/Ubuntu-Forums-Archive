---
title: "Random nVidia lockups with Kubuntu 15.04 and GTX 460"
date: 2015-08-18
forum: Hardware
---

### Post by jorritTyb on 2015-08-18
Hi all,

A few weeks ago I was using Kubuntu 13.04 and suffered from random lockups with my nVidia GTX 460. Usually when doing relatively intensive things like playing Minecraft. When the lockup occured the mouse would keep moving but nothing else worked. I can't click, I can't use the keyboard (pressing caps lock on the keyboard does NOT turn on the caps lock light). The only option is to forcibly reboot the computer. Also the computer will not usually boot up again after this happens. I have to actually power down the computer for some time and then start it up again before it reboots. I was using the proprietary nvidia drivers.

A few days ago I upgraded to Kubuntu 15.04 (basically I did a completely fresh install, I even formatted the HD). After first booting up the freezes were EXTREMELY frequent. Even opening a new tab in chrome causes it to freeze. I noticed it was using the xorg.org drivers. I switched to the proprietary drivers (version 400 something, don't remember and not at my computer right now) and it helped a lot. I could now use my computer for a much longer time. However, when playing Minecraft it suddenly froze again exactly the same way as with 13.04.

I did a bit of investigating on the internet and found several threads of people having similar issues. Some reported it fixed after taking some steps, but most of the times it appeared the fix was only temporary. One suggestion (for example) was to disable powermizer so that the gpu is always running at highest performance/power. That might work (haven't done enough tests to confirm that yet) but that's not really a nice solution for obvious reasons.

One thing I'd also like to mention is that I wasn't able to select nvidia 455 drivers in the system setup for some reason. I could select it but it would immediatelly revert to xorg.org free drivers.

Another thing I don't know is if it is recommended to try the latest nvidia drivers that you can get from nvidia itself. They are a lot more recent but I don't know if there are issues with them if I would try them.

So, what is the recommended way to solve this problem? I haven't found anything conclusive about this but it sure looks as if I'm not the only one with this problem. And btw, I never have this issue on Windows (same computer).

Ah yes, I'm using 64-bit kubuntu btw.

Thanks

---

### Post by jorritTyb on 2015-08-18
> **kvgeorge1-sbcglobal said:**
> This sounds very similar to the issues that I am now experiencing with my nVidia card (Quadro 2000).  I am using Ubuntu 14.04 LTS 64-bit and have just started having the same issues when I go full-screen (I also play minecraft, but haven't seen it there yet since I don't run it full-screen).

Well I also have this issue if I run Minecraft not full screen (I never run Minecraft fullscreen anyway)

---

### Post by jorritTyb on 2015-08-19
Nobody any clue? Also what about the upgrade to the latest nvidia drivers from nvidia itself? Is that recommended?

---

### Post by efflandt on 2015-08-19
I had similar symptoms with a cheap Chinese (Galaxy) GT 430 some time ago just after its 1 year warranty expired while using 64-bit Ubuntu 11.10 at the time. The initial symptom in Win7 was that it would occasionally freeze and then Windows would say something like "Video driver stopped responding, recovered". I had not noticed any issues initially in Ubuntu 10.04 that I still had in another partition. But in 64-bit 11.10 occasionally randomly keyboard and mouse clicks would stop responding to the point that I could not even do Ctrl+Alt+F1 to a virtual text terminal, but the mouse cursor still moved. This did not seem to happen while playing minecraft, it might happen after exiting minecraft or sometimes immediately after logging into X on cold boot. Eventually that also started happening in 10.04. And eventually I would sometimes get strange color patterns on the screen while booting and/or logs during boot from the nvidia driver reported that the hardware was not responding.

I replaced it with an EVGA GTX 550 Ti with 3 year warranty several years ago and never had any such problems since. I did have an issue initially installing 64-bit 14.04 because neither nouveau nor nvidia-current in 14.04 supported my GTX 750 Ti with the new Maxwell chip. But that was just a matter of booting recovery, enabling networking, and from root console purging nvidia-current and installing a newer driver version (nvidia-331-updates worked). Although, I am currently using nvidia-352 from xorg-edgers ppa.

Are you sure that your GPU fan(s) still work. How hot does NVIDIA X Server Settings show your chip is after playing minecraft for awhile. Or try installing **psensor** and which is a gui that can sense (and optionally graph and/or log) cpu and gpu temperatures to see if anything is out of the ordinary.

---

### Post by jorritTyb on 2015-08-19
Well I don't often play games on windows these days but when I did I never encountered anything like this before. Also Minecraft really isn't very heavy on the GPU side. It is heavy on the CPU side though (at least one core).

---

### Post by jorritTyb on 2015-08-22
I just had a major lockup again. However, this time I was prepared. I had installed openssh before that and I managed to connect to my computer while in lockup. The computer itself is not usable (even the mouse doesn't work). However ssh in works (from another computer). The first time I did this trick and I had a lockup the load with top was 37! The top contender in the list was 'trove' but it was only using 0.7% cpu. So I don't know why the load was so high.

However, at this very moment the load is reasonable (started at 3 and now stabilizes on 1.17). The top in the list is now 'Xorg' which is taking 100% cpu. 'trove-api' is on the second spot with 0.3% cpu.

Anything I can do to diagnose this? I have the computer locked up atm and an ssh connection to it so I can do stuff.

Thanks a lot!

---

### Post by jorritTyb on 2015-08-22
Hmm. It just locked up in windows too. Perhaps a hardware problem after all...

---

