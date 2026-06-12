---
title: "Please tell me what's wrong with my computer...Current hypothesis: graphics card died"
date: 2015-12-13
forum: Hardware
---

### Post by roy27 on 2015-12-13
This problem was born yesterday. I was playing in game while booted up in Windows, and then bam, the screen turned completely pink, and after a few seconds my computer shut itself down. 

When I boot up my computer, I enter the pass, then I go into grub selection screen to select which O.S. to run, if I choose Windows then the Windows loading screen shows up (nothing what-so-ever is wrong with it) then when it gets to the login screen, the screen it either black or (just now [after doing Windows repair]) it shows up but it looks weird: there are purple lines everywhere... It even let me login once, after I logged in the screen was completely blue.  

When I boot to Ubuntu same thing happens, except I don't get a loading screen, it goes to either the black screen or sometimes to the login screen (which again, looks weird; weird lines everywhere). It let me enter my pass, but I accidently pressed the screen and it all turned one color and then that was the end of it (I think it actually shut itself down). 

In both cases the computer often turns itself off. My hypothesis is that this is caused by overloading. I don't know if this completely true but I may have felt hot air coming out of either my GPU or CPU fans (which shouldn't happen, since when the computer boots up, it's not really doing any hard work). 

The video card I have is 7870 Radeon, for gaming...I spent around $300 for it, I've had it for many years and I was planning on keeping it for many more years...is it really dead? I looked up videos of this on YouTube and many people were having similar issues, so they would put GPU circuitboard into an oven for 15 minutes, and that fixed it, lol! I don't have a lot of money so hopefully there is a better way to fix it. This also might be a virus, like a boot sector virus...you tell me. By the way, if tried Windows repair, I've tried Ubuntu's package repair, I've tried running FailSafeX mode...none of them worked. I used to have a problem with running my video card on my Ubuntu machine, some years ago, but then I installed the proper driver and it was fine ever since; but this is clearly not just an Ubuntu problem (since my Windows OS doesn't work either). 

