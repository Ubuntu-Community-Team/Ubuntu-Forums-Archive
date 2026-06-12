---
title: "Laptop HYBRIDGRAPHICS - Ubuntu14.04LTS-14.10"
date: 2015-01-02
forum: Hardware
---

### Post by simon75 on 2015-01-02
Hi there, I own a HP touchsmart tm2, and I feel like my two graphics cards are fighting each other.

I first tried 14.04LTS, and with a fresh install, without any extra monitor, the control panel would show two monitors (green and red). The mouse was always flickering as well. disabling one of these two monitors would stop the mouse from flickering. Also, *radeontop *was originnally showing some processes going on while the two display were enabled at the same time, but then it stopped and it seemed that the two displays were the two gpu. So ... I though it was meant like that, but when I try to let run only the "radeon" display and disabling the "intel" one, I would only get a black screen. Also, I noticed that when both display were enabled the cursor would be able to leave the screen on the side were the "radeon" display is. Mirroring the desktop is making the second display disappear in the system settings, but according to radeontop, it is killing the radeongpu inpu t as well. 

After that, still on 14.04, I tried the AMD drivers as well (from system update) and I would get that message on reboot about running in LowGraphics, but the computer would stay idle for 2 hours. Also, the intel drivers, wich at that point I was unable to say if it would help or not and it obviously didn't. I wanted to use intel-gpu-tools to see wath the intel card was doing... but I couldn't find it or manage to install it correctly 

After a lot of reading ( I realize I still have tons to do ) I came across some newer discussions about hybridgraphics saying that these kind of problems might be fixed in 14.10 (it fixed some problems for some people with hybridgpu ). So I have installed 14.10 hoping I would have a different behavior. And I do. Now on the fresh install (after updates), I still had two displays in the control panel and a lot of graphics element would leave a remanent image (cursor, icons, animations). When I disable the "radeon" gpu, it fixes the problems. But if I try it with the "intel" one, the radeon still seems to send it's output nowhere. This time though, radeontop is never showing activity even when the two displays are enabled. 

I'm gonna now try ith amd drivers on 14.10 to see if I can get Catalyst control center, but it was not working on 14.04 so I'm not hoping much. I ressetted the boudaries for the touchscreen stylus earlier and now I guess I want to reset the vga output destination or something.
s at least. 

In the end, Ideally I would like to have the radeon card running with the third party drivers. Power consumption is not an issue as this computer is not leaving the house. Until now, I am able to run with the intel gpu with the native driver, and I couldn' figure out how to run with AMD card with natives drivers yet. 


Again, thank you for your help, and I am already aware I have to do my own research, but it cost nothing to ask !

---

### Post by simon75 on 2015-01-04
So, I'm still totally unable to use the radeon card ....proprietary driver won't work because it's MUXless (according to x report when booting). I would get that low graphics mode message on reboot and then nothing is happening and I am reading it should work with MUXless hybrid setups. What I understood untill now is that MUXed system have the GPU options in the BIOS, but that MUXless system are actually managing this in the OS and that therefore it should work.....  

I'm able to get the radeon to do a little work by using DRI_PRIME, but it is still not really using the card as the main graphics accelerators. I read somewhere that DRI_PRIME actually has limited uses and therefore it's only helping intelGPU on specifics operations. 

Here is what the most confusing for me: The newest documentation states that Hybrid graphics are now supported with the native drivers, how, where, I mean, I'm trying to turn on the radeon and I can't get a result. Will it just switch on on its own when the system determines it needs it ? Then what would the system look at to decide to use it or not ? 
Also, the oldest documentation is going around the problem using various ways like vga_switcheroo and DRI_PRIME=1. Are these solution what we mean by "supported by the native dirver" ?

So, mainly, why would x tell me it can't use the proprietary driver because MUXless if it's actually what I need to use these drivers. I am probably missing something, but every information I am reading about installing proprietary driver is mostly just saying change it in update control panel and there you go. What about intel drivers then ? Fglrx is for radeon, or for HybridGPU? Do I need to install intel proprietary driver throught the intel installation tools as well if I want it to work. There is not a single page that talk about installing intel stuff at the same time as fglrx but I can I know....  
The only answers I can find on the low resolution startup problems are "your GPU is not supported, forget it", but each time, the users who's asking has a GPU that is in the supported list of fglrx! what the what? I mean, my gpu is in the supported list, so it means it won<t work ? 

A few answers would be really appreciated, whatever bone you can throw me right now is welcome!

---

### Post by _az_ on 2015-01-06
I also have a TouchSmart tm2 and a lot of issues since 14.10

Before that, i was able to use my hdmi-output for an external monitor but now it's basically useless.

Unfortunately, AMD dropped the support for the Chipset [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550] in its newer drivers, so newer X-Versions (above 1.12) are not supported with the legacy drivers.

if you find a way, to enable the radeon card on this model, please let me know. All recommended ways just do "nothing" or at least nothing recognizable.

---

### Post by simon75 on 2015-01-06
Well, it didn't work for me totally but I got some incomplete result following this thread [http://ubuntuforums.org/showthread.php?t=2246301](http://ubuntuforums.org/showthread.php?t=2246301)
I was able to switch to the dicrete card but then I couldnt start lightdm properly. Maybe it is worth a try for you. I have a hd5450 in my tm2, you<re mentionning 4550 so it might work for you

---

### Post by _az_ on 2015-01-12
I searched for a bit more, stumbled over the same thread, and decided to get rid of my 4 years old kubuntu installation in favor of ubuntu studio 14.04.1

So far i'm really happy with it and the hdmi-output finally works, though i have some flickering issues, when using the Intel GPU.

Now i'm implementing some of the scripts found here: [https://wiki.ubuntu.com/HP%20TouchSmart%20tm2](https://wiki.ubuntu.com/HP%20TouchSmart%20tm2)

---

