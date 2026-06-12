---
title: "Keyboard, touchpad don't work on windows/ubuntu dual boot."
date: 2008-11-07
forum: Hardware
---

### Post by Silverspell on 2008-11-07
Ok i have the weirdest issue i have ever encountered, and unfortunately i don't know where else to ask about it. This might not be the best place but i hope i can get some advice from you guys.

My laptop is an
Acer Aspire 5672 AWLMi
2GB DDR2 RAM
Dual boot: Windows XP SP3 - Ubuntu 8.10

I am a new linux user. Recently upgraded from Ubuntu 8.04 to 8.10. My system is a dual-boot system with Windows XP SP3 and Ubuntu 8.10. Yesterday after messing a lot with the **linux** installation i decided to reinstall ubuntu completely. Everything goes well, and i am happy. I decide to log to my Windows to talk with Skype with cam (haven't managed to fix the cam drivers on my linux yet). Here is where things start getting crazy.. My windows installation which was working quite fine, now took 15minutes to boot. Got stuck on the loading after the welcoming screen, showing only desktop and no bars/icons. After it eventually loaded, my keyboard and touchpad didnt respond at all (although they do respond in BIOS). My USB connected mouse worked. I decide to do a couple of restarts to see if the problem persists. Yes same issue. I log back into linux. Touchpad, keyboard works like a charm. No problem there.

I decide to do a clean installation of my Windows partition. My laptop has a hidden partition for system recovery. I start it up, and make a factory installation of windows (which thank god didn't erase my GRUB). After it transfered all the files, it reboots and takes me to the usual first screen of a fresh windows installation where you set up your username, time, and network name... and to my surprise, even though, in the recovery menu everything worked great, here again...**Keyboard and touchpad don't work!?**. I start going a bit crazy, and reboot the whole thingy, going back to linux.

Where i am now...

So...any ideas, suggestions of what the heck is going on, or possible solutions? It will be greatly appreciated.

---

### Post by tau88 on 2008-11-07
I'm having kind of the same situation here. last night I upgraded form 7.10 to 8.10 on my desktop PC, everything worked pretty well, but i decided to reinstall, this time formatting my /home partition too. When i finished installing, i rebooted and the screen went blank before the login screen, rebooted again and this time i get to the login screen but **mouse and keyboard don't work at all**

Then I decide something must have wrong with the reinstall, so I check the integrity of my CD and it says there's no problem with it. So I** reinstall for the second time, but get the same issue**. 

This is very frustrating, I already tried booting into recovery mode and repairing xorg, to no avail.

Any suggestions?

---

### Post by Silverspell on 2008-11-07
The situation is getting stranger and stranger as it goes (and forgive me for this tau88) but i am happy to see i am not the first one to encounter a problem of such a nature. So here is what's been happening:

After all that i said, i decided to use another windows XP cd i had instead of the recovery, so that it would load the drivers from there. Same all, same all, the system refuses to recognize keyboard/touchpad at the same time point. I am starting to get crazy so i make a GParted boot disk, i boot from there and delete all of my partitions and reformat them to fat32. Try again the recovery from the "hidden" partition....SAME.

Next attempt, i delete also the hidden partition and reformat everything to fat 32. Run from my backup win XP cd...SAME

I rewrite the MBR from windows XP boot disc. No luck also.

I load Windows Vista installation (they are using different drivers than XP right ? -or so i thought), from my CD. Blah, blah, blah, installation moves on quite good...everything seems to be working ok. We are back to were you set your username and password. SAME PROBLEM. We are now talking about a hard drive that has been swept clean..

I put Ubuntu 8.04 cd. Install it. Things are finally working. 

But this does not mean that it is fixed since i need my windows installation for specific programs i use for my work. So anyone has ANY idea, clue, something, anything, about what exactly is going on, and where exactly is this problem hidden and only surfaces when i load windows now? I have to remind you here, this whole thing started after reinstalling Ubuntu 8.10...which ofcourse can be a coincidence, and there could have been a virus or something on my windows partition (which i keep quite clean with a firewall-antivirus combo). And even if it was...where it is hidden now after all these?

I mean, i am at a huge loss here, and i genuinely need some expert opinion.

Thanks for reading this anyway.

---

