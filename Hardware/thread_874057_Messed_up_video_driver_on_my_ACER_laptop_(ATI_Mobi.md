---
title: "Messed up video driver on my ACER laptop (ATI Mobility Radeon card). Please Help !"
date: 2008-07-29
forum: Hardware
---

### Post by EdouardoFR on 2008-07-29
Hi Everybody

I just started on Linux a few days ago... I admit I was forced to as, Windows wouldn't reinstall (2 days trying!). A friend told me to try Linux. I got Ubuntu 8.04: In 15 minutes, my laptop was saved :-) !!! 
My first steps with Linux. And I feel I just embarked on something really cool ! 

But I have been messing around and think I messed a bit too much... Please help !:

I have a laptop: ACER Aspire 5601AWLMi, with an ATI Radeon Mobility x1300. 

By installing the proprietary driver proposed by Linux, I could get 3D acceleration (playing on Nexuiz - fun game btw !) but the screen was flickering every 3 seconds: Very ennoying. So when I played I used to stop the compiz process to get rid of the flickering. But this rendered the system unstable and it would crash from time to time or after playing I would need to reboot to get a cool desktop again. Far from a perfect solution.

So a disabled (un-installed ?) the proprietary driver graphically  and installed an ATI driver: I downloaded  This file: ati-driver-installer-8-7-x86.x86_64.run and launched it from the terminal.
It started the driver graphical installer and compelte the procedure
But before configuring  I forgot to configure it from the terminal and  rebooted. back, I typed aticonfig --initial to configure the care:  Error: It wouldn't want to re-write a file called something like xorg.conf, it was a story of incorrect tag. Qnd Actually the file  wasn't there  :-(.
And there was still no 3D acceleration
I tried various things, got fed up, and did something bad: I re-enabled the Linux Proprietary driver, without un-installing teh other one (I didn't know how to do that).

Of course the computer didn't like that: It wouldn't recognize the video card, so in minimal video config I disabled it again. Things got back to normal, but obviously still no 3D acceleration.

Now if i type 'aticonfig' in the terminal, it says that the package is not installed. I tried again enabling the Linux Prop. driver and again it doesn't recognize the card. So I desacativated it again and now  feel compeletly stuck:

It seems that I have bits and pieces of the ATI driver that enter in conflict with the Linux Prop driver, in other words: a big mess. especially when I am completely and utterly a new bye !

Please help ! What should I do ?

Thanks !

---

### Post by Pulse214 on 2008-11-15
There's a chance the open source driver included in 8.10 has support for 3d acceleration.  you could try that if you haven't fixed the problem yet.

---