The pictures below should really clear things up. They show how the loading screens look completely normal, how the login screens look completely messed up (when they're not just black screens; which is rare), shows me trying to recover stuff, and shows me doing a memory test on my machine, as well as some other information about my machine.

---

### Post by roy27 on 2015-12-13
[ATTACH=CONFIG]266128[/ATTACH][ATTACH=CONFIG]266124[/ATTACH][ATTACH=CONFIG]266125[/ATTACH][ATTACH=CONFIG]266126[/ATTACH][ATTACH=CONFIG]266127[/ATTACH]

More images

---

### Post by QIII on 2015-12-13
Is the cooling fan working on the card?

Yes, the GPU will get pretty hot very quickly initially.  That isn't unexpected.  It will still be hot after an immediate reboot if it hasn't had time to cool.

Check the fan operation first.  If you've had it a while, there may be some mature dust bunnies in the heatsink keeping the air from flowing.  A quick shot of compressed air might help in that case.

If the heat sink has been blocked long enough and the GPU stressed to overheating for long enough, well, damage is surely going to occur.

My bet is that you'll need to replace it.

---

### Post by roy27 on 2015-12-13
I will try to clean the fan tomorrow, although I don't really have any special tools. I don't really know how to check if the fan is working properly without actually using software on the computer. The fan for the video card is indeed built into the video card, if you google "HD7870" most of the pictures that will show up will be the pictures of the video card that I have, it's a giant red card.

Edit: I'd think that non-GUI Ubuntu interface would still work, even if the video card is malfunctioning...but it doesn't, (ctrl+alt+f1 doesn't work either, normally, it would). Although I can do some interactions with machine@root when I enter Ubuntu's recovery mode and then select the option to work in the shell.

Edit2: So you've concluded that the problem is with the video card? Nothing else? I need to know for sure, before I lay out the money to replace it.

---

### Post by Yellow Pasque on 2015-12-13
> Edit2: So you've concluded that the problem is with the video card? Nothing else? I need to know for sure, before I lay out the money to replace it. 
Sorry, but we really can't confirm that. The video card overheating and failing is the most likely suspect based on your description, but hardware problems can be tricky when you don't have spare components to methodically troubleshoot the problem.

>  I don't really know how to check if the fan is working properly without actually using software on the computer
Look at it while the computer is on.

> which shouldn't happen, since when the computer boots up, it's not really doing any hard work).
Even if it's not doing "hard work" at boot, the components are still at load voltage because the OS handles a lot of the power management duties.

---

### Post by tokyobadger on 2015-12-13
> **roy27 said:**
> I will try to clean the fan tomorrow, although I don't really have any special tools. I don't really know how to check if the fan is working properly without actually using software on the computer. The fan for the video card is indeed built into the video card, if you google "HD7870" most of the pictures that will show up will be the pictures of the video card that I have, it's a giant red card.

Edit: I'd think that non-GUI Ubuntu interface would still work, even if the video card is malfunctioning...but it doesn't, (ctrl+alt+f1 doesn't work either, normally, it would). Although I can do some interactions with machine@root when I enter Ubuntu's recovery mode and then select the option to work in the shell.

Edit2: So you've concluded that the problem is with the video card? Nothing else? I need to know for sure, before I lay out the money to replace it.
1. Special tools: you shouldn't need much more than a can of compressed air and the tools you used to assemble the PC

2. non-GUI: no it won't work unless your CPU has GPU functionality and you've enabled it in BIOS/(U)EFI; even without a WM/DE you need something to display the CLI

3. Your graphics card is partially functional. Is it the root cause? Hard to say. I'd do as others have suggested. Pull out the card, pull out the RAM, clean the slots, clean the fans, check connections (all of them); if it's still not improved I'd try another PCIe slot (after cleaning). Next would be trying a different PSU (borrow one from a friend if you can and the spec is adequate).

4. BTW: what version of Ubuntu are you running?

---

### Post by roy27 on 2015-12-13
Unfortunately, I currently don't have access the tools you mentioned either...But I'll try to figure something out. \n   I am running Kubuntu 14.04   You think the PSU isn't providing enough power to the video card? It has worked for many years...  \n  Maybe something is shortcircuiting? But then I'd think the computer would start up, or at least it would look (after boot) more broken that it does.  \n  The weird thing to me, is that a lot of the things are showing up perfectly. I'd think with a broken GPU the screen wouldn't show the image at all, or at least show everything in a wrong way; however, it's only at the login screen where the effect starts taking place... seems very odd to me.

---

### Post by tokyobadger on 2015-12-13
1. $300 for the GPU vs $3 for the can of compressed air (max)

2. You purchased the card so that means you installed it or is this PC built by someone else?

3. If you want further meaningful help you'll need to share in full the hardware specs

4. Forget the PSU topic (for now); exhaust all other suggestions in the responses above

5. Thank you for clarifying the (x)Ubuntu release

---

### Post by QIII on 2015-12-13
> **roy27 said:**
> 
Edit2: So you've concluded that the problem is with the video card? Nothing else? I need to know for sure, before I lay out the money to replace it.

No, I haven't concluded anything.  I said it was my bet. That's based on nearly 40 years of fiddling with these infernal machines.  But it's not a slam dunk.  I suggested a couple of things to look at, and the list has been lengthened by other respondents.

---

### Post by roy27 on 2015-12-13
> **tokyobadger said:**
> 1. $300 for the GPU vs $3 for the can of compressed air (max)

2. You purchased the card so that means you installed it or is this PC built by someone else?

3. If you want further meaningful help you'll need to share in full the hardware specs

4. Forget the PSU topic (for now); exhaust all other suggestions in the responses above

5. Thank you for clarifying the (x)Ubuntu release

I built the computer, unfortunately. I say unfortunately because my water cooler was not made for my motherboard, so I had to 'improvise,' but hey, the problem seems to be with the video card and not the CPU. :)

The specs can be seen in the picture with the memory test...10 GB 1666Ghz Ram, 6-core CPU 3.5Ghz, 650 Watt Power Supply,  Water cooler on CPU, Radeon 7870 Ghz edition (2 GB Vram), Lots of fans.

I will not be able to properly clean my computer until I come home; end of next week.. So I'll get back to you after I get home and do it.

---

