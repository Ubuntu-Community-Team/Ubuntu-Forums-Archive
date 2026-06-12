---
title: "ATI Mobility Radeon 9200 issues with Wine"
date: 2010-08-06
forum: Hardware
---

### Post by RafaMaster on 2010-08-06
Hi, I'm Rafa,
I'm TOTALLY, ABSOLUTY newbie in this forum and in ubuntu I was (keep being) a Windows User xD.
I got a Compaq Presario R3000 (Intel Mobile Pentium 4)
1gb RAM
2.4 ghz CPU (Intel Mobile Pentium 4)
ATI Mobility Radeon 9200 (pixel shader 1.2 or 1.3 i dont remeber, and T&L, OpenGL, 64 mb Video RAM)
17 gb HD Free
I when i was installing it, i selected the option that says "Install ubuntu insides windows". It made a Virtual disk about 17gb.

Ubuntu works awesome on this system, all effects works great, none hang out or no freezes, just awesome lol... but
I had installed Wine, and then Halo Custom Edition, but when I try to execute it, It shows me up an error message about my video card doesn't meets the minimum requirements, etc etc etc. BUT there's something absoluty crazy on this, It says that I've got a nVidia gforce 3 (I really have ATI Mobility Radeon 9200), SO, when i clicked on the "Continue Anyway" button, The Screen just gets crazy, like the static on a TV Lol. Like my card goes sick or something lolol, the point is that i cant see anything so i have to reset it in bad way (unpluging it).

This is a screenshot of the error:
[IMG]http://img819.imageshack.us/img819/46/screenshothalowarning.png[/IMG]


My theory is that, ubuntu is using wrong drivers for my card, or i dont know, This is my first time under linux D:
So, i really would appreciate if someone could help me :)

Thank you

---

### Post by RafaMaster on 2010-08-06
So nobody can't help me :(?

---

### Post by bprins on 2010-08-07
what version of wine are you using?

---

### Post by RafaMaster on 2010-08-07
I'm using the last released version (1.2 i think). I have been investigating over the Internet and i found that i had to install directx (LOL) i haven't ever though that. BUT after installed and configured it Directx. then I opened Halo, but i couldn't see anything (Black screen), i also tried with Resident Evil 4, and GTA San Andreas, But GTA SA, gave me a error about directx 9.

So, i keep investigating and I found Radeon Drivers or "ati" especially for radeon 9500, 9100, 9200 etc and derivatives (my mobility radeon 9200 is a derivative i think). Uninstalled ATI original drivers and installed "ati". I tried Resident Evil 4, it shown me Select Language Menu, but when i have choosen one, the screen gets black and nothing :S, Halo did the same, but when fully loaded just gave a error and aslo, this driver made me lose Desktop Effects, i tried everything but couldn't fix it to work.

If somebody can help me please, i really would appreciate, by now I'm becoming an ubuntu lover-user, except by the gaming part... its really disappointing :(.

Thank you

---

### Post by bprins on 2010-08-08
I feel your pain. it was quite a struggle for me aswell to get things working properly. I'm far from an expert myself, but maybe I can give you some directions, that helps you resolve the problem.

what you might want to check is what hardware is really configured:
```

sudo lshw -C display

```

this lists your recognized display adapter(s).

If you like to see what other hardware you got:
```

sudo lshw -html > mySpecs.html

```

Might be helpful later. 

Check if ubuntu recognized your VGA adapter:
```

lspci | grep VGA

```

All should state that you have an ATI card.

With that information present, it might make it a lot easier to google more specifc to the problem you are running into.

Further more, if you are running ubuntu10.4 (lucid), maybe you could try to upgrade to the latest wine (1.3) (though I don't expect the problem is within wine).  And if you are not on ubuntu10.4, you might consider upgrading just to try if that helps. 

Again, I'm far from an expert ubuntu user, so if others read my command, please feel free to correct me where I'm completely wrong.

Don't give up though. It's all worth it. Once everything works, you'll be proud.

Keep posting your updates like the output of the commands above, if I can help I will!

Best regards, Bas

---

### Post by RafaMaster on 2010-08-08
Hi, first at all, Thank you for all the help that you're bringing to me :) I really really appreciate it for real, THANK YOU!

I got Wine 1.3 and Ubuntu 10.04, I reinstalled Ubuntu to get the original drivers that comes in it. I Installed Directx and Wine again and tried to run Halo, Half Life 1 and GTA SA, Halo runs just like before, same for GTA SA, but i got half life 1 running under Opengl a bit slowly because my card is not good enought under opengl, but when i tried run half life 1 under directx... i got same error like in halo, my screen went crazy, weird colors and then a error and then it closed itself.

I ran those commands that you gave me:

rafa@rafa-s-PC:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

rafa@rafa-s-PC:~$ sudo lshw -C display
[sudo] password for rafa: 
  *-display               
       description: VGA compatible controller
       product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:16 memory:f0000000-f7ffffff(prefetchable) ioport:9000(size=256) memory:e8100000-e810ffff memory:e8120000-e813ffff(prefetchable)

I think there's a error, my card's clock speed is about 400mhz (that's what i saw in Windows)

So, i got a new theory, my card/driver or whatever is complaining with Directx, or maybe i installed Directx badly or configured it bad.

---

### Post by bprins on 2010-08-09
Get better hardware then :P

But seriously, dunno if there much you can do about the 66 vs. 400mhz problem. If lshw states that it is 66 mhz.. Hmm, you would say that you werent the only 1 with that problem. Google should at least have more threads on that problem.

On wine over directX, I tried it, and never gone back ever since. I rely more on opengl (and I can play wow via wine using opengl, and it runs steady). 

Bump the thread now and then, maybe somebody has better knowledge that actually helps you further.

---

### Post by RafaMaster on 2010-08-10
Thank you for your support, it seems that were the ONLY one person in this comunity that could have helped me what a great support awesome ... I blow up ubuntu from system, and returned back to windows... Ubuntu is a great os but not useful for me sorry no offense . Well thats all THANK YOU :)

---

### Post by Blackcamaro8 on 2010-08-17
Guys, I'm having the same problem here. I'm never going to say I'm an expert, but I'm far from an Ubuntu newbie. I know a good bit about it, using it on two computers on my desk and on my laptop. Using Windows on this laptop when I first got it, Halo ran like a dream, almost as well as my primary desktop (nVIDIA GeForce 6200 A-LE, 1GB DDR, 3.0GHz Dual-core P4) or my secondary (nVIDIA GeForce 5200 FX, 1.5GB DDR, 2.8Ghz dual-core Intel Celeron) do on WINE, both using Ubuntu 10.04 LTS. 

However, I installed Ubuntu, and the first thing I installed was the PPA for WINE, the second thing is always my customizations, etc. I install Halo after using Winetricks to install d3dx9 and d3dx8. I also installed the mcXXX.dll(I don't remember the numbers.), and all I get when I start Halo is the splash screen where it's running the metadata checks on the map files, and then the creator videos show, and I get a black screen. I've tried the -novideo option, and still a black screen, although it had a grid of nine white spots to the top left. 

This laptop has:
1GB of RAM, Intel Pentium M 1.6Ghz processor, ATI Radeon 9000 using 64MB on the AGP aperture. 

Can anyone help? I also get the error about WINE reporting the wrong video card. It's saying it's an nVIDIA GeForce3.

---

